---
name: mooniex-image-gen-skill
description: >-
  Thin wrapper over the MeiGen AI Design MCP (jau123/MeiGen-AI-Design-MCP) —
  a curated 1,446-prompt gallery, prompt enhancement, and multi-model image
  generation (GPT Image 2, Nano Banana 2) for key art, posters, YT
  thumbnails, and product concept renders. Use when a C-level agent (CMO/
  CTO/CGO/CFO) needs a poster, thumbnail, key-art, or concept render and
  wants gallery/inspiration search or prompt enhancement before spending on
  actual generation. Enforces mockup-first + ask-before-paid — never calls
  generate_image / generate_video without an explicit CEO cost OK.
status: BLOCKED — plugin not installed (see Prerequisites). Skill body is
  ready to activate once installed; do not assume the MCP tools are callable
  yet.
license: N/A — wrapper only, no third-party content copied (see SOURCES.md)
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
   this in the PR/issue, don't self-approve.
3. **API key** — create a `meigen_sk_...` key at meigen.ai. Store per
   **API-key-registry (IRON §34)**, `LLMs/playbooks/api-key-registry.md` —
   add a new row + Changelog entry, value in env only, never in chat/config.
4. Confirm pricing per image/credit at meigen.ai/model-comparison before the
   first paid call, so the cost stated to the CEO (step below) is accurate.

If any of the above isn't done, tell the user this skill is not yet callable
and point at the missing step — do not simulate output.

## Tools this wraps

| Free (no key) | Paid (key + credits) |
|---|---|
| `search_gallery` — 1,446 curated prompts | `generate_image` — routes to GPT Image 2 / Nano Banana 2 |
| `enhance_prompt` | `generate_video` |
| `get_inspiration`, `list_models` | |
| `comfyui_workflow`, `manage_preferences` | |

## Workflow

1. **Search / inspire / enhance first — always $0.** Use `search_gallery`,
   `get_inspiration`, `enhance_prompt` freely to land on a strong prompt and
   composition. No confirmation needed for these.
2. **Mockup before spend.** Per wiki ADR `mockup-before-image-gen`
   (2026-06-13): produce a $0 wireframe/description of the shot and get it
   approved before any paid call — same rule as the org's existing poster
   pipeline.
3. **State cost, wait for OK.** Before the first `generate_image` /
   `generate_video` call, state the exact model, exact $/image (or $/sec for
   video) from meigen.ai/model-comparison, and the total for this batch.
   Wait for explicit CEO OK. This mirrors `ASK-before-paid-API` — bake the
   gate into the *call itself*, not just a prompt instruction (lesson from
   `feedback_lunar_brevity_enforce_in_code`: guardrails phrased as prose get
   skipped under pressure; a hard stop before the tool call doesn't).
4. **Generate**, then hand the asset to the requesting C-level flow
   (poster pipeline, thumbnail, etc.) same as any other generated image.

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

## Acceptance (from GH #24)

- C-level chat can run `search_gallery` + `enhance_prompt` ($0) and, after
  cost-OK, `generate_image` via GPT Image 2.
- Guardrails enforced: mockup-first + ask-before-paid, both as hard stops
  in this skill's workflow, not optional suggestions.
- Key lives in the registry, never in chat.
