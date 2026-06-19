# Structured Data Reference

## Contents

- General rules
- Common schema types
- Validation
- Finding format for schema issues

## General rules

Structured data helps search engines understand page entities. It does not guarantee rich results.

Rules:

- Mark up only content visible to users or clearly represented on the page.
- Use the most specific relevant schema type.
- Keep data accurate and updated.
- Avoid fake ratings, fake reviews, hidden FAQ, or misleading business data.
- Validate JSON-LD syntax and eligibility where possible.

## Common schema types

For commercial/corporate sites:

- `Organization`
- `LocalBusiness` or narrower subtype if appropriate
- `WebSite`
- `BreadcrumbList`
- `FAQPage` when visible FAQ exists and engine policies allow it
- `Article` or `BlogPosting` for editorial pages
- `Product` for product pages
- `Service` where appropriate, but check engine support expectations
- `Review`/`AggregateRating` only with genuine visible reviews and policy compliance

## Placement

JSON-LD is usually placed in:

```html
<script type="application/ld+json">...</script>
```

Per-page structured data should match the page, not the whole site globally.

## Validation

Use available validators:

- Google Rich Results Test for Google-specific rich result eligibility.
- Schema Markup Validator for general Schema.org validation.
- Search Console enhancements reports after indexing.

## Finding format for schema issues

Examples:

```md
### [P2] FAQPage markup does not match visible content
- Observation: JSON-LD contains FAQ entries that are not visible on the page.
- Evidence: <URL + JSON-LD snippet + visible page check>
- Risk: Search engines may ignore the markup or treat it as misleading.
- Recommendation: Remove hidden FAQ entries or make the same FAQ visible to users.
- Verification: Re-run Rich Results Test and inspect rendered page.
```
