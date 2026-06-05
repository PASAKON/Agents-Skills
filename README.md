# mooniex-claude-skills

Curated Claude **skills** for the MoonieX org. Each skill merges the best features of several upstream skills into **one skill per domain**, so Claude selects unambiguously (no "which overlapping skill?" problem).

Every skill ships:
- `SKILL.md` — the curated, merged skill
- `SOURCES.md` — per-feature attribution (source · GitHub link · license · pinned commit)
- `NOTICE.md` — upstream license texts, kept verbatim
- `references/`, `scripts/` — supporting material (vetted, attributed)

All merged content is **MIT-licensed**.

## Skills

| Skill | Domain | Install |
|---|---|---|
| [`mooniex-seo-skill`](./mooniex-seo-skill) | SEO — technical, on-page, schema, Core Web Vitals, content/E-E-A-T, programmatic SEO, GEO/AI-search | `npx skills add PASAKON/mooniex-claude-skills/mooniex-seo-skill` |

## Governance
Maintained per the MoonieX wiki: `playbooks/skill-maintenance.md` (the freshness ritual — check pinned upstreams, port only real fixes, re-pin) + `skills-registry.md` (index).

## License
This repository's curation is MIT (see [`LICENSE`](./LICENSE)). Each skill combines MIT-licensed upstream sources, credited per-feature in its `SOURCES.md` and preserved in its `NOTICE.md`.
