# International and Regional SEO Reference

## Contents

- International basics
- hreflang
- Google/global
- Yandex/RU-CIS
- Bing/Yahoo/IndexNow
- Naver/Korea
- Baidu/China
- Seznam/Czech Republic

## International basics

Check:

- Target countries and languages.
- URL structure: subdirectory, subdomain, ccTLD.
- Locale-specific content, currency, contacts, legal data.
- Avoid automatic redirects that prevent users/crawlers from accessing other locales.
- Keep each language/region page independently useful.

## hreflang

Use when multiple localized equivalents exist.

Check:

- Correct language-region codes.
- Self-referencing hreflang.
- Return links between alternates.
- Canonical does not contradict hreflang.
- Sitemap hreflang and HTML hreflang are consistent if both used.
- `x-default` where appropriate.

## Google/global

Prioritize:

- Crawlability/indexability.
- Helpful content aligned to intent.
- Mobile-first parity.
- Structured data policy compliance.
- Page experience and Core Web Vitals.
- Search Console monitoring.

## Yandex/RU-CIS

Check:

- Yandex Webmaster access if available.
- Yandex-specific indexing/excluded pages reports.
- `robots.txt` and Sitemap in Yandex tools.
- `Crawl-delay` only if intentionally needed.
- Regionality and business/contact signals for local commercial sites.
- Yandex Metrica goals if analytics is part of scope.

## Bing/Yahoo/IndexNow

Check:

- Bing Webmaster Tools access if available.
- Sitemap submitted to Bing.
- IndexNow support if site has frequent updates.
- URL submission for important updated URLs.
- Bing-specific crawl/index reports.

## Naver/Korea

Check:

- Naver Search Advisor setup.
- Site verification.
- robots and sitemap submission.
- Korean-language content quality if targeting Korea.
- Regional SERP expectations: Naver often has its own content ecosystem patterns.

## Baidu/China

Check:

- Baidu Search Resource Platform where available.
- Simplified Chinese localization if targeting mainland China.
- China hosting/CDN/accessibility considerations.
- Page speed from mainland China.
- Avoid reliance on blocked third-party resources.
- Verify with current Baidu resources or regional specialists when possible.

## Seznam/Czech Republic

Check:

- SeznamBot crawling/indexing guidance.
- Czech-language content quality if targeting Czechia.
- Sitemap and robots behavior.
- Local search expectations and regional directories where relevant.

## Hreflang cluster audit

For each localized template, verify:

- every locale version has a self-referencing hreflang;
- every locale version references all other valid alternates;
- alternates are reciprocal;
- `x-default` exists where a default/global URL is appropriate;
- alternate URLs return `200`;
- alternate URLs are indexable;
- alternate URLs do not redirect unexpectedly to another language;
- canonical does not point across languages unless intentionally consolidating duplicates;
- sitemap and HTML hreflang do not conflict.

## Localized internal linking

When a user is on a localized version, default internal links should usually remain in the same locale.

Report as an issue when:

- `/ru` pages link to English equivalents by default;
- language switcher redirects users back to the current locale;
- footer/menu/breadcrumb links mix locales unintentionally;
- localized pages canonicalize to another language while also declaring hreflang alternates.
