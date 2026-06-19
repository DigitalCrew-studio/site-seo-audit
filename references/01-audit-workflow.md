# SEO Audit Workflow

## Contents

- Scope setup
- URL sampling
- Crawl/index checks
- Template review
- Content and intent review
- Performance/mobile review
- Regional review
- Report assembly

## Scope setup

Record:

- Domain, protocol, canonical host: `https`, `www` vs non-`www`.
- Target regions, languages, and search engines.
- Site type and business goal.
- Important templates.
- Known constraints: no private tool access, staging-only access, blocked crawling, authentication.

State limitations in the final report.

## URL sampling

Use 5–20 URLs for a manual audit. For larger sites, request or run a crawl.

Minimum sample:

- `/`
- `/robots.txt`
- `/sitemap.xml`
- One service/product/category page.
- One detail page: article/product/case.
- One contact/about page.
- One old URL if migration is involved.
- One paginated or filtered URL if catalog/ecommerce.
- One alternate-language URL if international.

## Audit sequence

1. Resolve domain variants:
   - `http://example.com`
   - `http://www.example.com`
   - `https://example.com`
   - `https://www.example.com`
2. Check status codes and redirect chains.
3. Check `robots.txt` and `sitemap.xml`.
4. Check indexability signals:
   - HTTP status.
   - `robots.txt` accessibility.
   - `meta robots`.
   - `X-Robots-Tag`.
   - Canonical.
   - Password/auth blocks.
5. Review metadata and HTML semantics.
6. Review internal links and crawl paths.
7. Compare raw HTML and rendered HTML for JS-heavy sites.
8. Validate structured data if present.
9. Review images/media and performance signals.
10. Review mobile-first risks.
11. Apply regional checks.
12. Build findings and roadmap.

## Template review

For each representative template, record:

| Template | URL | Status | Indexable | Canonical | Title | H1 | Notes |
|---|---|---:|---|---|---|---|---|
| Homepage | `/` | 200 | yes/no | self/other | ok/issue | ok/issue | ... |

## Evidence standards

Use the strongest available evidence:

1. Search Console/Yandex/Bing data.
2. Server logs or crawl export.
3. Direct HTTP headers and HTML.
4. Rendered DOM / browser inspection.
5. Lighthouse/PageSpeed/WebPageTest.
6. Manual observation.

Do not convert assumptions into findings. Write assumptions as “Hypothesis” or “Needs verification.”

## Completion criteria

The audit is complete when it has:

- Scope and limitations.
- Template coverage.
- Technical/indexability review.
- Content/semantics review.
- Performance/mobile review.
- Regional review if relevant.
- Prioritized findings.
- Verification plan.
