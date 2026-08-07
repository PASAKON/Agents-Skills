# SOURCES — mooniex-retention

Provenance, licensing, and attribution for the merged `mooniex-retention`,
destined for the PUBLIC repo `PASAKON/mooniex-claude-skills`.

Inclusion rule applied: ship only **permissive-licensed (MIT/Apache/BSD)** or
**MoonieX-owned** content. All five source skills resolve to MIT-licensed repos,
so all are includable; the MoonieX-specific §5 playbook is MoonieX-owned.

Research method: each source skill lives in a git repo under
`/Users/gob/Projects/external/`. Provenance was established by (a) reading each
SKILL.md body and its `references/` subfolder, (b) reading the repo `LICENSE`
file, and (c) recording the repo `origin` URL + HEAD commit. Findings below.

---

## 1. Per-feature attribution table

| Merged section / feature | Source skill | Origin | License | Taken / Dropped + why |
|---|---|---|---|---|
| Sec 1 Activation — aha-moment definition, activation-metric discovery, TTV (5-minute rule), onboarding patterns (wizard/checklist/empty-state/tour), failure modes, completion metrics | `onboarding-cro` | AgentKits Marketing by AityTech — github.com/aitytech/agentkits-marketing | **MIT** © 2024-2025 AgentKits Team (AityTech) | **Taken (best-of: onboarding-cro)** — clearest activation + onboarding framework; benchmark/TTV detail from its `references/activation-playbook.md` |
| Sec 1 Activation — B=MAP, the Ability Chain (six simplicity factors), friction audit, Starter Step, retention diagnostics by drop-off day | `improve-retention` | Wondel.ai — github.com/wondelai/skills | **MIT** © 2025 Wondel.ai sp. z o.o. | **Taken (best-of: improve-retention)** — behavior-design backbone; Ability Chain detail from its `references/ability-chain.md` (BJ Fogg method, reimplemented) |
| Sec 2 Habit Loops — Hook Model (Trigger/Action/Variable Reward/Investment), internal-vs-external triggers, three reward types (Tribe/Hunt/Self), notification/Action-Line strategy, Manipulation Matrix + regret test | `hooked-ux` | Wondel.ai — github.com/wondelai/skills | **MIT** © 2025 Wondel.ai sp. z o.o. | **Taken (best-of: hooked-ux)** — the habit-loop framework; reward detail from its `references/rewards.md` (Nir Eyal Hook Model, reimplemented) |
| Sec 3 Lifecycle Email — one-email-one-job principles, welcome/nurture/re-engagement/win-back sequence templates, behavioral triggers, timing cadence, deliverability + metrics | `email-sequence` | AgentKits Marketing by AityTech — github.com/aitytech/agentkits-marketing | **MIT** © 2024-2025 AgentKits Team (AityTech) | **Taken (best-of: email-sequence)** — most complete lifecycle-email reference; sequence detail from its `references/sequence-templates.md` |
| Sec 4 Churn Prevention — voluntary vs involuntary split, cancel-flow structure, exit survey, offer-to-reason mapping, save-offer types, health-score model, dunning stack (pre-dunning/smart-retry/emails/grace), recovery benchmarks | `churn-prevention` | marketingskills by Corey Haines — github.com/coreyhaines31/marketingskills | **MIT** © 2025 Corey Haines | **Taken (best-of: churn-prevention)** — deepest churn + dunning playbook; retry/email detail from its `references/dunning-playbook.md` + `references/cancel-flow-patterns.md` |
| Sec 5 MoonieX Retention Playbook (activation gap, verified-but-silent cohort, CTA STEP 5 gap, `vip_joined_at` recommendation, broken weekly-digest) | — (MoonieX original) | MoonieX codebase (`mooniex-webapp`, `mooniex-claudeflow`) | MoonieX-owned | **Original** — grounded in real tables/files (`webapp_broker_accounts`, `claudeflow_verify_tickets`, `claudeflow_lunar_turns`, `src/webhook/line.js pushText()`, `/api/cron/weekly-digest`); not derived from any source skill |
| Operating principles (activation-before-retention, cohort-not-vanity, reduce-TTV, ethical habit design, one-experiment-at-a-time) | `onboarding-cro` + `improve-retention` + `hooked-ux` | mixed (all MIT, above) | MIT | **Concept taken, restated** — generic retention discipline, reworded MoonieX-style |

---

## 2. Credited sources

| Source | Author / Owner | Origin URL | License | Status in merge |
|---|---|---|---|---|
| onboarding-cro | AgentKits Team (AityTech) | https://github.com/aitytech/agentkits-marketing | MIT | **Included** (Sec 1) — attribution required & given |
| email-sequence | AgentKits Team (AityTech) | https://github.com/aitytech/agentkits-marketing | MIT | **Included** (Sec 3) — attribution required & given |
| improve-retention | Wondel.ai sp. z o.o. | https://github.com/wondelai/skills | MIT | **Included** (Sec 1) — attribution required & given |
| hooked-ux | Wondel.ai sp. z o.o. | https://github.com/wondelai/skills | MIT | **Included** (Sec 2) — attribution required & given |
| churn-prevention | Corey Haines | https://github.com/coreyhaines31/marketingskills | MIT | **Included** (Sec 4) — attribution required & given |
| MoonieX Retention Playbook | MoonieX | (internal — `mooniex-webapp` + `mooniex-claudeflow` codebase) | MoonieX-owned | **Included** (Sec 5) |

> NOTE: `improve-retention` and `hooked-ux` adapt the published frameworks of
> BJ Fogg (Fogg Behavior Model / Tiny Habits) and Nir Eyal (Hook Model)
> respectively. The merged skill uses the *concepts* (which are widely taught
> industry knowledge), reimplemented in MoonieX wording with forex/LuNar
> examples — it does not copy the upstream prose verbatim. The wondelai SKILL
> files themselves are MIT, so inclusion is license-safe; the books are credited
> as further-reading lineage, not shipped.

---

## 3. Pinned versions

| Item | Pin (commit SHA / path) | Date observed |
|---|---|---|
| agentkits-marketing repo (onboarding-cro + email-sequence source) | `8dcf8bf64a683db7e6763e99076b3f62252c2bce` (origin/main) | 2026-06-15 |
| agentkits-marketing LICENSE | MIT, `/Users/gob/Projects/external/agentkits-marketing/LICENSE` | 2026-06-15 |
| wondelai-skills repo (improve-retention + hooked-ux source) | `eff8b3cab2d9afab9dc09c4cc04e80ad9641db29` (origin/main) | 2026-06-15 |
| wondelai-skills LICENSE | MIT, `/Users/gob/Projects/external/wondelai-skills/LICENSE` | 2026-06-15 |
| marketingskills repo (churn-prevention source) | `7f4af1ea8e7809e0142c55bf19243a706f539c25` (origin/main) | 2026-06-15 |
| marketingskills LICENSE | MIT, `/Users/gob/Projects/external/marketingskills/LICENSE` | 2026-06-15 |
| MoonieX §5 facts | path-pinned: `mooniex-webapp` (`/api/cron/weekly-digest`, `auth_signup`, `webapp_broker_accounts`, `webapp_credits_orders`) + `mooniex-claudeflow` (`src/webhook/line.js` `pushText()` @ line 551, `claudeflow_verify_tickets`, `claudeflow_lunar_turns`, `claudeflow_subscriptions`) | 2026-06-15 |

---

## License Concerns (summary)

**INCLUDED with required attribution — 5 MIT skills across 3 repos:**
`onboarding-cro` + `email-sequence` (MIT, AgentKits/AityTech), `improve-retention`
+ `hooked-ux` (MIT, Wondel.ai sp. z o.o.), `churn-prevention` (MIT, Corey Haines).
MIT requires retaining the copyright + permission notice — see `NOTICE.md`.

**INCLUDED as MoonieX-owned — Sec 5:** the MoonieX Retention Playbook is original
work grounded in the MoonieX codebase. No copyleft (GPL) or proprietary
third-party content is present in the merged output.

**No exclusions.** Unlike the growth-skill merge, every retention source resolves
to a permissive (MIT) repo, so nothing had to be dropped for licensing.
