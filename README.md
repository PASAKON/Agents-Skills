# mooniex-claude-skills

Curated Claude **skills** for the MoonieX org. Each skill merges the best features of several upstream skills into **one skill per domain**, so Claude selects unambiguously (no "which overlapping skill?" problem).

Every skill ships:
- `SKILL.md` — the curated, merged skill
- `SOURCES.md` — per-feature attribution (source · GitHub link · license · pinned commit)
- `NOTICE.md` — upstream license texts, kept verbatim
- `references/`, `scripts/` — supporting material (vetted, attributed)

All merged content is **permissively licensed** (MIT, Apache-2.0, or MoonieX-original) — see each skill's `SOURCES.md` + `NOTICE.md` for exact per-feature licensing.

## Skills

| Skill | Domain | License | Install |
|---|---|---|---|
| [`mooniex-seo`](./mooniex-seo) | SEO — technical, on-page, schema, CWV, content/E-E-A-T, programmatic, GEO | MIT | `npx skills add PASAKON/mooniex-claude-skills/mooniex-seo` |
| [`mooniex-growth`](./mooniex-growth) | Growth / marketing-ops — ICP, positioning, pricing, paid + Meta ads, CRO, A/B, competitor, GTM/launch, analytics | MIT + MoonieX-original | `npx skills add PASAKON/mooniex-claude-skills/mooniex-growth` |
| [`mooniex-content`](./mooniex-content) | Content / copy — copywriting, editing, content strategy, brand voice, channel adaptation, long-form | MIT + MoonieX-original | `npx skills add PASAKON/mooniex-claude-skills/mooniex-content` |
| [`mooniex-tool-builder`](./mooniex-tool-builder) | Build polished web tools — calculators, dashboards, widgets + production UI design | Apache-2.0 | `npx skills add PASAKON/mooniex-claude-skills/mooniex-tool-builder` |
| [`mooniex-kpi`](./mooniex-kpi) | Measurement — KPI choice, north-star, attribution, CAC/LTV/ROAS, funnel + cohort metrics, tracking plans | MIT + MoonieX-original | `npx skills add PASAKON/mooniex-claude-skills/mooniex-kpi` |
| [`mooniex-retention`](./mooniex-retention) | Retention / lifecycle — activation, onboarding, habit loops, drip email, churn, win-back, dunning | MIT + MoonieX-original | `npx skills add PASAKON/mooniex-claude-skills/mooniex-retention` |
| [`mooniex-image-gen`](./mooniex-image-gen) | Image-prompt ideation via the MeiGen MCP free tools — gallery search, inspiration, prompt enhancement | MoonieX-original | `npx skills add PASAKON/mooniex-claude-skills/mooniex-image-gen` |
| [`seedance-scene-prompt`](./seedance-scene-prompt) | Cinematic video-gen scene prompts in REFERENCE + VISUAL + (DIALOGUE) + AUDIO/SFX format for Seedance 2.0 | MoonieX-original | `npx skills add PASAKON/mooniex-claude-skills/seedance-scene-prompt` |

## Naming

`mooniex-<domain>` for skills whose domain word is generic enough to collide
(`seo`, `growth`, `content`, `kpi`, `retention`) — the prefix marks ownership and
keeps them distinguishable from whatever another plugin installs under the same
name. No `-skill` suffix: everything here is a skill, so it carried no
information.

A name that is already unambiguous does not take the prefix —
`seedance-scene-prompt` names a specific model and output format, so `mooniex-`
would add characters without adding meaning.

## Governance
Maintained per the MoonieX wiki: `playbooks/skill-maintenance.md` (the freshness ritual — check pinned upstreams, port only real fixes, re-pin) + `skills-registry.md` (index).

## License
This repository's curation is MIT (see [`LICENSE`](./LICENSE)). Each skill combines MIT-licensed upstream sources, credited per-feature in its `SOURCES.md` and preserved in its `NOTICE.md`.
