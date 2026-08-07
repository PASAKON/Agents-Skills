# SOURCES & Attribution — mooniex-seo

`mooniex-seo` is a curated merge of three upstream SEO skills. It exists so
the MoonieX org uses ONE SEO skill instead of 3–4 overlapping ones. Every feature
below is credited to its origin. **All three sources are MIT-licensed** —
permissive, safe to combine and redistribute with attribution.

## Credited sources

| # | Source | Origin / GitHub | License |
|---|--------|-----------------|---------|
| 1 | **claude-seo** (community, comprehensive) | https://github.com/AgriciDaniel/claude-seo | MIT |
| 2 | **ecc:seo** skill + **seo-specialist** agent | ECC plugin marketplace (`skills/seo/SKILL.md`, `agents/seo-specialist.md`) | MIT — Copyright (c) 2026 Affaan Mustafa |
| 3 | **programmatic-seo** skill | Part of the `marketingskills` collection: https://github.com/coreyhaines31/marketingskills (`skills/programmatic-seo/`) | MIT — Copyright (c) 2025 Corey Haines |

> Note: programmatic-seo had no LICENSE file in its own subfolder; it is a sub-skill
> of `coreyhaines31/marketingskills`, whose repo root carries an MIT license
> (Copyright (c) 2025 Corey Haines). Verified by reading the parent repo LICENSE.

## Pinned versions (for future upstream diffs — see `playbooks/skill-maintenance.md`)

| Source | Pin | How captured |
|--------|-----|--------------|
| claude-seo | commit `dabfc1abb4ca9a4d7967242bf00d52593be56ed1` (branch `main`, examined 2026-06-05) | `gh api repos/AgriciDaniel/claude-seo/commits/main` |
| ecc:seo + seo-specialist | ECC marketplace checkout `c0f8c3bc813360f29e9f2b66bcae7e977cd03327` (examined 2026-06-05) | `git -C ~/.claude/plugins/marketplaces/ecc rev-parse HEAD` |
| programmatic-seo (marketingskills) | skill `version: 2.0.0` (examined 2026-06-05) | SKILL.md frontmatter; repo `coreyhaines31/marketingskills` |

## Per-feature attribution

| Feature / section | Source | License | Taken / dropped + why |
|---|---|---|---|
| Operating principles (fix tech before content, one-intent-per-page, mobile-first) | ecc:seo | MIT | **Taken** — cleanest, most concise principle list |
| "Read the real page/source first" + severity model (Critical/High/Medium) | seo-specialist agent (ecc) | MIT | **Taken** — best prioritization framework |
| Technical audit — Crawlability checklist | claude-seo `seo-technical` | MIT | **Taken (best-of)** — 10-category checklist, most complete; ecc's shorter list merged in |
| Technical audit — Indexability checklist | claude-seo `seo-technical` | MIT | **Taken (best-of)** — supersedes ecc's shorter version |
| Technical audit — Security headers / HTTPS | claude-seo `seo-technical` | MIT | **Taken** — only source covering security headers |
| Technical audit — URL structure, redirects ≤2 hops | claude-seo + ecc:seo | MIT | **Merged** — claude-seo URL rules + ecc's explicit "no chains >2 hops" |
| Technical audit — Mobile checks | claude-seo `seo-technical` | MIT | **Taken** — concrete thresholds (48px, 16px) |
| Technical audit — JS rendering (CSR/SSR, canonical parity) | claude-seo `seo-technical` | MIT | **Taken** — unique to claude-seo |
| Technical audit — IndexNow / Speculation Rules / bfcache / agent-friendly | claude-seo `seo-technical` | MIT | **Taken** — modern signals, unique to claude-seo |
| On-page — title (~50–60), meta (~120–160), single H1, formulas | ecc:seo | MIT | **Taken (best-of)** — tightest concrete thresholds + copy formulas |
| Images — alt text + dimensions for CLS | ecc:seo + claude-seo `seo-images` | MIT | **Merged** — kept lean; full image-gen pipeline dropped |
| Schema — JSON-LD preference + validation rules | claude-seo `seo-schema` | MIT | **Taken (best-of)** — concrete validation rules |
| Schema — per-page-type quick map | ecc:seo | MIT | **Taken (best-of)** — cleanest at-a-glance table |
| Schema — Active/Restricted/Deprecated type status | claude-seo `seo-schema` | MIT | **Taken** — ONLY source with current deprecation rules; load-bearing for legality of recommendations |
| Schema — JSON-LD example snippet | ecc:seo | MIT | **Taken** — compact example |
| Core Web Vitals thresholds (LCP/INP/CLS) | ecc:seo + claude-seo | MIT | **Merged** — identical thresholds; claude-seo adds CrUX-field-vs-lab + "INP replaced FID" |
| CWV common fixes (preload, reserve space, trim JS) | ecc:seo | MIT | **Taken** — actionable list |
| Sitemaps & robots | claude-seo `seo-sitemap` + ecc:seo | MIT | **Merged** — split-by-type (claude-seo) + public-surface discipline (ecc) |
| Keyword mapping 5-step | ecc:seo | MIT | **Taken (best-of)** — tightest procedure incl. cannibalization |
| Content quality / E-E-A-T (Who/How/Why) | claude-seo `seo-content` | MIT | **Taken** — ONLY source with E-E-A-T framework |
| Internal linking | ecc:seo + programmatic-seo | MIT | **Merged** — ecc anchor rules + pSEO hub-and-spoke |
| Programmatic SEO core rules (unique value, proprietary-data hierarchy, subfolders) | programmatic-seo (marketingskills) | MIT | **Taken (best-of)** — ONLY source for pSEO |
| The 12 playbooks | programmatic-seo (marketingskills) | MIT | **Taken** — condensed inline; full detail in `references/playbooks.md` |
| pSEO build framework + pre-launch checklist + monitoring | programmatic-seo (marketingskills) | MIT | **Taken** — practical, unique |
| Multi-location doorway guardrail (30 warn / 50 stop) | claude-seo `seo-local` | MIT | **Taken** — concrete penalty guardrail, reinforces pSEO |
| AI Search / GEO | claude-seo `seo-geo` | MIT | **Taken** — ONLY source covering AI-search/GEO |
| Audit output format `[SEVERITY] / Location / Issue / Fix` | ecc:seo + seo-specialist | MIT | **Taken (best-of)** — identical in both; standard shape |
| Anti-patterns table | ecc:seo (base) + claude-seo (deprecated-schema, FID, doorway rows) | MIT | **Merged** |

## Features deliberately DROPPED (kept out of the merged skill)

| Dropped feature | Source | Why dropped |
|---|---|---|
| 54 Python scripts (`render_page.py`, `pagespeed_check.py`, `gsc_*`, `ga4_report.py`, etc.) | claude-seo `scripts/` | This is a prompt-guidance skill, not a bundled Python tool/runtime. Noted so a maintainer knows the deep tooling exists upstream. |
| 8 MCP extensions (DataForSEO, Firecrawl, Ahrefs, SE Ranking, Profound, Bing Webmaster, Unlighthouse) | claude-seo `extensions/` | External paid/API integrations; out of scope for a self-contained skill |
| 18 specialist sub-agents + parallel-agent orchestration | claude-seo | Org uses one skill, not a multi-agent fleet; orchestration belongs to the CTO layer |
| PDF report generation (WeasyPrint + matplotlib) | claude-seo `pdf/` | Tooling, not guidance |
| **FLOW framework prompts** | claude-seo `seo-flow` | **CC BY 4.0, NOT MIT** — excluded to keep the merge cleanly MIT. Revisit only with explicit CC-BY attribution. |
| `homepage-audit` / CRO content | (separate skill) | Out of scope — conversion domain, stays its own skill |

## License summary
- claude-seo, ecc:seo, programmatic-seo (marketingskills) — **all MIT**, safe to combine + redistribute with the attribution above (MIT requires preserving the copyright + permission notice; `NOTICE.md` does this).
- The claude-seo **FLOW** sub-feature is **CC BY 4.0** and was **excluded** from this merge.
- No copyleft (GPL/AGPL) in any retained source — no viral-license risk.

## Maintenance
A future upstream diff should re-read claude-seo's `seo-content`, `seo-geo`,
`seo-local`, `seo-sitemap` sub-skills directly (all pinned at `dabfc1a`) — this
draft used the README + the two most load-bearing sub-skills (`seo-technical`,
`seo-schema`). See `playbooks/skill-maintenance.md` in the MoonieX wiki.
