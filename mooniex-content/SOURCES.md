# SOURCES — mooniex-content

Attribution and license provenance for the merged `mooniex-content`.
Target repo `PASAKON/mooniex-claude-skills` is **PUBLIC**, so only permissive
(MIT/Apache/BSD) or MoonieX-owned content ships verbatim. Anything with an
unknown/non-permissive license is **excluded entirely** and flagged below.

Researched 2026-06-05 on the org workstation.

---

## A. Per-feature attribution

| Feature (skill section) | Source skill | Origin / location | License | Taken / dropped + why |
|---|---|---|---|---|
| §1 Copywriting (frameworks, headlines, CTAs, tone, LP structure) | `copywriting` | `~/.claude/skills/copywriting/` — **real dir**, no third-party byline | **MoonieX-owned** (hand-written/internal) | **Taken** verbatim/condensed. No external license risk. |
| §2 Copy Editing (process, checklist, Hemingway, readability) | `copy-editing` | `~/.claude/skills/copy-editing/` — **real dir**, no byline | **MoonieX-owned** | **Taken** verbatim/condensed. |
| §3 Content Strategy (clusters, buyer journey, mix, cadence, distribution, repurposing) | `content-strategy` | `~/.claude/skills/content-strategy/` — **real dir**, no byline | **MoonieX-owned** | **Taken** verbatim/condensed. |
| §5 Brand Voice (when-to-run, source priority, extraction list, `VOICE PROFILE` schema, hard bans, persistence) | ECC `brand-voice` (+ `references/voice-profile-schema.md`) | `~/.claude/plugins/marketplaces/ecc/skills/brand-voice/` — ECC marketplace | **MIT** © 2026 Affaan Mustafa | **Taken** (schema + workflow), MIT permits with attribution. |
| §6 Channel Adaptation (per-platform rules, repurposing flow, quality gate) | ECC `content-engine` | `~/.claude/plugins/marketplaces/ecc/skills/content-engine/` | **MIT** © 2026 Affaan Mustafa | **Taken** (platform rules + repurposing flow). |
| §7 Long-Form Writing (core rules, process, structure, banned patterns, quality gate) | ECC `article-writing` | `~/.claude/plugins/marketplaces/ecc/skills/article-writing/` | **MIT** © 2026 Affaan Mustafa | **Taken** (long-form rules + banned patterns). |
| §8 Marketing Idea Bank (12 categories, stage/budget/timeline selection) | `marketing-ideas` | `~/.claude/skills/marketing-ideas/` — **real dir**, no byline | **MoonieX-owned** | **Taken as index only.** Full 139-item list kept as a referenced org asset to keep the merged file lean; category structure + selection guidance included. |
| §9 Cross-Cutting Rules | synthesized | de-duplicated from copywriting + copy-editing + ECC bans | **MoonieX-owned** (synthesis) | New synthesis to DRY the repeated "reader-over-brand / proof-over-adjectives / kill AI tells" rules. |

> §4 (Idea Generation) is intentionally **absent**. It derived from the non-permissive
> `content-idea-generator` skill and was dropped before publishing — see §D and the
> EXCLUDED note below. Section numbering keeps the gap on purpose.

---

## B. Credited sources (shipped)

| Skill | Author / owner | License | Used? |
|---|---|---|---|
| copywriting | MoonieX (original) | MoonieX-owned | Yes — §1 |
| copy-editing | MoonieX (original) | MoonieX-owned | Yes — §2 |
| content-strategy | MoonieX (original) | MoonieX-owned | Yes — §3 |
| marketing-ideas | MoonieX (original) | MoonieX-owned | Yes — §8 |
| brand-voice (ECC) | Affaan Mustafa / everything-claude-code | MIT | Yes — §5 |
| article-writing (ECC) | Affaan Mustafa / everything-claude-code | MIT | Yes — §7 |
| content-engine (ECC) | Affaan Mustafa / everything-claude-code | MIT | Yes — §6 |

### MIT attribution block to ship in the public repo (also in `NOTICE.md`)
```
Portions derived from the "everything-claude-code" (ECC) marketplace skills
brand-voice, article-writing, and content-engine.
Copyright (c) 2026 Affaan Mustafa. Licensed under the MIT License.
Source: https://github.com/affaan-m/everything-claude-code
```

---

## B2. EXCLUDED sources (proprietary / not permissively licensed — NOT shipped)

These were evaluated as merge sources but **excluded from the public repo**. No text,
structure, or section derived from them appears in the shipped `SKILL.md`.

| Skill | Author / owner | License | Disposition |
|---|---|---|---|
| `content-idea-generator` | Brian Wagner (brianrwagner.com) | **UNKNOWN / proprietary** — commercial author byline, no LICENSE file present | **EXCLUDED.** Formerly drafted as §4; the entire section was removed before publishing. Nothing from this skill ships. |
| `voice-extractor` | Brian Wagner (brianwagner4.gumroad.com) | **UNKNOWN / proprietary** — commercial gumroad product, no LICENSE file present | **EXCLUDED.** The same need (voice extraction) is met by ECC's MIT `brand-voice` in §5. No `voice-extractor` text reused. |

---

## C. Pinned versions

| Item | Pin |
|---|---|
| ECC marketplace repo | `https://github.com/affaan-m/everything-claude-code` |
| ECC commit (HEAD at research time) | `c0f8c3bc813360f29e9f2b66bcae7e977cd03327` |
| ECC commit date / subject | `2026-05-15 15:07:15 -0400` — "Refresh rc1 evidence for AgentShield provenance" |
| ECC LICENSE | `~/.claude/plugins/marketplaces/ecc/LICENSE` → MIT, © 2026 Affaan Mustafa |
| MoonieX local skills | `~/.claude/skills/{copywriting,copy-editing,content-strategy,marketing-ideas}/SKILL.md`, mtime 2026-05-25 (no VCS; not symlinks) |
| Excluded (not shipped) | `~/.claude/skills/{content-idea-generator,voice-extractor}/` — no LICENSE present |

---

## D. License concerns (read before publishing)

1. **content-idea-generator + voice-extractor are NOT permissively licensed and are NOT shipped.**
   Both carry a commercial author byline (brianrwagner.com / brianwagner4.gumroad.com) and ship
   **no LICENSE file**. Under the public-repo LICENSE RULE they cannot be included. The previously
   drafted §4 (idea generation) was removed in full; §5 (brand voice) is built entirely on ECC's
   MIT `brand-voice`. No text from either Brian Wagner skill remains in the shipped output.
2. **MoonieX-owned skills have no explicit license header.** copywriting / copy-editing /
   content-strategy / marketing-ideas are internal hand-written dirs — safe to publish. The repo's
   top-level `LICENSE` governs them; `NOTICE.md` records them as MoonieX-owned.
3. **ECC content is MIT — clear to ship** with the §B attribution block retained (see `NOTICE.md`).
4. **No symlinks found** for any source (all are real dirs); origin determined by byline +
   absence/presence of a LICENSE file rather than by tracing a parent repo.
