---
name: mooniex-image-gen
owner: CMO
origin: mooniex-org
scope: >-
  FREE MeiGen MCP tools only — gallery search, inspiration, prompt enhancement.
  It does NOT generate the final asset: no MeiGen API key exists or is wanted, so
  the finished prompt is handed to the org's Fal.ai pipeline under the
  ask-before-paid rule (CEO decision 2026-07-13). Requires the meigen plugin
  installed and /meigen:setup run.
description: Gallery search and prompt enhancement via the MeiGen MCP — free tools only. Trigger on /mooniex-image-gen when writing an image prompt for key art, posters, or thumbnails. Does NOT generate the image — no MeiGen key exists, so the finished prompt goes to the org's Fal.ai pipeline under ask-before-paid rules.
---

# MoonieX Image-Gen Skill (MeiGen MCP wrapper)

Origin: GH `mooniex-agents#22` idea note → `mooniex-agents#24` (surfaced doing
the Minecraft "Frost Knight" thumbnail, CEO 2026-06-21).

## Prerequisites (CEO/host action — NOT done yet)

This skill wraps a Claude Code **plugin-level MCP**, which this skill file
alone cannot install or call. Before any tool call in this skill works:

1. **Install** (CEO, needs a Claude Code restart):
   `/plugin marketplace add jau123/MeiGen-AI-Design-MCP` →
   `/plugin install meigen@meigen-marketplace` → restart → `/meigen:setup`
2. **Supply-chain review** — `jau123/MeiGen-AI-Design-MCP` is a third-party,
   unverified publisher. Not yet reviewed. Get an explicit CEO/CTO OK before
   connecting it to org sessions that also hold other credentials — flag
   this in the PR/issue, don't self-approve. (Lower stakes than originally
   scoped since no MeiGen credential ever passes through it — see below.)

**No MeiGen API key needed** (CEO decision 2026-07-13): this skill only ever
calls MeiGen's free tools. Actual generation reuses the org's existing
`FAL_API_KEY` (already in the registry) via the standard Fal.ai pipeline —
do not create a `meigen_sk_...` key.

If step 1 isn't done, tell the user this skill is not yet callable and point
at the missing install step — do not simulate output.

## Tools this wraps

Free tools only — this is the entire scope of this skill:

| Tool | Use |
|---|---|
| `search_gallery` | search the 1,446 curated prompts |
| `enhance_prompt` | sharpen a rough prompt into a stronger one |
| `get_inspiration` | browse for composition/style ideas |
| `list_models` | see what MeiGen's own gallery supports (reference only) |
| `comfyui_workflow` | inspect workflow graphs, if useful for reference |
| `manage_preferences` | set gallery search preferences |

`generate_image` / `generate_video` (MeiGen's own paid, key-gated routing)
are explicitly **out of scope** — never call them. Generation happens via
Fal.ai instead (see Workflow).

## Workflow

1. **Search / inspire / enhance — always $0.** Use `search_gallery`,
   `get_inspiration`, `enhance_prompt` freely to land on a strong prompt and
   composition.
2. **Hand the finished prompt to the existing Fal.ai pipeline** (`FAL_API_KEY`,
   `ecc:fal-ai-media` skill / `scripts/mooniex_poster.py` / `gen-rebate-scenes.py`
   as applicable) for the actual render. This skill never generates images
   itself.
3. **Mockup-first + ask-before-paid still apply** to that Fal.ai call, same
   as every other org image-gen path (wiki ADR `mockup-before-image-gen`,
   `ASK-before-paid-API`) — this skill doesn't change or bypass those, it
   just feeds them a better prompt.

## Reconciliation vs existing org image scripts

MeiGen **complements**, does not replace, the org's bespoke generators:

- `scripts/mooniex_poster.py`, `gen-rebate-scenes.py`, `spcx_*` — these bake
  MoonieX brand lockup (moon+pagoda, navy/gold, glossy 3D numbers) and
  composite crisp overlay text in a second pass. That brand-specific
  compositing logic is NOT something MeiGen does — keep these scripts as
  the final-render path for on-brand MoonieX posters.
- MeiGen's value-add is **upstream of that**: gallery search / inspiration /
  prompt enhancement to find the base scene composition faster, and as a
  general-purpose generator for non-MoonieX-branded work (e.g. the
  Minecraft "Frost Knight" thumbnail that surfaced this idea, or one-off
  concept renders that don't need the brand lockup).
- Rule of thumb: brand-locked MoonieX creative → existing `scripts/*`
  pipeline. Exploratory / non-brand / gallery-driven work → this skill.

## Surfacing to C-level spawn configs

Once installed and reviewed, add this skill's routing line to each
C-level's skill preferences (CTO/CMO/CGO/CFO spawn configs / CLAUDE.md) so
`search_gallery` / `enhance_prompt` are reachable from any of those chats.
Not done yet — do this as part of activation, after Prerequisites are clear.

## Acceptance (from GH #24, scoped down 2026-07-13)

- C-level chat can run `search_gallery` + `enhance_prompt` ($0), then hand
  the result to the existing Fal.ai pipeline for the actual render.
- `generate_image` / `generate_video` (MeiGen's own paid routing) are never
  called — no MeiGen key exists in this org.
- Mockup-first + ask-before-paid still enforced on the Fal.ai call, same as
  every other org image-gen path — this skill doesn't touch that gate.
