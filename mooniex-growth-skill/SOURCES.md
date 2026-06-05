# SOURCES — mooniex-growth-skill

Provenance, licensing, and attribution for the merged `mooniex-growth-skill`,
destined for the PUBLIC repo `PASAKON/mooniex-claude-skills`.

Inclusion rule applied: ship only **permissive-licensed (MIT/Apache/BSD)** or
**MoonieX-owned** content. Anything with unknown or non-permissive licensing was
EXCLUDED (see "License Concerns").

Research method: `~/.claude/skills/` is not a git repo, so provenance was
established by (a) resolving each skill's symlink/realpath, (b) byte/length
diffing local skills against their external namesakes, and (c) scanning each
SKILL.md for author/copyright footers. Findings recorded below.

---

## 1. Per-feature attribution table

| Merged section / feature | Source skill | Origin | License | Taken / Dropped + why |
|---|---|---|---|---|
| Sec 1 ICP & audience (firmographics, psychographics, pain/JTBD, interview + survey templates, persona card, validation) | `icp-builder` | MoonieX original (real dir, no external author footer) | MoonieX-owned | **Taken** — most complete ICP framework in the set; no overlap elsewhere |
| Sec 2 Positioning — April Dunford 5-step, messaging hierarchy, messaging-by-audience | `product-marketing` | MoonieX original (real dir; distinct from MIT `marketingskills/product-marketing`, which is a context-doc tool) | MoonieX-owned | **Taken (best-of: product-marketing)** — clearest positioning method + messaging tiers |
| Sec 2 Positioning quality test (Specific/Differentiated/Credible/Meaningful/Memorable) | `positioning-basics` | **Brian Wagner** (brianrwagner.com) | **Unknown / no LICENSE** | **Dropped as source; concept reimplemented** — the 5-check idea is generic CRO knowledge, but Wagner's exact prose is NOT shipped (see concerns) |
| Sec 3 Pricing — model selection, psychology, 3-tier design, gating, pricing page, A/B safety | `pricing-strategy` | MoonieX original (real dir; content-divergent from MIT `agentkits/pricing-strategy`) | MoonieX-owned | **Taken (best-of: pricing-strategy)** — self-contained and detailed |
| Sec 4 Paid advertising — objectives, funnel targeting, platform cheat-sheet, benchmarks, 70-20-10 budget, anti-patterns | `paid-advertising` (symlink) | AgentKits Marketing by AityTech — github.com/aitytech/agentkits-marketing | **MIT** (c) 2024-2025 AgentKits Team (AityTech) | **Taken (best-of: paid-advertising)** — permissive; best cross-platform paid overview |
| Sec 4 "Respond in user's language / token-efficient" operating rule | `paid-advertising` | AityTech | MIT | **Taken** — fits MoonieX Thai/EN bilingual use |
| Sec 5 Facebook/Meta — objective rule, custom/lookalike audiences, ad-format copy specs, scaling, naming | `facebook-ads` | MoonieX original (real dir, no external footer) | MoonieX-owned | **Taken (best-of: facebook-ads)** — deepest Meta-specific playbook |
| Sec 6 CRO — benchmarks, ATF audit, headline/CTA formulas, form & speed tables, heatmap, A/B hypotheses | `page-cro` | MoonieX original (real dir; content-divergent from MIT `agentkits/page-cro`) | MoonieX-owned | **Taken (best-of: page-cro)** — full optimization framework with benchmark tables |
| Sec 6 Audit scoring pattern (page-type weighting, headline before/after, impact x effort, self-critique) | `homepage-audit` | **Brian Wagner** (brianrwagner.com) | **Unknown / no LICENSE** | **Dropped as source; pattern reimplemented in MoonieX words** — Wagner's exact scoring rubric/prose NOT shipped (see concerns) |
| Sec 7 A/B testing — hypothesis, sample-size formula + table, test types, discipline, ICE | `ab-test-setup` | MoonieX original (real dir; content-divergent from MIT `agentkits/ab-test-setup`) | MoonieX-owned | **Taken (best-of: ab-test-setup)** — statistically rigorous, self-contained |
| Sec 8 Competitor — optional API integrations, multi-channel breakdown, SWOT, matrix, strategic recs | `competitor-analysis` | MoonieX original (real dir, no external footer) | MoonieX-owned | **Taken (best-of: competitor-analysis)** — broadest competitive coverage |
| Sec 8 Battlecard + Win/Loss templates | `product-marketing` | MoonieX original | MoonieX-owned | **Taken** — fills the sales-enablement gap competitor-analysis lacks |
| Sec 9 Launch — types, week-by-week pre-launch, launch-day hours, PH/HN/social playbooks, post-launch, metrics, budget | `launch-strategy` | MoonieX original (real dir; content-divergent from MIT `agentkits/launch-strategy`) | MoonieX-owned | **Taken (best-of: launch-strategy)** — most actionable GTM timeline |
| Sec 9 Launch tiers (Major/Medium/Minor) + sales-enablement package | `product-marketing` | MoonieX original | MoonieX-owned | **Taken** — complements launch-strategy with tiered framing |
| Sec 10 Analytics — principles, event naming, essential events, GA4/GTM, UTM, validation, privacy | `analytics` (symlink) | marketingskills by Corey Haines — github.com/coreyhaines31/marketingskills | **MIT** (c) 2025 Corey Haines | **Taken (best-of: analytics)** — permissive; best measurement reference |
| Operating principles (context-first intake, decision-not-data, evidence-grounding) | `marketing-principles` + `analytics` + `positioning-basics` | mixed (see concerns) | mixed | **Concept taken, Wagner prose dropped** — "context before output" is generic; restated in MoonieX words, not copied |

---

## 2. Credited sources

| Source | Author / Owner | Origin URL | License | Status in merge |
|---|---|---|---|---|
| paid-advertising | AgentKits Team (AityTech) | https://github.com/aitytech/agentkits-marketing | MIT | **Included** (Sec 4) — attribution required & given |
| analytics | Corey Haines | https://github.com/coreyhaines31/marketingskills | MIT | **Included** (Sec 10) — attribution required & given |
| facebook-ads | MoonieX | (internal — `~/.claude/skills/facebook-ads/`) | MoonieX-owned | **Included** (Sec 5) |
| page-cro | MoonieX | (internal — `~/.claude/skills/page-cro/`) | MoonieX-owned | **Included** (Sec 6) |
| ab-test-setup | MoonieX | (internal — `~/.claude/skills/ab-test-setup/`) | MoonieX-owned | **Included** (Sec 7) |
| launch-strategy | MoonieX | (internal — `~/.claude/skills/launch-strategy/`) | MoonieX-owned | **Included** (Sec 9) |
| icp-builder | MoonieX | (internal — `~/.claude/skills/icp-builder/`) | MoonieX-owned | **Included** (Sec 1) |
| competitor-analysis | MoonieX | (internal — `~/.claude/skills/competitor-analysis/`) | MoonieX-owned | **Included** (Sec 8) |
| pricing-strategy | MoonieX | (internal — `~/.claude/skills/pricing-strategy/`) | MoonieX-owned | **Included** (Sec 3) |
| product-marketing | MoonieX | (internal — `~/.claude/skills/product-marketing/`) | MoonieX-owned | **Included** (Sec 2, 8, 9) |
| homepage-audit | Brian Wagner | brianrwagner.com (no repo/LICENSE located) | **Unknown / non-permissive** | **EXCLUDED** — only the generic pattern reimplemented |
| positioning-basics | Brian Wagner | brianrwagner.com (no repo/LICENSE located) | **Unknown / non-permissive** | **EXCLUDED** — only the generic pattern reimplemented |
| marketing-principles | Brian Wagner | brianrwagner.com (no repo/LICENSE located) | **Unknown / non-permissive** | **EXCLUDED** — only the generic "context-first" concept reimplemented |

> NOTE on the 5 name-collision skills (`page-cro`, `ab-test-setup`,
> `launch-strategy`, `pricing-strategy`, `product-marketing`): each shares a
> *name* with an MIT skill in agentkits-marketing or marketingskills, but the
> local MoonieX copies are content-divergent (different `description`, no
> `brand:`/`version:` frontmatter, ~2-3x shorter, different frameworks). They
> are treated as MoonieX-owned rewrites. Even in the worst case (if any phrasing
> was originally seeded from those repos), the upstreams are MIT, so inclusion
> remains license-safe.

---

## 3. Pinned versions

| Item | Pin (commit SHA / path) | Date observed |
|---|---|---|
| agentkits-marketing repo (paid-advertising source) | `8dcf8bf64a683db7e6763e99076b3f62252c2bce` (origin/main, "bump-version-1.7.2") | 2026-06-05 |
| agentkits-marketing LICENSE | MIT, `/Users/gob/Projects/external/agentkits-marketing/LICENSE` | 2026-06-05 |
| marketingskills repo (analytics source) | `7f4af1ea8e7809e0142c55bf19243a706f539c25` (origin/main, PR #343 merge) | 2026-06-05 |
| marketingskills LICENSE | MIT, `/Users/gob/Projects/external/marketingskills/LICENSE` | 2026-06-05 |
| MoonieX-owned skills (8) | path-pinned: `~/.claude/skills/{facebook-ads,page-cro,ab-test-setup,launch-strategy,icp-builder,competitor-analysis,pricing-strategy,product-marketing}/SKILL.md` — not under git, no SHA available | 2026-06-05 |
| Excluded Wagner skills (3) | path-pinned: `~/.claude/skills/{homepage-audit,positioning-basics,marketing-principles}/SKILL.md` — author footer "Skill by Brian Wagner / brianrwagner.com" | 2026-06-05 |

---

## License Concerns (summary)

**EXCLUDED — 3 skills, third-party author, no permissive license found:**
`homepage-audit`, `positioning-basics`, `marketing-principles` each end with the
footer `*Skill by Brian Wagner | AI Marketing Architect | brianrwagner.com*`.
They are real directories under `~/.claude/skills/` with **no LICENSE/NOTICE
file** anywhere (not in the dir, not in any parent repo — they are not symlinks
and `~/.claude` is not a git repo, so there is no upstream to inspect). No public
repo or license was locatable. Under the "permissive or MoonieX-owned only" rule,
their prose must not be copied into the public repo. Only the generic,
non-copyrightable concepts they happen to use (gather-context-first, a 5-point
positioning sanity check, an impact x effort priority matrix, a before/after
headline rewrite step) were reimplemented in original MoonieX wording — these
patterns are industry-standard and also appear in the MIT and MoonieX-owned
sources. For their exact rubrics verbatim, obtain written permission from Brian
Wagner or a permissive license first.

**INCLUDED with required attribution — 2 MIT skills:** `paid-advertising` (MIT,
AgentKits/AityTech) and `analytics` (MIT, Corey Haines). MIT requires retaining
the copyright + permission notice — see `NOTICE.md`.

**INCLUDED as MoonieX-owned — 8 skills:** `facebook-ads`, `page-cro`,
`ab-test-setup`, `launch-strategy`, `icp-builder`, `competitor-analysis`,
`pricing-strategy`, `product-marketing`. No copyleft (GPL) or proprietary
content is present in the merged output.
