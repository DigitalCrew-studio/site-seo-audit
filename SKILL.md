---
name: seo-auditing
description: Conducts evidence-based SEO audits for public websites and web applications. Use when the user asks to check SEO, indexability, robots.txt, sitemap.xml, canonical URLs, metadata, HTML semantics, JavaScript rendering, structured data, Core Web Vitals, mobile-first readiness, regional search engines, migration risks, social previews, private/account-page indexation, or to produce an SEO audit report/roadmap.
---

# SEO Auditing

## Core rule

Perform an evidence-based SEO audit. Do not claim that a defect exists unless it was directly checked or the limitation is clearly stated.

Every finding must use this structure:

```md
### [P0/P1/P2/P3] <issue title>
- Area: <technical/indexability/content/rendering/schema/performance/regional/etc.>
- Affected URL(s) or template(s): <URL list, pattern, or template name>
- Observation: <what was verified>
- Evidence: <URL, command output, HTML snippet, tool result, screenshot, or stated limitation>
- Risk: <why it matters for crawl/index/ranking/UX>
- Recommendation: <specific fix>
- Owner: <SEO/Frontend/Backend/DevOps/Content/Analytics/Unknown>
- Verification: <how to confirm the fix>
```

If a previous third-party SEO audit is provided, do not copy its conclusions blindly. Extract reusable audit patterns, validate them against current search-engine documentation, keep site-specific findings separate, and merge only checks that are evidence-based and repeatable.

Never guarantee rankings, traffic growth, rich results, or indexing.

## Trigger contexts

Use this skill for:

- Full SEO audit of a website or web app.
- Pre-launch SEO check.
- Post-migration SEO check.
- Debugging indexing, crawlability, canonical, sitemap, robots, metadata, JavaScript rendering, schema, performance, or mobile issues.
- Creating a prioritized SEO roadmap.
- Regional SEO checks for Google, Yandex, Bing/Yahoo, Naver, Baidu, or Seznam.
- Reviewing a previous SEO audit and converting useful patterns into a reusable audit skill or checklist.

Do not use this skill for black-hat SEO, spam, cloaking, hidden text, doorway pages, fake reviews, traffic/ranking guarantees, or bulk low-value programmatic pages.

## Minimum input

If only a domain is provided, run a public audit and state that private tools were unavailable.

Prefer to collect:

- Primary domain and protocol: `https://example.com`.
- Target countries/languages/search engines.
- Site type: landing, corporate, SaaS, ecommerce, blog, marketplace, docs, catalog.
- Important URLs or templates: homepage, service page, product/category, article, case, contact.
- Migration context if applicable: old URLs, new URLs, launch date.
- Private data if available: Search Console, Yandex Webmaster, Bing Webmaster, analytics, server logs, crawl export.

## Reference loading map

Read only the reference files needed for the task. Keep the main workflow lean.

| Need | Read |
|---|---|
| Audit sequence and sampling | `references/01-audit-workflow.md` |
| robots, sitemap, status codes, canonical, redirects, noindex | `references/02-technical-indexability.md` |
| metadata, headings, semantic HTML, content, internal links, images | `references/03-html-content-semantics.md` |
| React/Vue/SPA/SSR, rendered HTML, lazy loading, JS links | `references/04-javascript-rendering.md` |
| JSON-LD, Schema.org, rich-result validation | `references/05-structured-data.md` |
| Core Web Vitals, mobile-first, images, fonts, caching | `references/06-performance-mobile.md` |
| hreflang and regional engines: Google, Yandex, Bing, Naver, Baidu, Seznam | `references/07-international-regional.md` |
| Scoring, priorities, report template, roadmap | `references/08-reporting-scoring.md` |
| CLI commands and repeatable checks | `references/09-cli-checks.md` |
| Source list for updating facts | `references/10-source-corpus.md` |
| Extracting reusable checks from a third-party audit | `references/11-third-party-audit-patterns.md` |
| Legacy domains, old URLs, post-migration redirects | `references/12-migration-legacy-url-audit.md` |
| Schema by page type and eligibility rules | `references/13-page-type-schema-matrix.md` |
| Open Graph, Twitter/X Cards, link previews | `references/14-social-preview-audit.md` |
| Login, account, checkout, admin and private page indexation | `references/15-private-account-indexing.md` |
| Why this skill is split this way | `references/00-skill-authoring-notes.md` |

## Audit modes

### Quick audit

Use when the user wants a first pass or only gave a domain.

1. Check homepage and 3–10 key URLs.
2. Check HTTP status, redirects, HTTPS, canonical, indexability, title/description/H1.
3. Check `/robots.txt` and `/sitemap.xml`.
4. Inspect visible HTML and major templates.
5. Check mobile and performance signals if tools are available.
6. Return top issues and next actions.

### Full audit

Use when the user wants a complete report.

1. Define scope, regions, engines, URL templates, and available data.
2. Sample all important templates.
3. Run technical/indexability checks.
4. Compare raw HTML vs rendered HTML for JS-heavy sites.
5. Review metadata, content, internal linking, structured data, media, performance, mobile.
6. Add regional checks where relevant.
7. Produce scorecard, prioritized findings, roadmap, and verification plan.

### Migration audit

Use when URLs, domain, CMS/framework, protocol, or site structure changed.

1. Compare old vs new URL inventory.
2. Verify 301 redirect mapping.
3. Check canonical, sitemap, robots, hreflang, internal links, status codes.
4. Identify lost pages, redirect chains, soft 404s, indexability regressions.
5. Check old domains/subdomains that historically received traffic.
6. Produce a migration risk report and post-launch monitoring checklist.

### Previous-audit distillation

Use when the user provides a previous SEO audit, agency report, or technical SEO task.

1. Separate reusable audit patterns from site-specific findings.
2. Keep useful checks, expected states, validation methods, and report formatting.
3. Remove unsupported claims, outdated advice, fake examples, and one-off domain assumptions.
4. Map retained checks to existing references or create a small focused reference file.
5. Update the main `SKILL.md` only when the workflow or reference map changes.

## Sampling rules

Do not audit only the homepage unless the site is a one-page landing. Include representative templates:

- Homepage.
- Service/product/category page.
- Detail page: product, article, case, listing item.
- Contact/about/legal pages if relevant.
- Filtered or paginated URLs for catalog/ecommerce.
- Locale/region variants if present.
- Login/account/private pages if public URLs exist.
- Old domains/subdomains if a migration or previous version is mentioned.

If a sample is insufficient, say so and recommend a crawl.

## Priority definitions

- `P0 Critical`: blocks crawl/indexing for important pages, breaks redirects after migration, sitewide noindex, blocked production site, severe 5xx.
- `P1 High`: likely harms indexability, duplicate consolidation, rendering of important content, major template metadata/canonical problems.
- `P2 Medium`: quality/performance/UX/structured-data/internal-linking issues that can reduce effectiveness.
- `P3 Low`: cleanup, consistency, optional enhancements, monitoring improvements.

## Output contract

For a short answer, provide:

```md
# SEO audit summary: <domain>

## Scope and limitations
## Executive summary
## Top findings
## Priority backlog
## What to verify next
```

For a full report, use `references/08-reporting-scoring.md`.

## Anti-hallucination rules

- If the site could not be crawled, say what was not checked.
- If a private tool was unavailable, do not infer Search Console/Yandex/Bing data.
- If performance was not measured with a tool, do not assign exact Core Web Vitals values.
- If structured data was not validated, say “needs validation,” not “valid.”
- If a recommendation is engine-specific, name the engine.
- Prefer official search engine documentation over SEO blogs.
- Do not recommend fake reviews, fake ratings, fake authors, hidden FAQ, or structured data that does not match visible page content.
- Do not state that `changefreq` or `priority` are major Google ranking factors; treat them as secondary sitemap metadata.
- Do not apply blanket `nofollow` to every external link; classify links as editorial, sponsored, user-generated, or untrusted.
