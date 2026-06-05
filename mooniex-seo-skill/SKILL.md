---
name: mooniex-seo-skill
description: >-
  One unified SEO skill for the MoonieX org. Audit, plan, and implement search
  optimization end to end — technical SEO, crawlability and indexation, on-page
  optimization, Schema.org structured data, Core Web Vitals, sitemaps and
  robots, content quality and E-E-A-T, keyword mapping, internal linking,
  programmatic (template-at-scale) SEO, and AI-search / GEO optimization.
  Use this when the user wants better search visibility or mentions: "SEO",
  "SEO audit", "site audit", "technical SEO", "crawlability", "indexation",
  "schema markup", "structured data", "JSON-LD", "rich results", "meta tags",
  "title tags", "meta descriptions", "heading structure", "Core Web Vitals",
  "LCP / INP / CLS", "page speed for SEO", "sitemap", "robots.txt", "canonical",
  "hreflang", "internal linking", "keyword mapping", "keyword cannibalization",
  "content SEO", "E-E-A-T", "programmatic SEO", "pSEO", "template pages",
  "pages at scale", "location pages", "comparison pages", "AI Overviews",
  "GEO", "generative engine optimization", or "AEO". This is the single SEO
  skill — prefer it over any other SEO skill for all of the above.
  (NOT for general conversion-rate / homepage CRO work — that is homepage-audit.)
---

# MoonieX SEO Skill

The org's single source of truth for SEO work. Merges the best of three upstream
SEO skills (see `SOURCES.md` for full per-feature attribution). Improve search
visibility through technical correctness, performance, structured data, and
content relevance — never gimmicks.

## When to Use

- Auditing a site or page for crawlability, indexability, canonicals, redirects
- Reviewing or writing title tags, meta descriptions, and heading structure
- Adding, validating, or fixing structured data (JSON-LD)
- Diagnosing or improving Core Web Vitals
- Keyword research and mapping keywords to URLs (and catching cannibalization)
- Planning internal linking, sitemaps, or robots changes
- Building SEO pages at scale from templates + data (programmatic SEO)
- Optimizing for AI Overviews / generative-engine results (GEO / AEO)

For conversion-rate optimization of a marketing page, use `homepage-audit` /
`page-cro` instead — that is a different domain.

## Operating Principles

1. Fix technical blockers before content optimization (best-of: ecc:seo).
2. One page = one clear primary search intent.
3. Prefer long-term quality signals over manipulative patterns.
4. Mobile-first: indexing is mobile-first, so assume mobile first.
5. Every recommendation must be page-specific, file-specific, and implementable
   — read the real page/source before advising (best-of: seo-specialist agent).
6. Match schema to reality: never mark up content that is not actually present.

---

## 1. Technical SEO Audit

Audit across these categories (best-of: claude-seo `seo-technical`, the most
complete checklist of the three; ecc:seo principles folded in).

### Crawlability
- `robots.txt` exists, is valid, and does not block important resources
- XML sitemap exists and is referenced in `robots.txt`
- `noindex` tags are intentional, never accidental
- Important pages reachable within ~3 clicks of the homepage
- Critical content does not require JavaScript to be seen by crawlers
- Crawl budget managed efficiently on large sites
- AI-crawler rules configured deliberately (GPTBot, ClaudeBot, Google-Extended)

### Indexability
- Canonical tags self-reference and never loop or conflict
- No `noindex` + `canonical` conflicts
- Duplicate / near-duplicate content identified and resolved
- Thin content flagged
- Pagination uses a coherent pattern (rel next/prev or load-more)
- `hreflang` correct for multi-language/region sites
- Index bloat minimized; preferred URL format consistent

### Security (SEO-relevant)
- HTTPS enforced with a valid certificate; no mixed content
- HSTS present; security headers (CSP, X-Content-Type-Options, Referrer-Policy)
  configured where applicable

### URL Structure
- Clean, descriptive, hyphenated URLs; logical folder hierarchy
- Redirects single-hop where possible; **never chains longer than two hops**
- Permanent moves use 301; trailing-slash usage consistent

### Mobile
- Responsive design with a `viewport` meta tag, no horizontal scroll
- Touch targets ~48x48px, base font ~16px, mobile-first compliance

### JavaScript Rendering
- Identify CSR vs SSR; confirm canonical and `noindex` match between raw HTML
  and rendered output
- Time-sensitive structured data must live in server-rendered HTML

### Modern signals
- IndexNow support (Bing, Yandex, Naver) where relevant
- Speculation Rules / bfcache eligibility for navigation speed
- Agent-friendly markup: semantic `<button>` / `<a>`, clean accessibility tree

### Severity model (best-of: seo-specialist agent)
- **Critical:** crawl/index blockers, robots/meta-robots conflicts, canonical
  loops, redirect chains >2 hops, broken internal links on key paths
- **High:** missing/duplicate titles or descriptions, invalid heading hierarchy,
  malformed/missing JSON-LD on key page types, CWV regressions on key pages
- **Medium:** thin content, missing alt text, weak anchors, orphan pages,
  keyword cannibalization

---

## 2. On-Page Optimization

(best-of: ecc:seo — cleanest concrete thresholds and formulas.)

### Title tags
- ~50–60 characters; primary keyword/concept near the front; human-legible

### Meta descriptions
- ~120–160 characters; honest description; main topic included naturally

### Heading structure
- Exactly one clear `H1`; `H2` / `H3` reflect real content hierarchy, not styling

### Formulas
```text
Title:  Primary Topic - Specific Modifier | Brand
Meta:   Action + topic + value proposition + one supporting detail
```

### Images
- Descriptive `alt` text; appropriately sized/compressed; explicit dimensions to
  protect CLS (overlaps with Core Web Vitals below)

---

## 3. Schema / Structured Data

(best-of: claude-seo `seo-schema` — only source with current deprecation /
restriction rules; ecc:seo per-page-type mapping retained as the quick guide.)

### Format & validation
- Prefer **JSON-LD** (`<script type="application/ld+json">`) over Microdata/RDFa
- Validate: valid `@context` + `@type`; correct property data types; absolute
  URLs (not relative); ISO-8601 dates; no placeholder text in live data;
  compatible with Google's supported rich-result types

### Per-page-type quick map (best-of: ecc:seo)
| Page type | Schema |
|-----------|--------|
| Homepage / company | `Organization` or `LocalBusiness` |
| Editorial / blog | `Article` / `BlogPosting` / `NewsArticle` |
| Product | `Product` + `Offer` (+ `ProductGroup` for variants) |
| Any interior page | `BreadcrumbList` |
| Profile / person | `Person` / `ProfilePage` |
| Video | `VideoObject` |

### Type status (best-of: claude-seo — must be kept current)
- **Active (use freely):** Organization, LocalBusiness, SoftwareApplication,
  Product, ProductGroup, Offer, Service, Article, BlogPosting, NewsArticle,
  Review, AggregateRating, BreadcrumbList, WebSite, WebPage, Person,
  ProfilePage, ContactPage, VideoObject, ImageObject, Event, JobPosting,
  Course, DiscussionForumPosting
- **Restricted:** `FAQPage` — only for government / healthcare-authority sites
  (restricted Aug 2023); otherwise do not use
- **Deprecated (never recommend):** HowTo, SpecialAnnouncement, ClaimReview,
  VehicleListing, EstimatedSalary, LearningVideo, CourseInfo carousel, and other
  retired types
- Time-sensitive markup (Product, Offer) must be in server-rendered HTML

### Example JSON-LD
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Page Title Here",
  "author":    { "@type": "Person",       "name": "Author Name" },
  "publisher": { "@type": "Organization", "name": "Brand Name"  }
}
```

---

## 4. Core Web Vitals

(best-of: claude-seo + ecc:seo — identical thresholds; claude-seo adds field/lab
nuance.)

- **LCP** < 2.5s · **INP** < 200ms · **CLS** < 0.1
- INP replaced FID (2024); do not optimize for FID anymore
- Prefer **field data** (CrUX, 75th percentile real users) and fall back to lab
  data (Lighthouse / PageSpeed Insights); measure mobile and desktop separately
- Common fixes: preload hero/LCP asset, cut render-blocking JS/CSS, reserve
  layout space (width/height) to prevent CLS, trim heavy JS, lazy-load
  below-the-fold

---

## 5. Sitemaps & Robots

(best-of: claude-seo `seo-sitemap` + ecc:seo.)

- XML sitemap reflects only the intended public surface (no noindex/redirect URLs)
- Split sitemaps by page type for large sites; keep them in sync with robots
- `robots.txt`: allow important pages, block low-value surfaces, reference the
  sitemap, set AI-crawler rules deliberately
- Submit/refresh via the appropriate webmaster channel; use IndexNow where supported

---

## 6. Content SEO, Keyword Mapping & Internal Linking

### Keyword mapping (best-of: ecc:seo — tightest procedure)
1. Define the search intent
2. Gather realistic keyword variants
3. Prioritize by intent match, likely value, and competition
4. Map one primary keyword/theme to one URL
5. Detect and avoid cannibalization

### Content quality / E-E-A-T (best-of: claude-seo `seo-content`)
Evaluate against the Search Quality Rater Guidelines (Who/How/Why heuristic):
- **Experience** — original research, case studies, first-hand material
- **Expertise** — author credentials, topical depth
- **Authoritativeness** — external citations, brand mentions
- **Trustworthiness** — contact info, HTTPS, transparent corrections, date stamps

### Internal linking (best-of: ecc:seo + programmatic-seo hub-and-spoke)
- Link from strong pages to pages you want to rank, with descriptive anchors
- Avoid generic anchors when a specific one exists
- Hub-and-spoke: hub category page → individual pages → cross-links between
  related pages; no orphan pages; breadcrumbs with structured data

---

## 7. Programmatic SEO (Pages at Scale)

(best-of: programmatic-seo — the only source covering template-at-scale; full
playbooks live in `references/playbooks.md`.)

### Core rules
- **Unique value per page** — not just swapped template variables
- **Proprietary data wins** (defensibility): proprietary > product-derived >
  user-generated > licensed > public
- **Subfolders, not subdomains** (`site.com/templates/` beats
  `templates.site.com/`) — consolidates authority
- Genuine search-intent match; quality over quantity; avoid doorway pages,
  keyword stuffing, duplicate content
- Multi-location guardrail: warn at ~30 templated pages, hard-stop near ~50
  without unique data (best-of: claude-seo `seo-local`) to avoid doorway-page
  penalties

### The 12 playbooks (pattern → example)
Templates (`[type] template`), Curation (`best [category]`), Conversions
(`[X] to [Y]`), Comparisons (`[X] vs [Y]`), Examples (`[type] examples`),
Locations (`[service] in [city]`), Personas (`[product] for [audience]`),
Integrations (`[A] [B] integration`), Glossary (`what is [term]`), Translations
(localized), Directory (`[category] tools`), Profiles (`[entity name]`).
Layerable, e.g. "best coworking spaces in San Diego" (Curation + Locations).

### Build framework
1. **Keyword-pattern research** — find the repeating structure + variables;
   validate aggregate volume and trend
2. **Data requirements** — source, freshness, first-party vs public
3. **Template design** — keyword header, unique intro, data-driven sections,
   related-page links, intent-appropriate CTA
4. **Internal-linking architecture** — hub-and-spoke, no orphans, XML sitemap
5. **Indexation strategy** — prioritize high-volume patterns, `noindex` very
   thin variants, manage crawl budget, separate sitemaps by type

### Pre-launch checklist
- [ ] Each page provides unique value and answers intent
- [ ] Unique titles + meta descriptions, proper headings, schema present
- [ ] Connected to site architecture, related pages linked, no orphans
- [ ] In XML sitemap, crawlable, no conflicting `noindex`
- [ ] Page speed acceptable

### Post-launch monitoring
Track indexation rate, rankings, traffic, engagement, conversion. Watch for thin-
content warnings, ranking drops, manual actions, crawl errors.

---

## 8. AI Search / GEO (Generative Engine Optimization)

(best-of: claude-seo `seo-geo` — the only source covering AI-search.)

- **Passage citability** — self-contained answer blocks (~134–167 words) that an
  AI engine can lift directly
- **Question-based heading hierarchy** — headings phrased as the queries users ask
- **Attribution density** — clear sourcing and entity references
- **Entity presence** — coverage across Wikipedia, Reddit, YouTube, LinkedIn
- Prerequisite: the page must be indexed and snippet-eligible to appear in any AI
  feature
- Ignore the myths: no `llms.txt` magic, no AI-specific keyword rewrites,
  no content-chunking tricks

---

## Output Formats

### Audit finding (best-of: ecc:seo / seo-specialist agent)
```text
[SEVERITY] Issue title
Location: path/to/file.tsx:42 or https://url
Issue: What is wrong and why it matters for ranking/indexing.
Fix: The exact change to make.
```

### Programmatic-SEO deliverable
- **Strategy doc:** opportunity analysis, implementation plan, content guidelines
- **Page template:** URL structure, title/meta templates, content outline, schema

---

## Anti-Patterns

| Anti-pattern | Fix |
|---|---|
| Keyword stuffing | Write for users first |
| Thin near-duplicate pages | Consolidate or differentiate them |
| Schema for content not on the page | Match schema to reality |
| Advice without reading the real page/source | Read it first |
| Generic "improve SEO" output | Tie every recommendation to a page/asset |
| Doorway pages at scale | Require unique data per page; respect the 30/50 guardrail |
| Using deprecated schema (HowTo, ClaimReview, etc.) | Use only active types |
| Optimizing for FID | Use INP |

## Related Skills
- `homepage-audit` / `page-cro` — conversion optimization (different domain)
- `content-strategy`, `competitor-analysis`

---

## Sources & Updates

Merged skill — full per-feature attribution + pinned commits in `SOURCES.md`, license texts in `NOTICE.md`. Upstream repos (check these for updates):
- **claude-seo** — https://github.com/AgriciDaniel/claude-seo (MIT)
- **ecc / seo + seo-specialist** — https://github.com/affaan-m/everything-claude-code (MIT, © Affaan Mustafa)
- **programmatic-seo** — https://github.com/coreyhaines31/marketingskills (MIT, © Corey Haines)

To update: diff the repos above vs the pinned commits in `SOURCES.md`, port real fixes, re-pin (MoonieX wiki `playbooks/skill-maintenance.md`).
