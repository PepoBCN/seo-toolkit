---
name: seo
description: >
  SEO analysis for any website. Full site audits, single-page analysis, technical SEO
  (crawlability, indexability, Core Web Vitals with INP), schema markup, content quality
  (E-E-A-T per Dec 2025 update), and Generative Engine Optimization (GEO) for AI
  Overviews, ChatGPT, and Perplexity. Industry detection for SaaS, e-commerce, local
  business, publishers, agencies. Triggers on: "SEO", "audit", "schema", "Core Web Vitals",
  "technical SEO", "content quality", "page speed", "structured data", "E-E-A-T".
---

# SEO — Universal SEO Analysis Skill

SEO analysis across all industries. Orchestrates 6 core sub-skills and 3 subagents.

## Commands

| Command | What it does |
|---------|-------------|
| `/seo audit <url>` | Full website audit with parallel subagent delegation |
| `/seo page <url>` | Deep single-page analysis |
| `/seo technical <url>` | Technical SEO audit (crawlability, indexability, security, CWV, schema, hreflang, images) |
| `/seo content <url>` | E-E-A-T and content quality analysis |
| `/seo plan <business-type>` | Strategic SEO planning |
| `/seo competitor-pages [url\|generate]` | Competitor comparison page generation |

## Orchestration — `/seo audit`

1. Detect business type (SaaS, local, ecommerce, publisher, agency, other)
2. Spawn subagents: seo-technical, seo-content, seo-performance
3. Collect results and generate unified report with SEO Health Score (0-100)
4. Create prioritised action plan (Critical > High > Medium > Low)

For individual commands, load the relevant sub-skill directly.

## Industry Detection

Detect business type from homepage signals:
- **SaaS**: pricing page, /features, /integrations, /docs, "free trial", "sign up"
- **Local Service**: phone number, address, service area, "serving [city]", Google Maps embed
- **E-commerce**: /products, /collections, /cart, "add to cart", product schema
- **Publisher**: /blog, /articles, /topics, article schema, author pages, publication dates
- **Agency**: /case-studies, /portfolio, /industries, "our work", client logos

## Quality Gates

Read `references/quality-gates.md` for thin content thresholds per page type.
Hard rules:
- WARNING at 30+ location pages (enforce 60%+ unique content)
- HARD STOP at 50+ location pages (require user justification)
- Never recommend HowTo schema (deprecated Sept 2023)
- FAQ schema only for government and healthcare sites
- All Core Web Vitals references use INP, never FID

## Reference Files

Load on-demand as needed — do NOT load all at startup:
- `references/cwv-thresholds.md` — Current Core Web Vitals thresholds
- `references/schema-types.md` — Supported schema types with deprecation status
- `references/eeat-framework.md` — E-E-A-T evaluation criteria (Sept 2025 QRG update)
- `references/quality-gates.md` — Content length minimums, uniqueness thresholds

## SEO Health Score (0-100)

| Category | Weight |
|----------|--------|
| Technical SEO | 25% |
| Content Quality | 25% |
| On-Page SEO | 20% |
| Schema / Structured Data | 10% |
| Performance (CWV) | 10% |
| Images & Media | 5% |
| AI Search Readiness | 5% |

## Priority Levels
- **Critical**: Blocks indexing or causes penalties (immediate fix)
- **High**: Significantly impacts rankings (fix within 1 week)
- **Medium**: Optimisation opportunity (fix within 1 month)
- **Low**: Nice to have (backlog)

## Subagents

For parallel analysis during audits:
- `seo-technical` — Crawlability, indexability, security, CWV, schema, hreflang, images
- `seo-content` — E-E-A-T, readability, thin content, AI citation readiness
- `seo-performance` — Core Web Vitals measurement
