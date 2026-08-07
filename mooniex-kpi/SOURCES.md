# SOURCES — mooniex-kpi

Provenance, licensing, and attribution for `mooniex-kpi`, destined for the
PUBLIC repo `PASAKON/mooniex-claude-skills`.

Inclusion rule applied: ship only **permissive-licensed (MIT/Apache/BSD)** or
**MoonieX-owned** content. This skill has exactly two origins — one MIT upstream
and one MoonieX codebase survey — so there are no licensing grey areas.

This skill is the org's **deep measurement** layer and the codebase-grounded
companion to `mooniex-growth` §10 (Growth Analytics & Measurement). It does
not duplicate or contradict growth §10; it extends it with the real MoonieX
tracking architecture, attribution math, event catalog, and measurement backlog.

---

## 1. Per-feature attribution table

| Merged section / feature | Source | Origin | License | Taken / Dropped + why |
|---|---|---|---|---|
| Operating principles (track-for-decisions, start-from-the-question, action-oriented reporting, respond-in-user-language) | `analytics-attribution` | AgentKits Marketing by AityTech | **MIT** | **Taken (best-of: analytics-attribution)** — generic measurement discipline, MIT-clean |
| Sec 1 North-Star & KPI — AARRR/pirate-funnel mapping, leading vs lagging, KPI-by-funnel-stage framing | `analytics-attribution` (Marketing KPIs by funnel stage) + MoonieX | MIT upstream framing, MoonieX-specific north-star table | MIT + MoonieX-owned | **Taken** — upstream gives the funnel-stage KPI skeleton; the MoonieX north-star/guardrail table is original |
| Sec 2 Attribution & ROI — attribution models table, attribution windows, CAC/LTV/ROAS/payback, blended vs channel, anti-patterns | `analytics-attribution` (Attribution Models, Best Practices, Anti-Patterns) | AityTech | **MIT** | **Taken (best-of: analytics-attribution)** — the strongest part of the source; MoonieX rebate/window specifics added on top |
| Sec 3 MoonieX Tracking Architecture (System A `webapp_user_events`, System B `webapp_user_activity_log`, the write-to-which-system decision rule, third-party scripts, claudeflow LuNar) | **MoonieX codebase survey** | `mooniex-webapp` + `mooniex-claudeflow` @ 2026-06-15 | MoonieX-owned | **Taken** — original, derived from reading the live code (file/function/interval/table names cited) |
| Sec 4 Event Catalog & Naming — closed enum, `<area>_<verb>` convention, full System A enum, System B dotted names, PII rules | **MoonieX codebase survey** | `src/lib/analytics/events.ts`, `src/lib/activity/track.ts` | MoonieX-owned | **Taken** — transcribed from the actual enums |
| Sec 5 Known Measurement Gaps (G1 broker events unfired, G2 feature_clicked vs outbound_click, G3 Exness sub-id, G4 no pixel/CAPI) | **MoonieX codebase survey** | verified across webapp components/actions/data | MoonieX-owned | **Taken** — original audit findings with file:line evidence |
| Sec 6 Dashboards & Reporting Cadence — per-dashboard contents, existing admin surfaces table, weekly funnel ritual | **MoonieX codebase survey** + `analytics-attribution` (report cadence concept) | `src/app/admin/*`, `metrics.ts` + MIT cadence framing | MoonieX-owned + MIT | **Taken** — admin-surface inventory is original; weekly-report cadence concept is generic/MIT |

---

## 2. Credited sources

| Source | Author / Owner | Origin URL | License | Status in merge |
|---|---|---|---|---|
| analytics-attribution | AgentKits Team (AityTech) | https://github.com/aitytech/agentkits-marketing | MIT | **Included** (operating principles, §1 framing, §2) — attribution required & given (`NOTICE.md`) |
| MoonieX codebase survey 2026-06-15 | MoonieX | internal — `mooniex-webapp`, `mooniex-claudeflow` | MoonieX-owned | **Included** (§3-6) |

> The `analytics-attribution` source is the same upstream repo
> (agentkits-marketing) that `mooniex-growth` Section 4 (paid-advertising)
> draws from, pinned at the same commit. Its `analytics-attribution/SKILL.md` is
> a distinct skill file from the `analytics` skill used in growth §10 (that one
> is Corey Haines' `marketingskills`). This KPI skill deliberately leans on the
> deeper **attribution** source and on first-hand codebase truth, rather than
> re-deriving growth §10.

---

## 3. Pinned versions

| Item | Pin (commit SHA / path) | Date observed |
|---|---|---|
| agentkits-marketing repo (analytics-attribution source) | `8dcf8bf64a683db7e6763e99076b3f62252c2bce` (origin/main, "bump-version-1.7.2") | 2026-06-15 |
| agentkits-marketing LICENSE | MIT, `/Users/gob/Projects/external/agentkits-marketing/LICENSE` | 2026-06-15 |
| analytics-attribution SKILL.md | `/Users/gob/Projects/external/agentkits-marketing/skills/analytics-attribution/SKILL.md` | 2026-06-15 |
| MoonieX codebase survey — webapp analytics | path-pinned: `mooniex-webapp/src/lib/analytics/{events,client,server,funnels,metrics}.ts`, `src/lib/activity/{track,track-client}.ts`, `src/components/analytics/AutoTracker.tsx`, `src/components/tools/useToolTracking.ts`, `src/app/api/cron/activity-rollup/route.ts`, `src/app/admin/**` | 2026-06-15 |
| MoonieX codebase survey — gap evidence | `mooniex-webapp/src/components/dashboard/ConnectBrokerForm.tsx`, `src/lib/webapp/broker-actions.ts`, `src/components/brokers/BrokerGuide.tsx`, `src/data/brokers.ts` | 2026-06-15 |
| MoonieX codebase survey — claudeflow LuNar | `mooniex-claudeflow/scripts/lunar-conversion-report.js`, `src/webhook/contactTracker.js` (mx_events removed v0.10.7) | 2026-06-15 |

---

## License Concerns (summary)

**INCLUDED with required attribution — 1 MIT source:** `analytics-attribution`
(MIT, AgentKits/AityTech). MIT requires retaining the copyright + permission
notice — see `NOTICE.md`.

**INCLUDED as MoonieX-owned — codebase survey:** §3-6 are original MoonieX
content derived from reading MoonieX's own private repositories. No third-party
copyrighted prose is reproduced; the cited file/function/table/line names are
factual references to MoonieX-owned code, not copied source. No copyleft (GPL)
or proprietary third-party content is present in the merged output.

**No EXCLUSIONS** — unlike `mooniex-growth`, this skill draws on no
non-permissive third-party skills (no Brian Wagner / unknown-license material).
