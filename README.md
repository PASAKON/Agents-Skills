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

## Governance
Maintained per the MoonieX wiki: `playbooks/skill-maintenance.md` (the freshness ritual — check pinned upstreams, port only real fixes, re-pin) + `skills-registry.md` (index).

## License
This repository's curation is MIT (see [`LICENSE`](./LICENSE)). Each skill combines MIT-licensed upstream sources, credited per-feature in its `SOURCES.md` and preserved in its `NOTICE.md`.
