# Page-Type Structured Data Matrix

## Purpose

Use this reference to choose structured data by page type and avoid invalid or misleading schema recommendations.

Structured data helps search engines understand entities and may make a page eligible for enhanced presentation. It does not guarantee rankings or rich results.

## Global rules

- Prefer JSON-LD unless a platform has a reason to use another syntax.
- Mark up only content that exists and is accurate.
- Do not invent reviews, ratings, prices, availability, authors, addresses, or phone numbers.
- Do not mark hidden FAQ as `FAQPage`.
- Validate syntax and engine-specific eligibility where possible.
- Per-page schema should match the current page, not be copied globally without context.

## Matrix

| Page/template | Recommended schema | Notes |
|---|---|---|
| Homepage | `Organization`, `WebSite`, optionally `WebPage` | Include legal brand name, URL, logo, sameAs where verified. |
| Corporate/about page | `AboutPage` or `WebPage`, `Organization` if relevant | Avoid duplicating conflicting organization data. |
| Service page | `Service`, `WebPage`, `BreadcrumbList` | Use only real service details visible on page. |
| Local service page | `LocalBusiness` or narrower subtype, `Service`, `BreadcrumbList` | Use only accurate address/area served/contact details. |
| Blog article/news | `Article` or `BlogPosting`, `BreadcrumbList` | Include real author, publisher, dates, image. |
| Case study | `Article`, `CreativeWork`, or `WebPage`, `BreadcrumbList` | Choose based on how the case is presented. |
| Product detail | `Product`, `Offer`, optionally `Review`/`AggregateRating` | Price, availability, reviews must be real and visible or supported by source data. |
| Product/category listing | `CollectionPage`, optionally `ItemList`; use `AggregateOffer` only when valid | Avoid marking a category as a fake single product unless it truly represents a product collection. |
| FAQ section | `FAQPage` | Only when Q&A content is visible and eligible for the target engine. |
| Contact page | `ContactPage`, `Organization` | Use accurate contact points. |
| Search results page | Usually no schema; often `noindex` depending on strategy | Internal search results are often not useful landing pages. |
| Login/account page | Usually no schema; often `noindex` | See private/account reference. |
| All non-home pages | `BreadcrumbList` where breadcrumbs exist | Final breadcrumb may be text-only rather than a link. |

## Validation checks

For each JSON-LD block, verify:

- valid JSON syntax;
- correct `@context` and `@type`;
- required/recommended fields for the target rich-result type;
- URLs are canonical and return `200`;
- images return `200` and meet size/format expectations;
- dates are valid and truthful;
- content matches visible page content;
- no duplicate/conflicting entities across multiple scripts.

## Risk patterns

Report these as issues:

- `AggregateRating` exists but no visible or real reviews exist.
- `FAQPage` includes questions not visible to users.
- `Product` price/availability differs from page content.
- `Article` author is fake or missing where required.
- `Organization` has placeholder social links or phone numbers.
- JSON-LD is injected only after client-side hydration on important pages and not present in raw HTML where SSR is expected.

## Priority guidance

- `P1`: misleading or policy-risk schema at scale, fake reviews/ratings, schema contradicts visible content.
- `P2`: missing schema on important eligible templates, invalid JSON-LD, broken image/logo URLs.
- `P3`: optional enhancements or field completeness improvements.
