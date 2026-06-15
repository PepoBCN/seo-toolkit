# SEO Toolkit for Claude Code

A bundle of [Claude Code](https://claude.com/claude-code) skills and agents for doing real SEO work, technical audits, content quality, page analysis, strategy and competitor pages, straight from your terminal.

It's built around current (late-2025/2026) SEO reality: Core Web Vitals with INP, E-E-A-T, schema markup, and **GEO** (Generative Engine Optimization) for AI Overviews, ChatGPT and Perplexity, not just classic Google ranking.

## What's in the box

### Skills

| Skill | What it does |
|---|---|
| **seo** | The hub. Full site audits, single-page analysis, technical SEO, schema, content quality, GEO. Detects business type (SaaS, e-commerce, local, publisher, agency). Triggers on "SEO", "audit", "schema", "Core Web Vitals", etc. |
| **seo-audit** | Full-site audit with parallel sub-agents. Crawls up to 500 pages, detects business type, delegates to specialists, produces a health score. |
| **seo-page** | Deep single-page analysis, on-page elements, content, meta, schema, images, performance. |
| **seo-plan** | Strategic SEO planning, industry-specific templates, competitive analysis, content strategy, implementation roadmap. |
| **seo-content** | Content quality + E-E-A-T analysis, readability, thin-content detection, AI-citation readiness. |
| **seo-technical** | Technical audit across 9 categories, crawlability, indexability, security, URL structure, mobile, CWV, structured data, JS rendering, IndexNow. |
| **seo-competitor-pages** | Generates "X vs Y" comparison and "alternatives to X" pages, feature matrices, schema, conversion optimisation. |

### Agents

Specialist sub-agents the audit skill delegates to:

- **seo-technical** — crawlability, indexability, security, URL structure, mobile, CWV, JS rendering
- **seo-content** — E-E-A-T, readability, content depth, AI-citation readiness, thin content
- **seo-performance** — Core Web Vitals and page-load performance

## Install

```bash
git clone https://github.com/PepoBCN/seo-toolkit.git
cd seo-toolkit

# copy skills
cp -R skills/* ~/.claude/skills/

# copy agents
cp agents/* ~/.claude/agents/
```

Restart Claude Code so it picks up the new skills and agents.

## Use

Just ask, or use the triggers:

```
audit https://example.com
analyze this page https://example.com/pricing
build me an SEO plan for a SaaS startup
check the content quality on https://example.com/blog/post
make a "Notion vs Obsidian" comparison page
```

For a full crawl-based audit:

```
/seo-audit https://example.com
```

The toolkit detects your business type and tailors thresholds and recommendations accordingly.

## Notes

- The audit skill can crawl up to 500 pages and fans work out to parallel agents, so big sites take a few minutes.
- Performance/CWV checks read real page-load data, point them at live URLs.
- Everything runs locally through Claude Code; no SEO SaaS subscription required.

## Licence

MIT, see [LICENSE](LICENSE). Use it, fork it, share it.
