# SEO Toolkit for Claude Code

Seven skills and three agents that turn Claude Code into an SEO analyst. Full site audits, single page reviews, technical checks, content quality, strategy and competitor pages, all from your terminal, no SEO SaaS subscription required.

## Why this exists

Most SEO tooling is a dashboard you log into once a month. This is the opposite: point Claude Code at a URL and it crawls, checks and reasons about the site there and then, in the same session you're already working in. No separate login, no export-to-spreadsheet step, no waiting for a scheduled crawl.

It's built for how SEO actually works now, not five years ago: Core Web Vitals with INP, E-E-A-T signals, schema markup, and GEO (Generative Engine Optimization) for how sites show up in AI Overviews, ChatGPT and Perplexity, not just classic Google ranking.

## Who it's for

Anyone running Claude Code who wants SEO answers without switching tools: consultants doing client audits, founders checking their own site, developers who inherited "also do the SEO" as a job. You don't need to know SEO jargon going in, the skills explain findings in plain language and prioritise what to fix first.

## What's in the box

### Skills

| Skill | What it does |
|---|---|
| **seo** | The hub. Full site audits, single-page analysis, technical SEO, schema, content quality, GEO. Detects business type (SaaS, e-commerce, local, publisher, agency). Triggers on "SEO", "audit", "schema", "Core Web Vitals", etc. |
| **seo-audit** | Full-site audit with parallel sub-agents. Crawls up to 500 pages, detects business type, delegates to specialists, produces a health score. |
| **seo-page** | Deep single-page analysis: on-page elements, content, meta tags, schema, images, performance. |
| **seo-plan** | Strategic SEO planning: industry-specific templates, competitive analysis, content strategy, implementation roadmap. |
| **seo-content** | Content quality and E-E-A-T analysis, readability, thin-content detection, AI-citation readiness. |
| **seo-technical** | Technical audit across 9 categories: crawlability, indexability, security, URL structure, mobile, CWV, structured data, JS rendering, IndexNow. |
| **seo-competitor-pages** | Generates "X vs Y" comparison and "alternatives to X" pages, feature matrices, schema, conversion optimisation. |

### Agents

Specialist sub-agents the audit skill delegates to for parallel work:

- **seo-technical**: crawlability, indexability, security, URL structure, mobile, CWV, JS rendering
- **seo-content**: E-E-A-T, readability, content depth, AI-citation readiness, thin content
- **seo-performance**: Core Web Vitals and page-load performance

## How it works

Each skill is a self-contained instruction set (a `SKILL.md` file plus reference material) that Claude Code loads when your request matches its triggers. The **seo** skill is the general entry point and routes to the others depending on what you ask for. **seo-audit** goes further: it crawls the site itself, works out what kind of business it is, then fans the work out to the three specialist agents in parallel so a large site doesn't take forever. Everything runs as part of your normal Claude Code session, there's no separate service to sign into.

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

Just ask, in plain language, or use one of these as a starting point:

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

### Walkthrough

A typical run looks like this. You say:

```
audit https://example.com and tell me the three things to fix first
```

Claude Code picks up the **seo** skill, detects the site's business type, and either runs a lightweight check itself or hands off to **seo-audit** for a full crawl. If it crawls, work fans out to the **seo-technical**, **seo-content** and **seo-performance** agents at the same time, each reporting back on its slice. You get a single health score plus a prioritised list, not three disconnected reports to reconcile yourself.

The toolkit adapts its thresholds and recommendations to the business type it detects, an e-commerce site and a SaaS blog get different advice, not one generic checklist.

## Notes

- The audit skill can crawl up to 500 pages and fans work out to parallel agents, so big sites take a few minutes.
- Performance and CWV checks read real page-load data, point them at live URLs.
- Everything runs locally through Claude Code.

## Honesty note

This toolkit reports what it measures. It does not fabricate rankings, traffic numbers or before/after results, and it won't promise a specific ranking outcome. Treat its output as a structured second opinion, not a guarantee.

## Licence

MIT, see [LICENSE](LICENSE). Use it, fork it, share it.
