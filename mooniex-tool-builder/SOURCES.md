# SOURCES — mooniex-tool-builder

`mooniex-tool-builder` is a derivative work merging the best of two skills from
Anthropic's official `anthropics/skills` monorepo.

## License correction (IMPORTANT)

The original task brief stated the repo is **MIT**. That is **incorrect**.
Verified from the actual source on 2026-06-05:

- Both source skills ship their own `LICENSE.txt` = **Apache License 2.0**.
- The repo README states verbatim: *"Many skills in this repo are open source
  (Apache 2.0)."*
- GitHub's auto license-detection API returns `null`/`null` **only** because
  there is no top-level `LICENSE` file — the license lives per-skill, so the
  detector misses it. The files themselves are unambiguously Apache-2.0.

Apache-2.0 permits this merge/derivative provided we (a) retain attribution and
(b) state that changes were made. `NOTICE.md` in this folder satisfies both.

> Note: the MoonieX wrapper repo (`mooniex-claude-skills`) carries its own MIT
> `LICENSE` for MoonieX-original additions. That does not relicense the
> upstream Apache-2.0 material — upstream terms are preserved in `NOTICE.md`.

## Pinned source

| Field | Value |
|---|---|
| Repo | `anthropics/skills` |
| Branch | `main` |
| Pinned commit SHA | `da20c92503b2e8ff1cf28ca81a0df4673debdbf7` |
| Fetched | 2026-06-05 |
| License (effective) | **Apache-2.0** (per-skill `LICENSE.txt` + README) |

## Credited sources

| Source skill | Repo | License | URL (pinned) |
|---|---|---|---|
| web-artifacts-builder | anthropics/skills | Apache-2.0 | https://github.com/anthropics/skills/tree/da20c92503b2e8ff1cf28ca81a0df4673debdbf7/skills/web-artifacts-builder |
| frontend-design | anthropics/skills | Apache-2.0 | https://github.com/anthropics/skills/tree/da20c92503b2e8ff1cf28ca81a0df4673debdbf7/skills/frontend-design |

## Per-feature attribution

| Feature | Source | GitHub URL | License | Taken / Dropped + why |
|---|---|---|---|---|
| 5-step build workflow (init -> develop -> bundle -> display -> test) | web-artifacts-builder | .../web-artifacts-builder/SKILL.md | Apache-2.0 | **Taken** — core "what to build" loop; step 4 reworded "display artifact" -> "display / hand off + MoonieX `/tools/*` integration". |
| Stack: React 18 + TS + Vite + Parcel + Tailwind + shadcn/ui | web-artifacts-builder | .../web-artifacts-builder/SKILL.md | Apache-2.0 | **Taken** verbatim — defines the functional component layer. |
| `scripts/init-artifact.sh` behavior (40+ shadcn components, `@/` aliases, Tailwind 3.4.1, Node 18 pin) | web-artifacts-builder | .../web-artifacts-builder/scripts/init-artifact.sh | Apache-2.0 | **Taken** (described) — scripts themselves NOT copied here (research/draft only); referenced by path. To actually run, copy `scripts/` from source. |
| `scripts/bundle-artifact.sh` single-file HTML bundling (parcel + html-inline) | web-artifacts-builder | .../web-artifacts-builder/scripts/bundle-artifact.sh | Apache-2.0 | **Taken** (described) — same caveat: script not bundled into this draft. |
| `scripts/shadcn-components.tar.gz` (pre-packed components) | web-artifacts-builder | .../web-artifacts-builder/scripts/ | Apache-2.0 | **Noted, dropped from draft** — binary asset; would be copied alongside scripts at install time, not in this markdown draft. |
| "Avoid AI slop": no centered layouts / purple gradients / uniform rounded corners / Inter | web-artifacts-builder | .../web-artifacts-builder/SKILL.md | Apache-2.0 | **Taken + merged** with frontend-design's larger anti-slop list (deduped into one "Avoid AI Slop" section). |
| shadcn/ui components reference link | web-artifacts-builder | .../web-artifacts-builder/SKILL.md | Apache-2.0 | **Dropped from body** — implied by stack; omitted to keep the merged skill lean (re-add if needed). |
| Design Thinking pre-step (Purpose / Tone / Constraints / Differentiation) | frontend-design | .../frontend-design/SKILL.md | Apache-2.0 | **Taken** verbatim — the "before coding, commit to a bold direction" gate; adapted Constraints to point at MoonieX notes. |
| Frontend Aesthetics: Typography / Color & Theme / Motion / Spatial Composition / Backgrounds & Visual Details | frontend-design | .../frontend-design/SKILL.md | Apache-2.0 | **Taken** verbatim — the entire "how it looks" production-grade layer. |
| "Match implementation complexity to aesthetic vision" + "Don't hold back" closing | frontend-design | .../frontend-design/SKILL.md | Apache-2.0 | **Taken** — calibration guidance + motivational close. |
| Full anti-slop list (Inter/Roboto/Arial/system, purple-on-white, predictable layouts, cookie-cutter) | frontend-design | .../frontend-design/SKILL.md | Apache-2.0 | **Taken** — became the spine of the unified "Avoid AI Slop" section (deduped with web-artifacts-builder's shorter list). |
| "Vary across generations / never converge on Space Grotesk" | frontend-design | .../frontend-design/SKILL.md | Apache-2.0 | **Taken** — folded into Design Thinking to enforce per-tool variety in the daily factory. |
| MoonieX `/tools/*` location + Next.js/Tailwind + `tool_viewed`/`tool_used` analytics | MoonieX (original, not from sources) | n/a | n/a | **Added** — org-specific integration glue per the daily-MVP engine; clearly marked as original, not derived. |

## Changes made (Apache-2.0 §4(b) summary — full notice in NOTICE.md)

This work is a modified combination of `web-artifacts-builder` and
`frontend-design` from `anthropics/skills` @ `da20c925`. Changes:
1. Merged two skills into one (`mooniex-tool-builder`).
2. New unified `description`/triggers covering both scopes.
3. Reorganized into "Design Thinking -> What to Build -> How It Looks -> Avoid
   AI Slop -> MoonieX Integration" with `(best-of: <source>)` dedupe tags.
4. Deduplicated the two anti-"AI slop" lists into a single section.
5. Added MoonieX-specific, original integration notes (`/tools/*`, analytics).
6. Reworded the bundle/display step for webapp integration.
Source scripts (`init-artifact.sh`, `bundle-artifact.sh`,
`shadcn-components.tar.gz`) are referenced by path but not reproduced in this
draft.
