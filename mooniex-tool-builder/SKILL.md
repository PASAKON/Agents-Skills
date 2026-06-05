---
name: mooniex-tool-builder
description: >-
  Build polished, production-grade web tools — calculators, dashboards,
  widgets, and interactive mini-apps — for the MoonieX trading-tool factory.
  Use this skill when the user asks to build a web tool, calculator, dashboard,
  widget, interactive component, mini-app, or landing-tool, OR to design /
  beautify a frontend UI (component, page, layout, styling) so it looks
  production-grade instead of generic "AI slop". Combines a functional
  component-building layer (state, routing, shadcn/ui, bundling) with a
  distinctive design-system layer (typography, color, motion, spatial
  composition). Examples: "build a pip calculator", "make a margin calculator
  widget", "trading dashboard", "lot-size tool", "polish this UI", "design a
  landing-tool".
license: Apache-2.0 (derivative of anthropics/skills — see SOURCES.md & NOTICE.md)
---

# MoonieX Tool Builder

Build interactive web tools that are BOTH functionally complete AND visually
distinctive. Two layers, applied together:

- **WHAT to build** — the functional component layer: state, routing,
  shadcn/ui components, single-file bundling. *(best-of: web-artifacts-builder)*
- **HOW it looks** — the production-grade design layer: typography, color,
  motion, spatial composition, anti-"AI slop". *(best-of: frontend-design)*

This skill powers the MoonieX daily-MVP "trading-tool factory" — shipping one
polished tool per day (pip calculator, margin calculator, lot-size calculator,
position-size sizer, P/L dashboards, and similar).

---

## Design Thinking — do this BEFORE coding  *(best-of: frontend-design)*

Understand the context and commit to a BOLD, intentional aesthetic direction:

- **Purpose**: What problem does this tool solve? Who uses it? (For MoonieX:
  usually a retail FX/crypto trader who wants a fast, trustworthy answer.)
- **Tone**: Pick an extreme and commit — brutally minimal, maximalist,
  retro-futuristic, organic/natural, luxury/refined, playful/toy-like,
  editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel,
  industrial/utilitarian. Use these as inspiration; design one that is true to
  the chosen direction.
- **Constraints**: Technical requirements (framework, performance,
  accessibility). For MoonieX, see the MoonieX Integration Notes below.
- **Differentiation**: What makes this tool UNFORGETTABLE? What is the one
  thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with
precision. Bold maximalism and refined minimalism both work — the key is
intentionality, not intensity. Vary across builds: alternate light/dark
themes, fonts, and aesthetics. NEVER converge on the same common choices
(e.g. Space Grotesk) across generations — every tool should look distinct.

---

## What to Build — the functional layer  *(best-of: web-artifacts-builder)*

**Stack**: React 18 + TypeScript + Vite + Parcel (bundling) + Tailwind CSS +
shadcn/ui.

Use this stack for complex, stateful tools requiring state management, routing,
or shadcn/ui components — not for trivial single-file HTML/JSX snippets. For a
quick static widget, plain HTML/CSS/JS is fine (and the design layer below
still applies).

### Build workflow

1. **Initialize** the frontend repo using `scripts/init-artifact.sh`.
2. **Develop** the tool by editing the generated code.
3. **Bundle** all code into a single HTML file using `scripts/bundle-artifact.sh`.
4. **Display / wire up** the tool (for MoonieX, mount under `/tools/*` — see
   Integration Notes).
5. *(Optional)* **Test** the tool.

### Step 1 — Initialize Project

```bash
bash scripts/init-artifact.sh <project-name>
cd <project-name>
```

This creates a fully configured project with:
- React + TypeScript (via Vite)
- Tailwind CSS 3.4.1 with the shadcn/ui theming system
- Path aliases (`@/`) configured
- 40+ shadcn/ui components pre-installed
- All Radix UI dependencies included
- Parcel configured for bundling (via `.parcelrc`)
- Node 18+ compatibility (auto-detects and pins the Vite version)

### Step 2 — Develop Your Tool

Edit the generated files. Build the calculator/dashboard/widget logic here.
Apply the design layer (below) as you go — do not bolt styling on at the end.

### Step 3 — Bundle to a Single HTML File

```bash
bash scripts/bundle-artifact.sh
```

Produces `bundle.html` — a self-contained artifact with all JavaScript, CSS,
and dependencies inlined.

- **Requirements**: the project must have an `index.html` in the root directory.
- **What the script does**: installs bundling deps (parcel,
  `@parcel/config-default`, `parcel-resolver-tspaths`, `html-inline`); creates
  a `.parcelrc` with path-alias support; builds with Parcel (no source maps);
  inlines all assets into a single HTML file via `html-inline`.

### Step 4 — Display / Hand Off

Surface the finished tool. As a standalone artifact, share `bundle.html`. For
MoonieX, integrate the component under `/tools/*` instead (see Integration
Notes) rather than shipping a loose bundle.

### Step 5 — Testing / Visualizing (optional)

Only if necessary or requested. Use available tools (other Skills, or built-in
Playwright / Puppeteer). Avoid testing upfront — it adds latency between the
request and seeing the finished tool. Test later, after presenting it, if
requested or if issues arise.

---

## How It Looks — production-grade design  *(best-of: frontend-design)*

Implement real, working code with exceptional attention to aesthetic detail.
Match implementation complexity to the aesthetic vision: maximalist designs
need elaborate code with extensive animation and effects; minimalist/refined
designs need restraint, precision, and careful spacing and typography.

Focus on:

- **Typography**: Choose fonts that are beautiful, unique, and interesting.
  Pair a distinctive display font with a refined body font. Avoid generic
  fonts.
- **Color & Theme**: Commit to a cohesive palette. Use CSS variables for
  consistency. Dominant colors with sharp accents outperform timid, evenly
  distributed palettes.
- **Motion**: Use animation for effects and micro-interactions. Prefer
  CSS-only solutions for HTML; use the Motion library for React when available.
  Focus on high-impact moments — one well-orchestrated page load with staggered
  reveals (`animation-delay`) beats scattered micro-interactions. Use
  scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry, overlap, diagonal
  flow, grid-breaking elements. Generous negative space OR controlled density —
  pick one and commit.
- **Backgrounds & Visual Details**: Create atmosphere and depth rather than
  defaulting to solid colors. Layer contextual effects/textures that match the
  aesthetic — gradient meshes, noise textures, geometric patterns, layered
  transparencies, dramatic shadows, decorative borders, custom cursors, grain
  overlays.

The output should be production-grade and functional, visually striking and
memorable, cohesive with a clear point-of-view, and meticulously refined in
every detail.

> Claude is capable of extraordinary creative work. Don't hold back — show what
> can truly be created when committing fully to a distinctive vision.

---

## Avoid "AI Slop"  *(best-of: both — frontend-design + web-artifacts-builder)*

VERY IMPORTANT. Do **not** use generic AI-generated aesthetics:

- **Overused fonts**: Inter, Roboto, Arial, generic system fonts.
- **Clichéd color schemes**: especially purple gradients on white backgrounds.
- **Predictable layouts**: excessive centered layouts, uniform rounded corners,
  cookie-cutter component patterns.
- **Context-free design**: anything that lacks context-specific character.

Interpret creatively and make unexpected choices that feel genuinely designed
for the context. No two tools should look the same.

---

## MoonieX Integration Notes

For tools built inside the MoonieX org (these requirements are in addition to
the generic stack above):

- **Location**: tools live under `/tools/*` in the **mooniex-webapp** repo
  (Next.js + Tailwind). Build the calculator/widget as a component mounted on a
  `/tools/<tool-name>` route rather than only emitting a loose `bundle.html`.
  (The single-file bundle workflow above is for standalone artifacts; for the
  webapp, integrate the React component into the Next.js app.)
- **Analytics (required)**: every tool MUST emit the daily-MVP engine events:
  - `tool_viewed` — fire on mount / when the tool route is shown.
  - `tool_used` — fire on the primary interaction (e.g. a calculation run /
    result produced).
  Wire these to the existing MoonieX analytics layer; do not invent a new one.
- **Tailwind**: reuse the mooniex-webapp Tailwind config and design tokens; the
  design layer above guides how to differentiate each tool *within* those
  brand constraints.

---

## Sources & Updates

Merged skill — full per-feature attribution + pinned commit in `SOURCES.md`, Apache-2.0 attribution + changes notice in `NOTICE.md`. Upstream repo (check for updates):
- **web-artifacts-builder** + **frontend-design** — https://github.com/anthropics/skills (Apache-2.0, © Anthropic)

To update: diff the repo above vs the pinned commit in `SOURCES.md`, port real fixes, re-pin (MoonieX wiki `playbooks/skill-maintenance.md`).
