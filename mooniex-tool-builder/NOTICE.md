# NOTICE — mooniex-tool-builder

This skill (`mooniex-tool-builder`) is a derivative work that combines and
modifies two skills from Anthropic's `anthropics/skills` repository. The
upstream material is licensed under the **Apache License, Version 2.0**. This
NOTICE preserves the upstream attribution and states the modifications made, as
required by Apache-2.0 §4(b).

## Upstream attribution

- **Upstream project**: anthropics/skills
- **Upstream URL**: https://github.com/anthropics/skills
- **Pinned commit**: `da20c92503b2e8ff1cf28ca81a0df4673debdbf7` (branch `main`)
- **License**: Apache License, Version 2.0 — http://www.apache.org/licenses/LICENSE-2.0
- **Source skills incorporated**:
  - `skills/web-artifacts-builder` (Apache-2.0, see its `LICENSE.txt`)
  - `skills/frontend-design` (Apache-2.0, see its `LICENSE.txt`)

### Upstream copyright

```
Copyright Anthropic, PBC.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Modifications (Apache-2.0 §4(b) — "carry... prominent notices stating that You changed the files")

The following changes were made to the upstream material when creating
`mooniex-tool-builder`:

1. **Merged two skills into one.** `web-artifacts-builder` and
   `frontend-design` were combined into a single skill named
   `mooniex-tool-builder`.
2. **New frontmatter.** A new `name` and unified `description`/trigger set were
   written to cover both the functional-component scope and the design scope.
   The `license` field was set to `Apache-2.0` to reflect the upstream terms.
3. **Reorganized structure.** Content was reordered into the sections
   "Design Thinking -> What to Build -> How It Looks -> Avoid AI Slop ->
   MoonieX Integration", each tagged with `(best-of: <source>)` to attribute
   which upstream skill each section derives from.
4. **Deduplicated guidance.** The two separate anti-"AI slop" lists from the
   upstream skills were merged and deduplicated into a single section.
5. **Reworded the display/bundle step** to describe MoonieX webapp integration
   instead of only sharing a standalone artifact.
6. **Added MoonieX-original content** (NOT from upstream): integration notes
   requiring tools to live under `/tools/*` in mooniex-webapp (Next.js +
   Tailwind) and to emit `tool_viewed` / `tool_used` analytics events for the
   daily-MVP engine.

## Note on the wrapper repository license

The MoonieX wrapper repository (`mooniex-claude-skills`) declares an MIT
`LICENSE` covering MoonieX-original additions. That MIT grant does **not**
relicense the upstream Apache-2.0 material incorporated here; the upstream
Apache-2.0 terms and this NOTICE continue to govern the derived portions.

## Disclaimer (carried from upstream)

The upstream skills are provided for demonstration and educational purposes.
The implementations and behaviors you receive from Claude may differ. Test
thoroughly in your own environment before relying on this skill for critical
tasks.
