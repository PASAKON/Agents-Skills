---
name: mooniex-kpi-skill
owner: CGO
origin: mooniex-curated
scope: >-
  Measurement only — metric choice, attribution modelling, and the org's REAL
  tracking architecture (System A webapp_user_events, System B
  webapp_user_activity_log) plus the known G1-G4 measurement gaps. Documents what
  is actually instrumented, not what should be. Does not run campaigns.
description: The org's measurement authority — KPI choice, north-star, attribution, CAC/LTV/ROAS, funnel and cohort metrics, event tracking, and the real System A/B tracking tables. Trigger on /mooniex-kpi-skill and on "north star", "attribution", "CAC", "LTV", "ROAS", "tracking plan", "funnel metrics", "cohort". Use instead of the generic analytics skill.
---

# MoonieX KPI & Measurement Skill

You are the MoonieX measurement and analytics authority. This skill is the deep
measurement layer for the org: how to choose the right metric, how to attribute
revenue honestly, and — most importantly — the **real** MoonieX tracking
architecture, so every agent measures the same way against the same tables
instead of inventing parallel definitions.

This is the codebase-grounded companion to `mooniex-growth-skill` §10 (Growth
Analytics & Measurement). Growth §10 is the quick "instrument before you spend"
reference that feeds the acquisition/CRO/launch sections; **this** skill is where
you come for the precise data model, attribution math, the event catalog, and
the measurement backlog. The two do not contradict — when growth §10 says "name
things consistently before implementing," sections 3-5 here are the canonical
naming and the canonical tables.

## Operating Principles (apply to every section)

1. **Track for decisions, not vanity.** Every metric and every event must change
   a decision. If no action follows from a number, do not put it on a dashboard.
   Start from the question ("what will we do differently?") and work back to the
   metric. (best-of: analytics-attribution)
2. **One north-star + a small set of guardrails per goal.** A single rallying
   metric, fenced by 2-4 guardrails that catch the ways you could "win" the
   north-star while hurting the business.
3. **Pre-register success metrics and sample size.** Before a test or a campaign,
   write the primary metric, the minimum effect worth detecting, and how long /
   how much traffic it needs. Decide the decision rule up front (cross-link
   mooniex-growth-skill §7 for the sample-size formula and table).
4. **Respect attribution windows.** Match the window to the real decision lag.
   MoonieX has a long, off-platform conversion lag (click rebate link → open a
   broker account → fund → trade enough lots to rebate), so short last-click
   windows systematically under-credit awareness and content.
5. **Instrument before you spend.** No paid push, no new funnel stage, and no
   "let's see if it works" launch without the events firing first — an
   un-instrumented step is an invisible step (see §5, the measurement backlog,
   for what this rule has already cost us).
6. **Respond in the user's language.** If the request is in Thai, answer in Thai;
   sacrifice grammar for concision and list open questions at the end.
   (best-of: analytics-attribution)

---

## 1. North-Star & KPI Framework

A KPI framework picks the *one* number a goal is steering by, then fences it.

### Choosing a north-star
A good north-star is (a) a leading indicator of sustainable revenue, (b) a
measure of **delivered customer value**, and (c) movable by the team. For
MoonieX the business is broker-affiliate rebate revenue, so the honest
north-star is a **funded, trading referred account** — not signups, not traffic.
Everything upstream (signup, broker-connect) is a leading proxy for it.

| MoonieX goal | Candidate north-star | Why | Guardrails |
|---|---|---|---|
| Acquisition | New verified broker accounts / week | Closest leading proxy to rebate revenue | CAC, signup→verify rate, lead quality (junk signups) |
| Activation | % of signups who connect a broker within 7d | First real value moment | time-to-connect, support tickets |
| Engagement (tools) | Weekly active tool-users (distinct) | Tool factory = the acquisition engine | tool_result/tool_submit ratio (error rate), bounce |
| Retention | Week-4 cohort return rate | Durable usage = durable rebates | churn, LINE opt-out rate |
| Revenue | Net rebate revenue / month | The actual P&L line | refund/clawback rate, % from a single broker (concentration) |
| Referral | Referred signups per active user | Compounding loop | invite→signup rate, fraud |

> Pick **one** per active goal this quarter. Multiple north-stars = no north-star.

### AARRR (pirate funnel) mapped to MoonieX
| Stage | MoonieX meaning | Primary event(s) — System A | Key metric |
|---|---|---|---|
| **Acquisition** | Land on site from SEO / social / LINE / ads | `page_view` (+ `utm_*`) | sessions, source mix |
| **Activation** | First real value: signup, run a tool, connect a broker | `auth_signup`, `tool_used`, `broker_connect_started` | activation rate, time-to-value |
| **Retention** | Comes back and keeps using tools / LuNar | repeat events per user (cohort grid) | W1/W4 return rate |
| **Revenue** | Funds + trades a referred account; rebates accrue | `broker_verified` (proxy) + broker API truth | verified accounts, net rebate |
| **Referral** | Shares a tool / rebate poster / ref link | `ref_link_copied`, `ref_shared`, `link_in_bio_clicked` | invites, K-factor |

### Leading vs lagging
- **Lagging** (the result): net rebate revenue, verified accounts, churn. True,
  but slow — they tell you what already happened.
- **Leading** (the steering wheel): tool usage, signups, broker-connect starts,
  content reads. Move these this week to move the lagging metric next month.
- Rule: **steer on leading, report on lagging.** A dashboard with only lagging
  metrics is a rear-view mirror.

---

## 2. Attribution & Marketing ROI
*(best-of: analytics-attribution)*

### Attribution models
Attribution decides which touchpoint gets credit for a conversion. There is no
"correct" model — only one that fits your sales-cycle length and maturity.

| Model | Credit rule | Best for | MoonieX fit |
|---|---|---|---|
| **Last-touch (last-click)** | 100% to final touchpoint | Short cycles, direct response | Default in most tools; **under-credits** MoonieX content/SEO |
| **First-touch** | 100% to first touchpoint | Brand / TOFU discovery value | Good for "what found us" (often SEO/TikTok) |
| **Linear** | Equal across all touches | Understanding the whole journey | Honest baseline when volume is low |
| **Time-decay** | More to recent touches | Long sales cycles | Fits the broker-funding lag well |
| **Position-based (U)** | 40 / 20 / 40 first–mid–last | Balanced first+last view | Good compromise once multi-touch exists |
| **Data-driven** | ML-distributed credit | High volume, mature | **Not yet** — needs volume MoonieX doesn't have |

Default stance for MoonieX today: **report last-touch AND first-touch side by
side** (the gap between them is the "awareness debt" last-click hides), and graduate
to position-based once multi-touch capture exists. The `utm_*` columns on
`webapp_user_events` are first-touch-capable per session; full multi-touch needs
journey stitching across sessions (not built — see §5).

### Attribution windows
The window = how long after a touch a conversion still counts. Match it to the
real lag.
- Set the window ≥ the time from first touch to the money event.
- MoonieX conversion is **off-platform and slow**: site → broker signup link →
  account open → KYC → fund → trade lots → rebate. That can be days to weeks, so
  a 1-day/7-day click window badly undercounts. Prefer a **28-day** (or longer)
  view for broker conversions; treat sub-7-day numbers as "fast movers only."
- State the window on every ROI number. "ROAS 3:1" is meaningless without it.

### CAC / LTV / ROAS / payback — formulas
```
CAC            = total acquisition spend / new customers acquired   (same period, same channel)
LTV            = ARPU × gross margin % × average customer lifetime (months)
                 (or, contribution-based: avg monthly contribution × lifetime)
LTV:CAC        = LTV / CAC          target ≥ 3:1   (< 1:1 = losing money per customer)
ROAS           = revenue attributed / ad spend     target ≥ 3:1 (channel-dependent)
Payback period = CAC / (monthly contribution per customer)   target ≤ 12 months (shorter for thin cash)
```
MoonieX specifics:
- "Revenue" for a referred trader is **rebate revenue**, which is recurring and
  trading-volume-dependent — so LTV must use *contribution over lifetime*, not a
  one-off order value. A single high-volume trader can dwarf dozens of dormant
  signups; never average naively.
- The org's rebate claim numbers (XM $15/lot, Exness $8/lot, gold-based, 80% IB
  share) are **locked** — do not recompute headline rebate from a DB max (BTC
  inflates it). Use the locked figures for LTV modeling.

### Blended vs channel ROAS
- **Blended ROAS** = total revenue / total marketing spend. Honest top-line, but
  hides which channel works.
- **Channel ROAS** = per-channel attributed revenue / that channel's spend. Needed
  to allocate budget — but only as trustworthy as the attribution + windows above.
- Watch the **last-click trap**: branded search / direct often "win" channel
  ROAS because they sit at the end of journeys that SEO or TikTok started. Cross-
  check channel ROAS against first-touch and against a holdout/geo test before
  cutting a top-of-funnel channel.

### Anti-patterns (attribution)
Vanity-only reporting (impressions ≠ rebates) · last-click bias as the *only*
lens · ROAS with no stated window · ignoring the off-platform broker lag ·
recomputing rebate rates from raw DB instead of the locked figures.

---

## 3. MoonieX Tracking Architecture (codebase truth)

MoonieX runs **two distinct first-party tracking systems** plus a small set of
third-party scripts. They are not interchangeable. Write to the right one.

> Survey basis: `mooniex-webapp` @ 2026-06-15. Re-verify when analytics code
> changes — this section is only as current as the files it cites.

### System A — `webapp_user_events` (primary analytics: funnel · cohort · attribution)
The site-wide behavioral log. 365-day retention. This is the system for
**conversion, funnel, cohort, and attribution** questions.

- **Client queue:** `src/lib/analytics/client.ts`
  - `trackClient(event, props)` enriches each event with `page_path`,
    `referrer`, `device_type`, `ts`, and UTM via `readUtmFromUrl()`, pushes to a
    `sessionStorage` queue (max 50), and flushes to `POST /api/track` every
    **5s** (`FLUSH_INTERVAL_MS`). `flushSoon()` force-flushes on tab hide.
  - `getSessionId()` = stable per-browser UUID in `localStorage` (`mnx_session_id`).
  - Consent: `hasConsent()/setConsent()` gate the **third-party** Clarity tracker
    only; first-party events still queue (anon events carry `session_id` only).
- **Auto-capture:** `src/components/analytics/AutoTracker.tsx` (mounted in root
  layout) emits without manual wiring:
  - `page_view` on every route change
  - clicks on any element carrying a `data-track="<event>"` attribute (walks up
    to 4 ancestors; `data-track-prop-*` become props)
  - `scroll_depth` at 25/50/75/100%
  - `time_on_page` (visible-time accumulator) on visibility change
  - a **60s presence heartbeat** to `POST /api/presence` (feeds "online now")
- **Server insert:** `src/lib/analytics/server.ts`
  - `trackEvent(args)` — single insert from a server milestone (signup, payment).
    Validates against the closed enum, drops PII keys, fire-and-forget.
  - `ingestEvents(args)` — batch insert from `/api/track`; drops + logs
    unregistered event names and PII-bearing rows.
  - IP is hashed with a **daily salt** (`hashIp`) — per-day uniqueness, never a
    stable fingerprint. `presenceUpsert()` maintains `webapp_user_presence`.
- **Funnels / cohorts:** `src/lib/analytics/funnels.ts`
  - `computeFunnel(def)` — ordered event sequence; counts distinct users (or
    `anon:<session_id>`) who fired each stage **after** the previous one;
    50k-row in-memory pivot cap.
  - `computeCohortRetention(weeksBack=12)` — weekly signup buckets × week-N
    return grid, rooted on `auth_signup`.
  - `PRESET_FUNNELS`: `signup-to-first-action`, `discovery-to-pricing`,
    `broker-onboarding`.
- **Admin read aggregates:** `src/lib/analytics/metrics.ts` (`getMetricsSnapshot`)
  — online-now, 7d/30d views+sessions, per-tool viewed/used, a
  page_view→tool_used→signup→order funnel, top UTM sources. Read-only; falls back
  to zeroed shapes on error (honest empty state in week 1). Note its funnel
  crosses a **session→user** unit boundary (stages 1-2 sessions, 3-4 users) — a
  directional read, surfaced with a unit label.

### System B — `webapp_user_activity_log` (tool-usage / interaction depth)
The fine-grained product-interaction log. **This is for engagement depth**, not
top-of-funnel conversion.

- **Client batch:** `src/lib/activity/track-client.ts`
  - `trackActivityClient(args)` buffers and POSTs to `POST /api/activity/track`
    every **2s** or at 20 events (`BATCH_INTERVAL_MS` / `BATCH_LIMIT`), flushes
    on `pagehide`/`beforeunload`. Session id in `sessionStorage` (rotates per tab).
- **Server insert:** `src/lib/activity/track.ts`
  - `trackActivity(args)` — fire-and-forget insert into
    `webapp_user_activity_log`. Category enum: `page_view | interaction |
    conversion | error | discovery`. Event names are dotted
    `<area>.<feature>.<action>` (e.g. `image_studio.gen.complete`); canonical
    names live in the exported `EVENTS` map.
  - Privacy: regex-redacts sensitive keys; **honors `webapp_profiles.activity_paused`
    (PDPA opt-out)** — skips the insert entirely for opted-out users.
- **Tool hook:** `src/components/tools/useToolTracking.ts` → emits
  `tool_submit` and `tool_result` (category `interaction`, `tags.tool=<slug>`),
  settled ~800ms.
- **Daily rollup:** cron `src/app/api/cron/activity-rollup/route.ts` (Vercel
  cron, ~00:30 UTC) aggregates yesterday's raw rows into
  **`webapp_user_activity_daily`** keyed `(day, event_name, category)` for fast
  dashboard reads, and enforces **90-day retention** on the raw log.

### Decision rule — which system do I write to?
| You want to measure… | Write/read | System | Why |
|---|---|---|---|
| A funnel / conversion step | `trackClient` or server `trackEvent` (enum event) | **A** `webapp_user_events` | Funnel + cohort engines read this table |
| Attribution / UTM source of a conversion | event with `utm_*` (auto-captured) | **A** | UTM columns live here |
| Cohort retention | rely on `auth_signup` + any events | **A** | `computeCohortRetention` roots on it |
| Whether a tool is actually *used well* (submit→result, errors, latency) | `trackActivityClient` / `trackActivity` | **B** `webapp_user_activity_log` | Interaction-depth + daily rollup |
| Image-studio / academy / credits interaction depth | `EVENTS.*` dotted names | **B** | That's what `EVENTS` enumerates |
| "Online now" / live presence | presence heartbeat | **A** (presence table) | `countOnline()` |
| A headline number on an exec dashboard | read `metrics.ts` / rollup tables | A + B | Pre-aggregated, fast, honest empty state |

Rule of thumb: **funnel / conversion / cohort / attribution → System A.
Tool-engagement depth → System B.** A conversion that matters for the funnel
(signup, broker-verify, payment) belongs in A *even if* you also log interaction
detail in B.

### Third-party / pixels (deliberately minimal)
- **Microsoft Clarity** — heatmaps/session replay, loaded **only after cookie
  consent** (`src/components/analytics/ClarityLoader.tsx`, gated on
  `getConsent()==="accepted"`, env `NEXT_PUBLIC_CLARITY_PROJECT_ID`).
- **Vercel Analytics + Speed Insights** — first-party / cookieless, always on
  (`<Analytics/>` + `<SpeedInsights/>` in `src/app/layout.tsx`).
- **Explicitly NOT present:** no **Meta Pixel** (`fbq`), no **GA4 / gtag**, no
  **Google Tag Manager**, no **server-side Meta CAPI**. (Verified absent
  2026-06-15.) Paid social therefore has **zero conversion signal** today — see
  §5 G4.

### claudeflow side — LuNar is measured separately
The LINE bot LuNar lives in `mooniex-claudeflow`, not the webapp, and is measured
on its own:
- `scripts/lunar-conversion-report.js` joins `claudeflow_lunar_turns` (chat
  turns) with `claudeflow_verify_tickets` (broker-verify attempts) to compute
  `started_rate` (verify_started / conversations) and `success_rate`
  (verify_success / conversations; success = ticket `status === 'verified'`).
- **claudeflow does NOT write `webapp_user_events`.** That instrumentation
  (`mx_events`) was **removed in v0.10.7** (see comment in
  `src/webhook/contactTracker.js`). Do not assume LINE activity shows up in
  System A — join LuNar metrics from the claudeflow tables instead.

---

## 4. Event Catalog & Naming

### Naming convention (System A — `src/lib/analytics/events.ts`)
- Shape: **`<area>_<verb>`**, snake_case, verb in **past tense**
  (`tool_used`, not `use_tool`). Areas: `auth | nav | content | academy |
  trading | broker | studio | partner | pricing | checkout | system`.
- The enum is a **closed allowlist** (`ANALYTICS_EVENTS`). Unregistered names are
  dropped at ingest and logged — adding an event means editing `events.ts` first.
- Context goes in **props**, not the name (the public-tool funnel stays flat:
  one `tool_used` event with a `tool` prop, not one event per tool). Same for
  indicators (`slug` prop), rebate posters (`broker` prop), bio links
  (`profile`/`item_label` props).
- **No PII in props.** `FORBIDDEN_PII_KEYS` (email, phone, full_name, address,
  dob, card*, password, token, ssn, passport, national_id) — server drops the
  whole row + Sentry-warns if any appears.

### The real System A event enum (canonical — keep in sync with `events.ts`)
| Area | Events | Typical fire |
|---|---|---|
| auth | `auth_signup`, `auth_login`, `auth_logout`, `auth_password_reset` | **server** (`trackEvent` on milestone) |
| nav | `page_view`, `outbound_click`, `scroll_depth`, `time_on_page` | **client** (auto via AutoTracker) |
| pricing/checkout | `pricing_viewed`, `plan_compared`, `upgrade_clicked`, `checkout_started`, `payment_succeeded`, `payment_failed` | mixed (view=client, `payment_*`=**server**) |
| tools | `tool_viewed`, `tool_used`, `tool_cta_clicked` | client (`tool` prop = which) |
| indicators | `indicator_viewed`, `indicator_access_clicked` | client (`slug`, `page`, `cta_location` props) |
| landing CTAs | `hero_signup_clicked`, `cta_indicator_clicked` | client (`data-track` on hero buttons) |
| content | `article_viewed`, `guide_viewed`, `news_viewed`, `search_submitted`, `share_clicked` | client |
| academy | `course_started`, `episode_played`, `episode_completed`, `cert_downloaded` | mixed |
| trading | `backtest_run`, `backtest_saved`, `positions_viewed`, `signal_viewed`, `signal_subscribed`, `journal_created` | mixed |
| broker | `broker_connect_started`, `broker_verified`, `broker_disconnected` | **should be server** — see §5 G1 (currently unfired) |
| landing rebate | `rebate_poster_clicked` | client (`broker` prop = xm\|exness\|qrs\|interstellar) |
| link-in-bio | `link_in_bio_clicked` | client (`profile`, `item_label` props) |
| studio | `image_gen_started`, `image_gen_completed`, `template_applied` | mixed |
| partner/IB | `video_gen_started`, `ref_link_copied`, `ref_shared` | client |
| system | `consent_accepted`, `consent_declined`, `feature_clicked` | client |

Required-ish props on every event: UTM (auto-captured from URL) and the area's
discriminator prop (`tool` / `slug` / `broker` / `profile`). Server-fired
milestones (`auth_signup`, `payment_*`) carry `userId`; client events default to
`session_id`-keyed and attach `userId` once known.

### System B activity names (`src/lib/activity/track.ts` `EVENTS`)
Dotted `<area>.<feature>.<action>` — e.g. `auth.signup.complete`,
`image_studio.gen.complete`, `connections.platform.connected`,
`credits.purchase.complete`, `academy.episode.complete`, plus the tool hook's
`tool_submit` / `tool_result`. Category is one of `page_view | interaction |
conversion | error | discovery`. Keep names in the exported `EVENTS` map so
renames go through TypeScript, not grep.

---

## 5. Known Measurement Gaps & Fixes (the measurement backlog)

These are **real, verified gaps** in the live instrumentation (survey
2026-06-15). They are the highest-leverage measurement work because each one is a
decision the org is currently making blind. Prioritized by impact.

| # | Gap | Impact | Fix | Files |
|---|---|---|---|---|
| **G1** | `broker_connect_started` + `broker_verified` are defined (`events.ts:72-73`) and used in the `broker-onboarding` preset funnel (`funnels.ts:49-55`) but are **never fired anywhere** — the broker connect form and server action emit no events. The broker funnel reads **0 at stages 2-3**. | **Critical** — the single most revenue-relevant funnel is dark | Emit `broker_connect_started` on connect submit and `broker_verified` (server `trackEvent`) on verify success | `src/components/dashboard/ConnectBrokerForm.tsx`, `src/lib/webapp/broker-actions.ts` |
| **G2** | The broker-guide "Open account / เปิดบัญชี" link fires `feature_clicked` (with `feature=broker_signup_click`, `broker`, `channel` props) instead of the canonical `outbound_click`, and there is **no server-side conversion event** — the most valuable click on the site is mis-categorized and has no durable conversion record | **High** — pollutes `feature_clicked`, hides the real outbound-to-broker step | Switch the `data-track` to `outbound_click` (keep the broker/channel props); ideally also log a server conversion event | `src/components/brokers/BrokerGuide.tsx:149-157` |
| **G3** | Exness has **no per-channel TikTok sub-ID** — `brokers.ts` has a `TODO(attribution)` and no `affiliateChannels` entry, so TikTok→Exness signups fall back to the web default link and are mis-attributed (XM and Interstellar both have `affiliateChannels.tiktok`) | **Medium** — TikTok→Exness ROAS is wrong | Add `affiliateChannels.tiktok` to the Exness entry once the partner link supports a sub-id param | `src/data/brokers.ts` (Exness entry, ~`:156-158`) |
| **G4** | **No Meta Pixel / CAPI / GA4** anywhere — paid social and Google get **zero conversion signal**, so their channel ROAS cannot be computed and their algorithms can't optimize | **High** *if/when* paid spend starts (today spend is ~zero, so it's latent) | Add server-side Meta CAPI on `auth_signup` + `broker_verified` (server-side keeps it consent-clean and ad-blocker-proof). **ASK before adding any pixel** — confirm with CEO; respect the deliberate no-3rd-party-pixel stance | new server CAPI util + call sites in auth + broker verify |

Working these in order (G1 → G2 → G4 → G3) takes the broker funnel from "0 at
the bottom" to fully measured, then lights up paid-social signal. G1+G2 are pure
instrumentation (no new vendor, no cost, no consent change) — do them first.

> Process note (why this list exists): MoonieX has already paid for the
> "instrument before you spend" lesson. Never green-light a paid push on a step
> that isn't firing — verify the event in `webapp_user_events` first.

---

## 6. Dashboards & Reporting Cadence

### What goes on each dashboard
- **Acquisition** — sessions by source (`utm_source`/`utm_medium`), new vs
  returning, top landing pages, branded vs non-branded; first-touch source mix.
  (reads System A: `topUtmSources`, `windowStats`)
- **Activation** — signup rate, % connecting a broker within 7d, time-to-value,
  tool_used reach. (System A funnels + per-tool)
- **Retention** — weekly cohort grid (W0-W11 return %), churn, repeat-tool usage.
  (System A `computeCohortRetention`; engagement depth from System B daily rollup)
- **Revenue** — verified accounts (proxy) + broker-API truth, net rebate,
  rebate concentration by broker, LTV:CAC, payback. (broker APIs + locked rebate
  figures — not raw DB max)
- **Engagement quality (tools)** — submit→result ratio, error rate, latency, per-
  tool usage. (System B `webapp_user_activity_daily`)

Every tile follows the operating principles: a number with **context** (vs target
/ vs prior period) and an implied action. Honest empty states over fake zeros in
the sparse early weeks.

### Existing admin surfaces (already built — use these before building new)
| Route | Reads | Shows |
|---|---|---|
| `/admin/activity` | `webapp_user_events` | 24h/7d events, unique users/sessions, top events/pages/UTM |
| `/admin/activity/funnels` | `computeFunnel` (System A) | preset funnel stages + conversion (incl. the dark broker funnel — see G1) |
| `/admin/activity/cohorts` | `computeCohortRetention` | 12-week retention grid |
| `/admin/metrics` | `getMetricsSnapshot` | online-now, 7/30d views+sessions, per-tool, top UTM, page_view→tool→signup→order funnel |
| `/admin/finance` | `getCfoSnapshot` / `webapp_cfo_daily_rollup` | 14-day daily burn + finance detail (`/admin/cfo` permanently redirects here) |

### Weekly funnel review ritual
Once a week (cross-ref mooniex-growth-skill §10 cadence): pull the funnel +
cohort + UTM views, compare to the prior week, find the **single biggest drop-off
or the biggest leading-indicator move**, and assign **one** decision/experiment.
Confirm any side-effect-bearing metric against the source of truth (broker APIs
for revenue, not just events) before acting — verify external state, don't trust
the event count alone for money decisions.

---

## Cross-Section Workflow

A measurement engagement chains the sections:
**§1 pick the north-star + guardrails → §3 confirm the right system/table is
instrumented (and check §5 for gaps in that path) → §4 fire correctly-named
events → §2 attribute and compute CAC/LTV/ROAS with the right window → §6 put it
on the right existing dashboard and run the weekly review.**

You rarely run all six in one pass — match the request:
- "What should our north-star be?" → §1.
- "Why is our broker ROAS / attribution off?" → §2 + §5 (G1-G4).
- "Where do I send this event / which table?" → §3 decision rule + §4.
- "Build/read a dashboard" → §6 (reuse the admin surfaces).

For the broader growth strategy these metrics feed (paid, CRO, launch), hand off
to **mooniex-growth-skill** — this skill stops at "measured correctly," growth §3-9
takes it from there.

---

## Sources & Updates

Merged skill — per-feature attribution + pinned commit in `SOURCES.md`, license
text in `NOTICE.md`. This skill is **codebase-grounded**: §3-6 document the live
`mooniex-webapp` / `mooniex-claudeflow` analytics code as surveyed 2026-06-15.

- **analytics-attribution** — https://github.com/aitytech/agentkits-marketing
  (MIT, © AgentKits / AityTech) — §1 funnel framing, §2 attribution models /
  windows / CAC-LTV-ROAS / anti-patterns, operating principles.
- **MoonieX codebase survey 2026-06-15** (MoonieX-owned) — §3 tracking
  architecture, §4 event catalog, §5 measurement gaps, §6 dashboards.

**Re-verify when analytics code changes.** §3-6 cite exact files, function names,
intervals, table names, and line numbers; treat them as a snapshot. If
`events.ts`, `funnels.ts`, `metrics.ts`, the activity libs, the cron, or the
broker components change, re-run the survey and update the affected rows
(especially the §5 gap table once G1/G2/G3/G4 are fixed). To update the upstream
portion: diff agentkits-marketing vs the pinned commit in `SOURCES.md`, port real
fixes, re-pin (MoonieX wiki `playbooks/skill-maintenance.md`).
