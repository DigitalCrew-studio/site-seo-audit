# Private, Account, Auth, Checkout, and Admin Indexing Reference

## Purpose

Use this reference when the site has login, registration, account, dashboard, checkout, cart, admin, app, or other private/public-hybrid URLs.

These pages often exist as public routes but are not useful search landing pages.

## URL patterns to inspect

Look for:

- `/login`, `/sign-in`, `/signin`, `/auth`;
- `/register`, `/signup`;
- `/account`, `/profile`, `/dashboard`, `/cabinet`;
- `/cart`, `/checkout`, `/payment`, `/order`;
- `/admin`, `/manager`, `/cms`;
- `/app`, app subdomains, and mobile-app landing/auth flows;
- localized variants such as `/ru/login` or `/en/account`.

## Classification

Classify each page as:

1. `Public landing page`: useful public content, can be indexable if intentional.
2. `Thin auth page`: login/register form only; usually `noindex`.
3. `Private user page`: requires authentication; should not be indexable.
4. `Transactional page`: cart/checkout/payment; usually `noindex` and not in sitemap.
5. `Admin/internal page`: should be protected and not indexable.
6. `App marketing page`: may be indexable if it contains useful public content.

## Checks

For each URL/template:

- HTTP status for unauthenticated users;
- whether content is useful publicly;
- meta robots and `X-Robots-Tag`;
- canonical target;
- presence in sitemap;
- internal links from public pages;
- whether private data can leak in rendered HTML;
- whether auth redirects create crawl traps;
- whether blocked-by-robots pages still appear in search due to external links.

## Expected states

Usually:

- Login/register pages: `noindex, follow` or equivalent, unless a search landing page is intentional.
- Account/dashboard/private pages: require auth; no private content in public HTML; not in sitemap; usually `noindex` when public response exists.
- Checkout/cart/payment: not in sitemap; usually `noindex`; canonical should not point to unrelated pages.
- Admin/staging: protected by authentication and/or network controls; not only hidden from navigation.

## Important distinction

Do not rely only on `robots.txt` to remove private/public-auth pages from search. If a URL is blocked from crawling, crawlers may not see `noindex`. For pages that must be removed from the index, allow crawl of a `noindex` response or use appropriate search engine removal tools where necessary.

## Priority guidance

- `P0`: private data visible in public HTML or indexable admin/internal pages.
- `P1`: important private/account templates indexable at scale; auth redirects create crawl traps.
- `P2`: thin login/register/checkout pages in sitemap or internally overlinked.
- `P3`: metadata/social preview cleanup for auth pages.

## Reporting snippet

```md
### [P1] Account login page is indexable and included in sitemap
- Area: Private/account indexation
- Affected URL(s): /login, /account
- Observation: Auth pages return 200, are indexable, and appear in sitemap.
- Evidence: <curl output + sitemap snippet>
- Risk: Thin/private-intent pages can enter search results and waste crawl budget.
- Recommendation: Remove from sitemap; add `noindex, follow` where the public response is crawlable; protect private routes; keep only intentional app marketing pages indexable.
- Owner: Frontend / Backend / SEO
- Verification: Re-check raw HTML/meta robots, sitemap, and webmaster indexed/excluded reports.
```
