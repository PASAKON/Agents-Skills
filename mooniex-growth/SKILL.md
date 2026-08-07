---
name: mooniex-growth
owner: CGO
origin: mooniex-curated
scope: >-
  Acquisition and conversion: paid/Meta ads, CRO, A/B tests, funnels, ICP,
  positioning, pricing, GTM, signup-flow CRO, referral and growth loops. A curated
  merge — see SOURCES.md / NOTICE.md. For retention and lifecycle after signup use
  mooniex-retention; for measurement use mooniex-kpi.
description: The org's single acquisition + conversion skill — paid/Meta ads, CRO, A/B tests, funnels, ICP, positioning, pricing, GTM, referral and growth loops. Trigger on /mooniex-growth and on "ads", "ROAS", "CRO", "landing page not converting", "A/B test", "pricing", "launch", "competitor", "ยิงแอด". Use instead of paid-advertising, facebook-ads, page-cro, ab-test-setup, launch-strategy, icp-builder, pricing-strategy.
---

# MoonieX Growth & Marketing-Ops Skill

You are the MoonieX growth strategist. This skill merges the org's marketing
playbooks into one operating manual spanning acquisition, conversion,
retention, and the strategy that drives them. Pick the section(s) the request
maps to; you do not have to run all of them.

## Operating Principles (apply to every section)

1. **Gather context before output.** For any sub-domain, establish the
   product, target market (B2B/B2C/SMB/enterprise), stage (pre-launch / early /
   growth / scale), current metrics, and the specific decision to resolve. If
   context is vague, ask one targeted follow-up — vague context produces vague
   advice. (best-of: marketing-principles, positioning-basics)
2. **Track for decisions, not data.** Every metric or event should inform an
   action. Avoid vanity metrics. (best-of: analytics)
3. **Prioritize by impact / effort.** Lead with quick wins; map bigger work to
   "Do This Week / This Month / Deprioritize." (best-of: homepage-audit-style
   impact x effort matrix — MoonieX reimplementation)
4. **Ground claims in evidence.** Label assumptions vs. validated insight. Use
   real customer words and real competitor names, never placeholders.
5. **Respond in the user's language.** If they write in Thai or another
   language, answer in that language; sacrifice grammar for concision and list
   unresolved questions at the end. (best-of: paid-advertising)

---

## 1. ICP & Audience Definition
*(best-of: icp-builder)*

Run this first when targeting is unclear — it feeds ad targeting, positioning,
pricing, and content.

**Context to establish:** product, problem solved, current customers, market
type, price point, sales motion (self-serve / sales-assisted / enterprise),
stage, existing data (analytics, CRM, surveys), geography.

### B2B ICP (company-level)
```
FIRMOGRAPHICS   Industry, Size (employees/revenue), Growth stage, Geography, Business model
TECHNOGRAPHICS  Tech stack, Current solution, Technical maturity
TRIGGERS        Events creating urgency (raised funding, grew past 50 staff, contract ending, new VP)
QUALIFYING      Must-have, Nice-to-have, Disqualifying
```

### B2C ICP (individual-level)
```
DEMOGRAPHICS    Age, Income, Location, Life stage
PSYCHOGRAPHICS  Values, Identity, Aspirations, Influences
BEHAVIORAL      Platforms, Content consumed, Purchase behavior, Brand loyalty
```

### Pain points & goals
```
Pain Point: [problem], Severity 1-10, Frequency, Current workaround, Cost of inaction, Emotional impact, "Quote"
Goals: Primary (+ metric, timeframe), Secondary, Dream outcome
JTBD: "When I [situation], I want to [action], so I can [outcome]."
```
Pain categories: Functional, Financial, Process, Social, Emotional.

### Customer research instruments
- **Interviews:** target 10-15 (current 5-7, churned 2-3, prospects 3-5), 30-45
  min, structured Context -> Problem -> Solution -> Buying -> Close. Synthesize
  into common themes, surprising findings, validated/invalidated assumptions,
  ICP adjustments.
- **Survey:** 10-15 questions / 5-7 min (Screening, Problem, Solution,
  Demographics). Minimum 100 responses for quantitative, 30 for directional.

### Persona card
```
PERSONA: [e.g. "Marketing Mary"], Role, Company type, Age
BIO (2-3 sentences), GOALS vs FRUSTRATIONS, TOOLS, CHANNELS
BUYING: research style, decision speed, budget authority
MESSAGING: Do say "___" / Don't say "___", Key benefit, Proof needed
OBJECTION -> Response, JTBD, QUOTE
```

**Validation:** based on real data, 10+ customers match, ICP has higher LTV /
lower churn, reachable via identified channels, specific but not so narrow the
market disappears. Update every ~50 new customers, after pricing/feature
changes, or quarterly.

---

## 2. Positioning & Messaging
*(best-of: product-marketing for the April Dunford method + messaging hierarchy
+ battlecards; ICP/competitor inputs from section 1 and section 8)*

### Positioning (April Dunford method)
1. **Competitive alternatives** — what would customers use if you didn't exist?
   (direct, indirect, status quo)
2. **Unique attributes** — what you have that alternatives don't (matrix:
   You vs Comp A/B vs Status Quo). Focus on unique or significantly-better.
3. **Value ("So what?")** — translate each unique attribute into customer value
   (saves X hrs/week, cuts error rate Y%).
4. **Target customer** — who cares most about those values (firmographics, role,
   trigger, great-vs-okay characteristics).
5. **Market category** — the context that makes your value obvious (existing
   category / sub-category / new category — new is risky, needs education
   budget).

### Positioning statement template
```
For [target customer] who [situation/need],
[Product] is a [category] that [key benefit].
Unlike [named real alternative], we [key differentiator].
```

### Messaging hierarchy
```
L1 Positioning statement (internal)
L2 Value propositions — 3 pillars, each "Benefit — because proof point"
L3 Headlines & taglines (homepage headline + subhead)
L4 Feature messages — Feature -> Benefit -> Proof
```

### Messaging by audience
| Audience | Cares about | Emphasis |
|---|---|---|
| End user | Day-to-day workflow | Ease of use, time savings |
| Manager | Team productivity, oversight | Collaboration, reporting |
| Executive | Business outcomes, ROI | Revenue impact, cost reduction |
| Technical | Implementation, security | Architecture, APIs, compliance |
| Procurement | Risk, compliance, cost | Security, SLA, pricing model |

### Quality test (run before delivering positioning)
Specific, Differentiated (could a competitor say this? if yes, it isn't a
differentiator), Credible, Meaningful (pain they'd pay to fix), Memorable.
Revise and re-test on any fail.

> Positioning is a strategic framing decision, not tagline writing. Talk to
> customers before finalizing — internal assumptions are often wrong. The best
> positioning makes competition irrelevant, not merely inferior.

---

## 3. Pricing Strategy & Pricing-Page Design
*(best-of: pricing-strategy)*

**Context:** product, market, current pricing, cost structure (COGS, marginal
cost), value delivered, competitive pricing, current conversion, revenue model,
stage.

### Model selection
| Model | Best for | Watch |
|---|---|---|
| Freemium | Viral / low marginal cost | Low conv. 2-5% |
| Free trial (time) | Needs time to show value | Needs strong onboarding; 10-25% conv. |
| Flat rate | Simple, single persona | Leaves money on table |
| Per-seat | Collaboration tools | Discourages spreading |
| Usage-based | API / infra | Unpredictable revenue |
| Tiered | Most SaaS, distinct segments | Can overwhelm |
| Hybrid | Mature platforms | Complex |

Decision tree: low marginal cost + viral -> freemium; needs demo time -> free
trial (14d simple / 30d complex); scales with team -> per-seat; scales with
consumption -> usage-based; distinct segments -> tiered (3 tiers).

### Pricing psychology
Anchoring (show highest tier / compare to outcome value), Decoy effect, Charm
pricing ($99 vs $100; round numbers for enterprise), Center-stage (target =
middle of 3), Loss aversion, Endowment effect, Price-quality signal (don't
underprice premium).

### Tier design (3-tier)
- **Starter** — acquisition, low/no cost, enough value to demonstrate; natural
  upgrade triggers.
- **Pro (target)** — revenue engine, "Most Popular," 2-4x Starter.
- **Enterprise** — high WTP (SSO, audit logs, SLAs), custom/sales-assisted,
  2-5x Pro.

Feature gating: keep core value in all tiers; gate on scale (seats, storage,
API calls), admin/governance, and support level — never gate basic security.

### Pricing page
Value-focused headline -> billing toggle (show % + $ saved) -> highlighted
middle tier -> expandable comparison table -> social proof addressing price
objections -> FAQ (switch plans? after trial? discounts? refunds? cancel
anytime?) -> final CTA. Mobile: stack vertically, most-popular first, price font
2-3x larger.

### Pricing A/B safety
Never show different prices to the same user on repeat visits; test only new
visitors; run 30+ days; track downstream (churn, LTV); grandfather existing
customers. Pricing tests measure **revenue per visitor**, not just CR.

---

## 4. Paid Advertising (cross-platform)
*(best-of: paid-advertising — MIT, AgentKits/AityTech)*

Apply when planning paid strategy, optimizing ROAS, or allocating budget across
platforms. **Set up tracking/pixel BEFORE launching anything.**

### Objective by goal
| Objective | Use when | Primary KPI |
|---|---|---|
| Awareness | Building brand | CPM, reach |
| Traffic | Driving visits | CPC, CTR |
| Engagement | Growing social | CPE |
| Leads | Generating contacts | CPL, lead quality |
| Conversions | Driving sales | ROAS, CPA |
| App installs | Mobile acquisition | CPI |

### Funnel-based targeting
- **TOFU (cold):** broad interests, lookalikes 1-3%, video viewers; educational
  content; bid CPM/ThruPlay.
- **MOFU (warm):** site visitors 7-30d, email matches, engaged social; case
  studies/comparisons; bid landing-page views.
- **BOFU (hot):** high-intent (pricing/demo) visitors, cart abandoners 1-7d,
  trialists; offers/urgency/testimonials; bid conversions/ROAS.

### Platform cheat-sheet
- **Google:** Search (high-intent BOFU, exact match), Display (awareness/RTG),
  Shopping (feed optimization), Performance Max, YouTube (TOFU).
- **Meta:** Traffic, Conversions (Pixel + CAPI), Leads, Catalog/DPA,
  Advantage+.
- **LinkedIn (B2B):** Sponsored Content, Message Ads, Lead Gen Forms, Document
  Ads.

### Metrics & benchmarks
| Metric | Formula | Good | If below |
|---|---|---|---|
| CTR | Clicks/Impr | 1-3% | Improve creative/targeting |
| CPC | Spend/Clicks | <$1-5 (varies) | Improve quality score |
| CPL | Spend/Leads | <$20-100 | Optimize landing page |
| CPA | Spend/Conv | < 1/3 LTV | Full-funnel review |
| ROAS | Revenue/Spend | 3:1+ | Improve AOV or CVR |
| CVR | Conv/Clicks | 2-5% | Landing-page optimization |

### Budget allocation
- **Mature (70-20-10):** 70% proven, 20% optimization tests, 10% new
  channel/audience experiments.
- **Testing phase:** equal split until data; min viable spend $500-1000/test;
  2 weeks minimum per test.

### Optimization discipline
Let data accumulate (50+ conversions before major changes), one variable at a
time, weekly (not daily) review, segment by audience/placement.

**Anti-patterns:** launching without tracking, too-broad targeting, single
creative, daily bid changes, blaming ads for a weak landing page.

---

## 5. Facebook / Meta Ad Campaign Builder
*(best-of: facebook-ads — the deepest Meta-specific playbook)*

Use for Meta-specific builds. **Context first:** product, audience, objective,
budget (daily/lifetime), landing page, existing Pixel history, creative assets.

### Objective selection rule
If Pixel has <50 conversions/week -> start Traffic or Lead Gen. If 50+ ->
Conversions. No Pixel data on a new product -> Engagement to build social proof.

### Audience strategy
- **Core (interest):** sweet spot 1M-10M for conversion; exclude current
  customers and recent converters (7-14d).
- **Custom:** site visitors (30/60/90/180d), engaged (top 25% by time),
  add-to-cart abandoners (7-30d), video viewers (50/75/95%), page engagers
  (90d), customer-list upload (target 60%+ match).
- **Lookalike:** start 1% from purchasers (top 25% LTV) for conversions; expand
  to 3-5% only after 1% saturates; seed min 1,000 (ideal 5,000+).

### Ad formats & copy
- **Single image:** Primary text (125 visible / 2000 total) = hook + 2-3
  benefits + CTA; Headline <=40; Description <=30; CTA button.
- **Carousel (2-10 cards):** shared hook text; per-card headline (40) +
  description (20) + URL; story arc Problem -> Solution -> Proof -> CTA.
- **Video (15-60s):** 0-3s hook, 3-10s problem, 10-25s solution, 25-40s proof,
  40-50s offer/CTA. First 3s drive ~80% of performance; design sound-off with
  captions; square/vertical beats landscape.

Copy formulas: PAS, Before/After, Social-Proof Lead, Direct Offer.

### Budget & scaling
By funnel: TOFU 20-30%, MOFU 10-20%, BOFU 40-50%, Retention 10-20%. Min $10/day
per ad set or 2x target CPA; learning phase needs ~50 conv/7d; never raise
budget >20% at once. Scale vertically (+15-20% every 3-4 days), horizontally
(duplicate winners to new audiences), or by creative refresh.

### Naming convention
`[Brand]_[Objective]_[Funnel]_[Date]` / `[Audience]_[Detail]_[Placement]` /
`[Format]_[Concept]_[Version]`. Always include character counts and flag
overflows; provide 2-3 creative variations per format.

---

## 6. Landing-Page CRO & Homepage Audit
*(best-of: page-cro for the full optimization framework + benchmarks; audit
scoring/headline-rewrite pattern reimplemented MoonieX-style — see license note)*

### Benchmark conversion rates
| Industry | LP CR | Good | Excellent |
|---|---|---|---|
| SaaS (free trial) | 3-5% | 7% | 10%+ |
| SaaS (demo) | 2-4% | 5% | 8%+ |
| E-commerce | 2-3% | 4% | 6%+ |
| B2B lead gen | 2-5% | 6% | 10%+ |
| Financial | 2-4% | 5% | 8%+ |
| Education | 3-6% | 8% | 12%+ |
| Agency | 3-5% | 7% | 10%+ |

Paid converts 2-3x organic; mobile ~30-50% lower than desktop.

### Above-the-fold audit (decides 60-80% of stays)
Headline clarity (offer clear in <5s), benefit-led value prop, message match to
the ad/link, visual hierarchy, primary CTA visible without scroll, CTA contrast,
outcome-focused CTA copy, only one primary action.

Headline formulas: "[Outcome] without [pain]", "[N] [audience] use [product] to
[outcome]", "What if you could [outcome] in [timeframe]?", "Join [N] [audience]
who [outcome]". CTA copy: never "Submit/Click Here/Learn More" — use "Start My
Free Trial / Get My [Deliverable] / Book My Demo".

### Full-page audit
Social proof within first 2 scrolls (logos for B2B, ratings for e-comm,
testimonials addressing the #1 objection), benefits-led with "So what?" test
(3-5 blocks), 3-step "How it works", objection handling (price -> ROI, time ->
speed, trust -> credentials, risk -> guarantee, effort -> ease), FAQ (5-8 from
sales/support), repeated final CTA.

### Form optimization
*(best-of: form-cro)*

| Fields | Impact on CR |
|---|---|
| 1 (email) | baseline (highest) |
| 2-3 | -10 to -20% |
| 4-5 | -25 to -40% |
| 6+ | -40 to -80% |
Single column, labels above fields, inline validation, pre-fill, buttons
instead of dropdowns (<5 options), honeypot not CAPTCHA. Multi-step for 5+
fields (+20-40%).

**Field reduction (every field has a cost):** for each field ask — do we need
this *before* we can help them, can we get it another way (infer company from
email domain, enrich post-submit), can we ask it later? Defer everything
non-essential to progressive profiling. Sensitive fields (phone, company size)
last, after commitment is built.

**Single-step vs. multi-step:** single-step for ≤3-4 fields / high-intent
traffic; multi-step (one topic per step, progress indicator "step X of Y", back
navigation, save-on-refresh) once you cross 5 fields or have logically distinct
sections. Progressive-commitment order: low-friction start (email) → more detail
→ qualifying questions.

**Validation & error UX:** inline/real-time validation on field blur (not
aggressively mid-typing); specific, fixable error messages near the field
("Please enter a valid email, e.g. name@company.com" not "Invalid input");
never clear entered data on error; on submit, focus the first error field and
summarize if multiple. Email field: single (no confirm field) + typo detection
(gmial.com → gmail.com).

**Smart defaults, autofill & mobile:** pre-fill known/returning-visitor data,
autocomplete attributes for browser autofill, smart defaults where a sensible
one exists; correct mobile keyboards per field type (`type="email"` / `tel` /
`number`), 44px+ tap targets, single column, sticky submit.

**Trust near submit + button copy:** privacy reassurance ("No spam,
unsubscribe anytime" / "We'll never share your number"), effort cue ("Takes 30
seconds"), security badge only if collecting sensitive data, a testimonial
adjacent to the form. Button = action + outcome ("Get My Free Quote", not
"Submit"); show a loading state on click. Track form-start rate, completion
rate, and per-field drop-off to find the leaky field.

**MoonieX:** apply this to the **broker-connect (MT5 account-link) form** — ask
only the MT5 ID/account fields genuinely required to verify the IB link, defer
the rest, validate the account number inline, and reassure ("we only read your
trade volume for rebates") right at the submit button — and to the **register
form** (keep it to email/phone + minimal, see §11).

### Speed
| Load | Impact |
|---|---|
| 0-2s | baseline |
| 2-3s | -7% |
| 3-5s | -20% |
| 5-8s | -35% |
| 8s+ | -50%+ |
Target LCP <2.5s, CLS <0.1; WebP + lazy-load; 48x48px tap targets.

### Quick structured audit (when reviewing a specific page)
Require a URL, screenshot, or pasted above-the-fold copy before auditing, plus
business type, target customer, and primary conversion goal. Classify page type
(SaaS / Service / E-commerce) — scoring weights differ. Score sections (Above
the Fold, Value Prop, Social Proof, Clarity, CTA, Trust) and **always deliver a
before/after headline rewrite** plus an Impact x Effort priority list (3+ "Do
This Week", 2+ "This Month"). Flag anything you couldn't verify (e.g. real load
speed needs PageSpeed Insights).

### Output
```
CRO AUDIT — Page, Current CR, Benchmark, Traffic, Improvement potential
CRITICAL ISSUES -> fix -> expected impact
HIGH-IMPACT OPPORTUNITIES
A/B TEST ROADMAP (priority, lift, effort)
QUICK WINS (<1 hr)
DETAILED RECS (section-by-section with specific copy rewrites)
```
Prioritize by impact/effort; provide specific copy rewrites, not general advice.

---

## 7. A/B Testing & Experimentation
*(best-of: ab-test-setup; cross-ref the CRO hypotheses in section 6 and pricing
tests in section 3)*

### Hypothesis
```
OBSERVATION: [what the data/research/feedback showed]
HYPOTHESIS: If we [change], then [metric] will [delta] by [amount], because [reason].
CONTROL (A) / VARIANT (B) / PRIMARY METRIC / GUARDRAILS
```
Categories: Clarity, Motivation, Friction, Trust, Relevance.

### Sample size & duration
```
n = (Z_a/2 + Z_b)^2 * (p1(1-p1) + p2(1-p2)) / (p2 - p1)^2
Z_a/2 = 1.96 (95%), Z_b = 0.84 (80% power), p2 = p1*(1 + MDE)
```
Quick reference (per variant, 95%/80%):
| Baseline | 10% MDE | 15% | 20% | 25% |
|---|---|---|---|---|
| 2% | 385,040 | 173,470 | 98,740 | 63,850 |
| 5% | 148,640 | 67,040 | 38,200 | 24,730 |
| 10% | 70,420 | 31,780 | 18,120 | 11,740 |
| 20% | 31,310 | 14,140 | 8,070 | 5,230 |
Duration = (sample/variant x #variants) / daily traffic; min 7 days, max 8
weeks. If >8 weeks: raise MDE, fewer variants, higher-traffic page, or
micro-conversion metric.

### Test types
A/B (50/50), A/B/n (control + 2-4), MVT (100K+/mo), Bandit, Pre/Post (weakest
causal evidence).

### Discipline
Pre-launch checklist (hypothesis, sample size, cross-device QA, tracking
verified, no overlapping tests, exclusions, aligned decision criteria). During:
don't peek for 3-5 days, don't stop early unless guardrail violated, watch
sample-ratio-mismatch (>1% = setup bug), don't add variants mid-test. Run 2+
weeks for novelty effect; one primary metric (Bonferroni for extras); separate
statistical from practical significance.

### Prioritization (ICE)
`(Impact + Confidence + Ease)/3`, each 1-10. Run tests sequentially on the same
page to avoid interaction effects; maintain an ICE-ranked backlog.

---

## 8. Competitor Analysis
*(best-of: competitor-analysis for the full multi-channel breakdown + optional
API integrations; battlecards/win-loss from product-marketing)*

### Optional API integrations (all optional; web search works without them)
- `SEMRUSH_API_KEY` — domain overview, organic keywords, competitor discovery,
  keyword gap.
- `SERPAPI_API_KEY` — real-time SERP positions, competitor ad-copy extraction.
- `SCRAPINGBEE_API_KEY` — scrape JS-heavy / bot-protected pricing pages
  (charges per request — try WebFetch first).

### Identify
Direct (3-5), Indirect (2-3), Aspirational (1-2). Discover via Google top-10
(ads + organic), G2/Capterra compare pages, "[competitor] alternative" on
Reddit/Twitter, customer interviews, job posts, funding news.

### Analyze across channels
- **SEO:** DA/DR, organic traffic, ranking keywords, content strategy, backlink
  profile; gap analysis (keyword / content / backlink).
- **Paid:** est. spend, platforms, Google ad copy + landing pages, Meta Ad
  Library count/duration, LinkedIn formats.
- **Social:** followers, frequency, engagement, top content, community tone.
- **Email/lifecycle:** sign up for each list — newsletter cadence, onboarding
  sequence day-by-day, promo/discount patterns, retention emails.
- **Pricing & positioning:** comparison table, 2x2 positioning map (find white
  space), messaging extraction (tagline, value prop, differentiator, persona,
  tone, proof).

### Battlecard (per key competitor)
```
Quick facts: their positioning, pricing, target, strengths, weaknesses
Where we win: scenario -> why -> talk track
Where they win: scenario -> why -> counter
Common objections -> responses, Landmine questions to ask prospects
```
Weakness sources: G2/Capterra 1-2 star reviews, Reddit/Twitter complaints,
Glassdoor, support forums, feature gaps. Win/Loss log per deal (outcome,
competitor, deal size, decision-maker, why chosen, what could've changed,
cycle length). Refresh battlecards quarterly.

### SWOT + competitive matrix + strategic recs
SWOT each major competitor (with evidence). Matrix across founded, funding,
target market, entry price, key differentiator, DA, traffic, G2 rating,
features. Recommendations cover positioning, content, paid, product (build from
gaps / deprioritize), pricing, and 3 quick wins this week — each grounded in
specific competitor data.

---

## 9. Go-to-Market & Product Launch
*(best-of: launch-strategy for the week-by-week timeline + channel playbooks;
launch tiers from product-marketing)*

### Launch tier (which scale of launch)
| Tier | When | Activities | Goal |
|---|---|---|---|
| Tier 1 Major | New product, pivot, rebrand | Press, event, all channels | Max awareness |
| Tier 2 Medium | Major feature, integration | Blog, email, social, in-app | Adoption/upgrades |
| Tier 3 Minor | Update/improvement | Changelog, in-app, email | User awareness |

### Launch type (full public example: ~4-8 week prep, 1-day spike)
Stealth/Alpha, Closed Beta (50-500), Open Beta, Soft, Full Public, Rolling.

### Pre-launch
- **Weeks 8-6 Foundation:** positioning + one-sentence value prop, landing page
  (headline, demo video, 3 benefits, email capture, social proof, FAQ),
  analytics + email automation, 3-5 launch-week blog posts, 60-90s demo, press
  release draft, founder story.
- **Weeks 6-4 Audience:** build-in-public, referral waitlist, community
  engagement, micro-influencer outreach (20-50); waitlist targets — solo
  500-5,000+, small team 1,000-10,000+, funded 5,000-50,000+; select 50-200
  beta users with a feedback template.
- **Weeks 4-2 Momentum:** request testimonials, collect usage metrics,
  newsletter/cross-promo amplification, load-test for 10x traffic, war-room +
  on-call.

### Launch week
Day-before QA (product, page, links, queued posts, pixels, payment flows).
Launch day hour-by-hour: H0 publish everywhere + waitlist email + Product Hunt;
H1-4 respond to every mention, fix bugs; H4-12 "why we built this" post; H12-24
recap email + Day-2 plan.

**Channel playbooks:**
- **Product Hunt:** maker profile 2+ weeks early; tagline (60), description
  (260), 5+ images, maker comment (200+), 60-90s video; launch 12:01 AM PT,
  reply within 30 min, ask for "feedback" not "upvotes," target top 5.
- **Hacker News:** "Show HN: [Name] - [plain-English what]"; comment covers
  architecture, why built, honest limitations; post 8-10 AM ET Tue-Thu; no
  superlatives.
- **Social:** Twitter thread (hook -> problem -> solution+screenshot -> proof ->
  story -> CTA), LinkedIn personal story, Reddit value-first per sub rules.

### Post-launch (weeks 2-8)
W2 recap + first case study + retargeting + NPS; W3-4 SEO/comparison content +
onboarding optimization; W5-6 funnel analysis + LP A/B tests + referral program;
W7-8 scale paid + integrations + plan v2.

### Metrics & budget
Targets: waitlist CR 20-40%, beta activation 60%+, PH top 5, activation 40%+,
D1/D7/D30 retention 60/30/15%+, trial-to-paid 10-25%, NPS 40+. Track channel
attribution by quality (activation, retention, LTV), not volume. Budget:
Content 20-25%, Paid 30-40%, PR/Outreach 10-15%, Tools 5-10%, Reserve 10-15%
(double down on what works). Zero-budget path: network, Product Hunt, Show HN,
Reddit, Twitter thread, cold-email journalists, cross-promotion.

### Sales enablement package (per launch)
One-pager, pitch deck (10-15 slides), demo script, battlecards (section 8), ROI
calculator, case studies, FAQ.

---

## 10. Growth Analytics & Measurement
*(best-of: analytics — MIT, Corey Haines)*

Set up tracking that drives decisions; this data powers sections 3-9.

### Principles
Track for decisions not data, start from the questions (what will you do with
this?), name things consistently before implementing, maintain data quality
over volume.

### Tracking plan & event naming
Object-action, lowercase_underscores, specific (`cta_hero_clicked` not
`button_clicked`); context goes in properties, not the event name; no PII in
properties. Event types: pageviews, user actions, system events, custom
conversions.

Essential marketing-site events: `cta_clicked` (button_text, location),
`form_submitted` (form_type), `signup_completed` (method, source),
`demo_requested`. Product events: `onboarding_step_completed`, `feature_used`,
`purchase_completed` (plan, value), `subscription_cancelled` (reason).

Standard property groups: Page, User, Campaign (source/medium/campaign/content/
term), Product.

### GA4 + GTM
GA4 quick setup: property + data stream -> gtag/GTM -> enhanced measurement ->
custom events -> mark conversions.
```javascript
gtag('event', 'signup_completed', { method: 'email', plan: 'free' });
```
GTM = Tags (what fires) + Triggers (when) + Variables (dynamic values); push via
dataLayer.

### UTM strategy
| Param | Purpose | Example |
|---|---|---|
| utm_source | source | google, newsletter |
| utm_medium | medium | cpc, email, social |
| utm_campaign | campaign | spring_sale |
| utm_content | version | hero_cta |
| utm_term | paid keyword | running+shoes |
Lowercase, consistent separators, specific (`blog_footer_cta` not `cta1`),
documented in one spreadsheet.

### Validation & privacy
DebugView / GTM Preview / Tag Assistant. Checklist: events fire on correct
triggers, properties populate, no duplicates, cross-device, conversions
recorded, no PII leak. Privacy: consent mode (wait for consent), IP
anonymization, collect only what you need, support user deletion (EU/UK/CA
cookie consent).

---

## 11. Signup-Flow CRO
*(best-of: signup-flow-cro; distinct from §6 landing CRO — this is the
register / account-creation / activation flow itself, and uses §6 form rules as
its foundation)*

§6 optimizes the page that *leads to* signup; this section optimizes the
**signup flow** — every screen between "clicked sign up" and "activated."

### Signup friction audit
Map every step and field, then attack the worst. For each field ask the §6
reduction questions; the typical priority is Essential (email **or** phone,
password) / Often-needed (name) / Usually-deferrable (company, role, team size,
phone, address). Count steps, list required fields, find the drop-off step.

### Auth method trade-offs (social vs. email vs. OTP)
- **Social login** (Google/Apple/Microsoft/SSO): often the highest-converting —
  place prominently, frequently as the primary option, visually separated from
  the email form; pick the providers your audience actually uses.
- **Email + password:** show the password toggle + requirements upfront (not
  after failure), allow paste, strength meter over rigid rules; consider
  passwordless / magic-link to skip password friction entirely.
- **OTP (phone/SMS or email code):** lowest typing, mobile-friendly, doubles as
  verification — but adds a code-entry step and SMS deliverability risk; only
  require it when verification is genuinely needed.

### Progressive disclosure & deferred fields
Value first, signup second — let users experience as much as possible before the
account wall. Then **one field per step** where it reduces perceived effort,
lead with the easy fields, push customization/qualifying questions to *after*
account creation (or into onboarding). Don't show every option at once.

### Value reassurance & uncertainty removal at signup
"No credit card required" / "Free forever" / "14-day trial" near the CTA,
privacy note, a testimonial, and a clear preview of *what happens after signup*
(no surprise steps). Set expectations ("Takes 30 seconds").

### Post-submit / verification & time-to-first-value
Minimize the gap to the first "aha." Prefer instant access with verification
deferred or via magic link; let users explore while a verification email is
pending; clear resend + "check spam" + change-email options; auto-login after
signup rather than bouncing to a login screen.

### Dropoff diagnosis by step
Instrument each step (focus/blur/error per field, step progression, time
between steps, social-vs-email ratio) and read drop-off per step, not just an
overall rate — the leak is almost always one specific step or field.

**MoonieX:** optimize the `/register` → OTP → first-login path. The phone/email
OTP is the natural verification step — keep the form before it to the minimum
(phone or email only), defer broker/IB details to after the account exists, and
get the user to first value (their rebate dashboard / a calculator result) fast.
Critically, the signup steps are currently **unmeasured** — events like
`broker_connect_started` and `broker_verified` aren't fired, so per-step
drop-off is invisible. **Recommend instrumenting each step** (`register_started`,
`otp_sent`, `otp_verified`, `first_login`, then `broker_connect_started` →
`broker_verified`) per §10's naming convention before optimizing — you can't fix
a funnel you can't see.

---

## 12. Growth Loops

Acquisition and retention compounders that feed each other. Pick the loop(s)
that fit; instrument every one per §10 (an unmeasured loop can't be tuned).

### 12.1 Referral Program
*(best-of: referral-program)*

**Program design — the loop:** Trigger moment → Share action → Referred converts
→ Reward → (back to trigger). Place the ask at high-intent moments (right after
an "aha," a milestone, great support, a renewal/upgrade), not randomly. Lead
with the highest-converting share mechanism (in-product share > personalized
link > email invite > social > code).

**Incentive structure — one-sided vs. two-sided:**
- *One-sided* (referrer only): simpler, fits high-value products; risk = no
  urgency for the referred.
- *Two-sided* (both parties): higher conversion, win-win framing — the default.
- *Tiered/gamified:* sustains repeat referrals (cf. Morning Brew swag tiers).

**Reward type & timing:** cash/credit, product credit, free months, feature
unlock, swag, or charity — match to product (credit drives usage; cash feels
transactional). Size it with `Max reward = (LTV × gross margin) − target CAC`.
Pay **after** the referred user activates (not on signup) to blunt fraud.

**Fraud guardrails:** email verification, device/IP signals, delayed payout
after a meaningful action + activity threshold, reward clawback on
refund/chargeback, caps per period and lifetime, rewards in product credit
(less attractive to abusers).

**Viral-loop math:** k-factor `K = invites_sent × invite_conversion`; K>1 =
self-sustaining viral growth, K<1 = referrals amplify other channels (still
valuable). Watch **cycle time** (trigger → referred activates) — a smaller K
with a fast cycle can out-compound a bigger slow one. Referral rate benchmark:
good 10-25% of customers refer, great 25-50%. Referred users typically have
higher LTV and lower churn — track them as a cohort.

**Placement:** prominent in-product prompt + email reminders to non-referrers
(day 7 / 30 / post-milestone) + a referral landing page that surfaces the
referrer's endorsement.

**MoonieX:** this is a **user refer-a-friend** loop (one trader invites another,
both get a small reward) and must stay **distinct from the existing IB /
affiliate program** (revenue-share commission to partners who may not be
customers — the broker-rebate business itself). Don't conflate the two: the
referral loop drives peer signups with light incentives; the IB program is the
ongoing commission engine. (Affiliate-program design — commission tiers, cookie
windows, partner enablement — also lives in this skill if you formalize the IB
side, but keep the two programs and their tracking separate.)

### 12.2 Lead Magnets
*(best-of: lead-magnets)*

Gated content / content upgrades that trade value for an email (then nurture →
product). Principles: solve **one** specific problem, match the buyer stage
(awareness = educate, consideration = compare, decision = implement), high
perceived value + low time investment (consumable <10 min), and a **natural path
to the product** — the magnet should solve a problem your product also solves.

**Magnet types:** checklist / cheat-sheet (low effort), template
(doc/sheet/Notion), swipe file, ebook/guide, email or video mini-course,
quiz/assessment (also segments leads), webinar, resource library. One format —
don't mix ebook + video + spreadsheet.

**Value vs. friction (gating):** full gate (max capture, less reach) vs. partial
gate (preview + gated full) vs. ungated-with-optional-capture vs. inline content
upgrade (converts 2-5x a generic CTA). Ask for the minimum — email-only
converts best; every extra field costs ~5-10% (see §6). Frame the exchange:
obvious value ("the full 25-page guide, free"), a preview/mockup, social proof
("downloaded by 5,000+"), risk reducer ("no spam, unsubscribe anytime").

**Distribution:** in-post content upgrades, exit-intent/scroll popups matched to
page content, social teasers, paid lead ads / retargeting, partner
co-promotion.

**Capture → nurture handoff:** don't waste the thank-you page (confirm delivery
+ offer the next step). Deliver instantly (or email to verify), then a nurture
sequence relevant to the magnet topic with a clear path to product — this handoff
is where most lead magnets leak. Benchmarks: LP CR 20-40% warm / 5-15% cold;
judge by lead-to-customer rate, not raw captures.

**MoonieX:** strong fits for Thai retail traders — e.g. a "broker fee / spread
comparison sheet," an "XAUUSD trading-cost cheat-sheet," or a "rebate-maximizing
checklist" — gated for email/LINE, then nurtured toward a broker signup under
MoonieX's IB link.

### 12.3 Free-Tool Strategy (engineering-as-marketing)
*(best-of: free-tool-strategy)*

Free tools as a triple play: acquisition (shareable, link-worthy), SEO (rank for
"[thing] calculator" + attract backlinks because tools are referenceable), and
lead-gen. The tool must be genuinely useful **standalone**, adjacent to the core
product, simple/focused, and worth it (`lead value × leads > build + maintenance`,
plus SEO + brand halo).

**Tool selection:** calculators (numeric decisions), generators, analyzers/
auditors (curiosity + reveal a problem you solve), testers/validators, resource
libraries. Score candidates on search demand, audience-to-buyer match,
uniqueness, natural path to product, build feasibility, maintenance burden,
link/share potential. Ship an MVP (core function, clean input→output, mobile,
basic capture) and skip accounts/saving/edge-cases initially.

**Lead-capture pattern:** ungated tool with optional email-to-save/share-results
(max usage) → partial gate (preview free, email for the full report) → full gate
(high-value only). Value exchange explicit, email-only, show a preview of what
they get; then instant result email + a topic-relevant nurture toward the
product. Technical SEO matters: fast, mobile, crawlable (not JS-only), proper
meta + schema.

**Distribution:** launch (email, blog/landing page, social, Product Hunt) +
ongoing (tool keywords + supporting content + link outreach to "best free tools
for X" roundups) + product integration (link from sales/onboarding).

**MoonieX:** the **6 live calculators** (rebate-calc, position-size, pip,
risk-reward, xau-alert, economic-calendar) currently only **link out via
`ToolsCta`** with no capture and no measurement — they're pure SEO/brand right
now. Upgrade them into the loop: add an optional email/LINE capture ("save your
result" / "get the XAU alert by LINE") and **measure tool → signup** (fire
`tool_used` {tool} → `tool_lead_captured` → attribute to `signup_completed` /
broker signup per §10). This turns the existing tool factory into a lead engine
instead of a dead-end SEO asset.

### 12.4 Community-Led Growth
*(best-of: community-marketing)*

Community as a retention + referral compounder. Build around a **shared identity**
(who members are/aspire to be), not the product — members come for the product,
stay for the people. **Value flows to members first** (exclusive knowledge/early
signals, peer connection, status, roadmap influence).

**The flywheel:** members join → get value → engage → create content / help
others → new members discover → repeat. Every decision: does it accelerate or
slow the loop? Launch from zero by hand-recruiting 20-50 founding members,
setting culture explicitly, seeding conversations, and doing un-scalable things
(welcome everyone, reply to every post) to buy social proof.

**Advocates / ambassadors:** ~1% of members create ~90% of value — find people
already recommending you unprompted, make the ask 1:1, give meaningful benefits
(early signals, recognition, revenue share) + tools (referral links → §12.1,
shareable assets, a private channel), and measure the traffic/signups they
drive.

**Engagement cadence:** recurring rituals build habit — a weekly "what are you
trading / what are you working on?" thread, monthly AMA, seasonal challenge,
plus a new-member journey (pinned welcome, intro channel, "start here"). Watch
health signals: new-member post rate within 7 days, thread reply rate, % content
from non-staff, lurker ratio; warning sign = most posts are from staff.

**Community → product loop:** mine top questions into a knowledge base
(support deflection), recognize members who help others, and **close the loop**
— when community feedback ships, announce it and credit the members. Feeds §1
(real customer language) and churn reduction.

**MoonieX:** the **VIP LINE group / OpenChat** is the natural engine — run it as
a retention + referral loop, not a broadcast channel: identity = serious Thai
traders cutting their costs, rituals = daily XAU/market threads and rebate-win
shoutouts, advocates = top members who pull in friends under the IB link (tie to
§12.1), and route real questions/feedback back into LuNar's KB and the roadmap.

---

## Cross-Section Workflow

A typical full engagement chains the sections:
**Section 1 ICP -> Section 2 Positioning -> Section 3 Pricing -> Section 10
Analytics (instrument) -> Section 4/5 Paid + Section 6 CRO (acquire & convert)
-> Section 7 A/B (optimize) -> Section 8 Competitor (defend) -> Section 9 Launch
(when shipping).**
Each section's output is a valid input to the next; you rarely need to run all
ten in one pass — match the request to the relevant section(s).

---

## Sources & Updates

Merged skill — full per-feature attribution + pinned commits in `SOURCES.md`, license texts in `NOTICE.md`. Upstream repos (check these for updates):
- **paid-advertising** — https://github.com/aitytech/agentkits-marketing (MIT, © AgentKits / AityTech)
- **analytics** — https://github.com/coreyhaines31/marketingskills (MIT, © Corey Haines)
- **MoonieX-original** (MoonieX-owned, no upstream): icp-builder, product-marketing, pricing-strategy, facebook-ads, page-cro, ab-test-setup, competitor-analysis, launch-strategy
- Excluded (proprietary, no license — not shipped): homepage-audit, positioning-basics, marketing-principles (Brian Wagner)

To update: diff the repos above vs the pinned commits in `SOURCES.md`, port real fixes, re-pin (MoonieX wiki `playbooks/skill-maintenance.md`).
