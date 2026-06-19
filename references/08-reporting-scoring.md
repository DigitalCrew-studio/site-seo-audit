# Reporting, Scoring, and Roadmap Reference

## Contents

- Scoring model
- Priority model
- Full report template
- Backlog format
- 30/60/90 roadmap

## Scoring model

Use a 100-point score only as an audit summary, not as a scientific SEO grade.

Suggested weighting:

| Area | Points |
|---|---:|
| Crawlability and indexability | 20 |
| Canonical, redirects, duplicates | 15 |
| Metadata, HTML semantics, internal links | 15 |
| Content and search intent | 15 |
| JavaScript rendering | 10 |
| Structured data | 8 |
| Performance and Core Web Vitals | 10 |
| Mobile-first and accessibility basics | 5 |
| Analytics and monitoring | 2 |

If data is unavailable, mark the area “not fully assessed” instead of guessing.

## Priority model

- `P0 Critical`: immediate action. Sitewide or high-value page crawl/index blockers.
- `P1 High`: fix in the next sprint. Important template-level SEO issues.
- `P2 Medium`: planned improvement. Quality, performance, content, and enhancement issues.
- `P3 Low`: cleanup or optional optimization.

## Full report template

```md
# SEO Audit: <domain>

## 1. Scope and limitations
- Domain:
- Date:
- Target regions/search engines:
- Site type:
- URLs/templates checked:
- Tools/data available:
- Limitations:

## 2. Executive summary
- Overall score:
- Main risks:
- Highest-impact fixes:

## 3. Scorecard
| Area | Score | Status | Notes |
|---|---:|---|---|

## 4. Critical findings
<Findings P0/P1>

## 5. Technical SEO and indexability

## 6. Canonical, redirects, and duplicates

## 7. HTML, metadata, semantics, and internal links

## 8. Content and search intent

## 9. JavaScript rendering

## 10. Structured data

## 11. Performance and mobile

## 12. Regional SEO

## 13. Analytics and monitoring

## 14. Prioritized backlog
| Priority | Issue | URL/template | Owner | Effort | Verification |
|---|---|---|---|---|---|

## 15. Roadmap
### 0–30 days
### 31–60 days
### 61–90 days

## 16. Appendix
- Commands used
- Source references
- URL sample
```

## Backlog format

Each task should be implementable:

```md
- Priority: P1
- Area: Canonical
- Template: Service pages
- Problem: Canonical points to homepage
- Fix: Generate self-canonical for each service URL
- Acceptance criteria: HTML contains canonical matching final URL; sitemap contains same URL; no redirect/noindex conflict
```

## Default 30/60/90 roadmap

### 0–30 days

- Fix P0/P1 indexability blockers.
- Resolve bad redirects, canonicals, noindex, robots issues.
- Clean sitemap.
- Ensure important pages have unique title, description, H1.
- Submit sitemap and request validation in webmaster tools.

### 31–60 days

- Improve internal linking.
- Expand thin commercial pages.
- Add/validate structured data.
- Fix major image/media issues.
- Address JavaScript rendering gaps.

### 61–90 days

- Improve Core Web Vitals.
- Build content clusters.
- Improve regional/local signals.
- Create ongoing monitoring dashboard.
- Re-crawl and compare before/after results.
