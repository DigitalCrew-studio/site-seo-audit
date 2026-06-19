# Technical SEO and Indexability Reference

## Contents

- Status codes and redirects
- HTTPS and host canonicalization
- robots.txt
- sitemap.xml
- Indexability
- Canonical and duplicates
- Facets, pagination, parameters
- Migration checks

## Status codes and redirects

Expected behavior:

- Important indexable pages return `200`.
- Permanent moves use `301` or `308`.
- Temporary moves use `302` or `307` only when genuinely temporary.
- Deleted pages return `404` or `410`.
- Server errors `5xx` are urgent when affecting important URLs.

Check:

- Redirect chains longer than one hop.
- Redirect loops.
- Mixed HTTP/HTTPS behavior.
- Inconsistent `www` and non-`www` behavior.
- Soft 404 pages returning `200`.

## HTTPS and canonical host

Pick one canonical host:

- `https://example.com`, or
- `https://www.example.com`.

All variants should redirect to the canonical host.

## robots.txt

Check `https://example.com/robots.txt`.

Look for:

- Accidental `Disallow: /` on production.
- Important CSS/JS/images blocked when needed for rendering.
- Sitemap directive.
- Engine-specific directives such as Yandex `Crawl-delay` where relevant.
- Staging rules accidentally deployed to production.

Important distinction:

- `robots.txt` controls crawling.
- `noindex` controls indexing.
- If a URL is blocked by `robots.txt`, crawlers may not see its `noindex` meta tag.

## sitemap.xml

Check:

- Sitemap URL exists and returns `200`.
- XML is valid.
- Only canonical, indexable `200` URLs are included.
- No redirects, `404`, `noindex`, blocked, parameter junk, or duplicate URLs.
- `lastmod` is accurate enough to be useful.
- Sitemap index is used for large sites.
- Image/video/news extensions only when relevant.

Sitemap is a discovery signal, not an indexing guarantee.

## Indexability

A URL is indexable only if signals align:

- Status is `200`.
- Not blocked by auth or firewall.
- Not blocked from crawling when content must be discovered.
- No `noindex` in meta or `X-Robots-Tag`.
- Canonical points to itself or to the intended representative URL.
- Page has meaningful, accessible content.

## Canonical and duplicates

Check:

- Self-canonical on canonical pages.
- Canonical absolute URL or correct relative behavior.
- Canonical not pointing all pages to homepage.
- Canonical not pointing to redirected/404/noindex URLs.
- Canonical consistency with sitemap and internal links.
- Parameter/UTM/filter pages handled intentionally.

Canonical is a strong signal, not an absolute command.

## Facets, pagination, parameters

For ecommerce/catalog sites:

- Define which filters are indexable landing pages.
- Block or canonicalize crawl traps.
- Avoid infinite combinations in sitemap.
- Keep internal linking to valuable categories.
- Ensure paginated content can be crawled where needed.

## Migration checks

For migrations:

- Every important old URL maps to a relevant new URL.
- Redirects are direct and permanent.
- Internal links updated to new URLs.
- Canonicals updated to new URLs.
- Sitemap contains only new canonical URLs.
- Old high-value URLs are monitored for `404` and traffic loss.
