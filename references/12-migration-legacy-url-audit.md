# Migration and Legacy URL Audit Reference

## Purpose

Use this reference when the site has changed domain, protocol, host, subdomain, CMS/framework, language structure, or URL patterns.

Also use it when a previous audit mentions old domains, old subdomains, app/login subdomains, staging hosts, or historical traffic.

## Inputs to request

Ask for:

- old domain(s), subdomain(s), and URL patterns;
- new domain and canonical host;
- launch/migration date;
- old sitemap or crawl export;
- Search Console/Yandex/Bing access or export if available;
- top organic landing pages before migration;
- backlink or high-traffic URL list if available.

If the user cannot provide these, run a limited public check and state the limitation.

## Checks

### 1. Canonical host and protocol

Expected:

- `http` redirects to `https`.
- non-canonical host redirects to canonical host.
- `www` vs non-`www` policy is consistent.
- redirects are one-hop where possible.

### 2. Old URL mapping

Expected:

- High-value old URLs redirect to the most relevant new URL.
- Do not redirect every old URL to the homepage unless there is no relevant equivalent.
- Deleted pages return `404` or `410` when no replacement exists.
- Old sitemaps are not still submitted as current production sitemaps.

### 3. Redirect quality

Check:

- redirect chains;
- redirect loops;
- `302/307` used for permanent moves;
- redirects to `404`, `noindex`, or blocked pages;
- locale redirects that trap users/crawlers in one language;
- trailing slash and case variations.

### 4. Internal links after migration

Expected:

- Internal links point directly to final canonical URLs.
- No internal links to redirected URLs where avoidable.
- Locale-specific pages link to the correct locale by default.
- Old absolute URLs are removed from templates, CMS content, menus, breadcrumbs, footer, and XML feeds.

### 5. Sitemap after migration

Expected:

- sitemap contains only new canonical URLs;
- old URLs are excluded;
- URLs return `200`;
- `lastmod` is meaningful;
- multilingual sites use valid hreflang clusters in HTML or sitemap;
- sitemap index is used when separate sitemaps are needed.

### 6. Canonical and hreflang after migration

Expected:

- canonical points to the final new URL;
- hreflang alternates point to final `200` URLs;
- hreflang clusters are reciprocal;
- `x-default` exists where a default/global version is needed;
- canonical does not contradict hreflang.

### 7. Old subdomain handling

Check old subdomains such as:

- `app.example.com`;
- `old.example.com`;
- `blog.example.com`;
- `stage.example.com`;
- `www`/non-`www` variants.

Expected:

- public legacy subdomains with historical traffic redirect intentionally;
- private/staging subdomains are blocked from indexing and protected;
- app/auth subdomains are not indexed unless there is useful public content.

## Priority guidance

- `P0`: sitewide bad redirect, production blocked, important old URLs lost, redirect loop on key templates.
- `P1`: high-value old pages redirect to irrelevant pages or return `404`; hreflang/canonical broken after migration.
- `P2`: internal links still go through redirects; sitemap includes old or redirected URLs.
- `P3`: cleanup of low-value legacy URLs and consistency issues.

## Reporting snippet

```md
### [P1] High-value legacy URLs redirect to irrelevant destinations
- Area: Migration / redirects
- Affected URL(s): <old URL sample>
- Observation: Old URLs redirect to homepage instead of relevant replacements.
- Evidence: <curl -I output or crawl export>
- Risk: Search engines and users lose topic continuity; migration signals are weaker.
- Recommendation: Map each old URL group to the closest new URL; use 404/410 only when no replacement exists.
- Owner: Backend / DevOps / SEO
- Verification: Re-run redirect crawl; confirm one-hop 301/308 to relevant `200` canonical URLs.
```
