# Third-Party Audit Pattern Extraction Reference

## Purpose

Use this reference when the user provides an external SEO audit, agency report, technical SEO task, or remediation document and asks what should be reused in this skill.

Do not treat the external audit as automatically correct. Treat it as a source of patterns to review.

## Extraction workflow

1. Identify all audit sections and checks.
2. Mark each item as one of:
   - `Reusable check`: should become part of the generic SEO audit workflow.
   - `Site-specific finding`: useful only for the audited site.
   - `Unsupported claim`: needs current official-source verification.
   - `Outdated / risky advice`: should be rejected or rewritten.
   - `Implementation detail`: useful as an example, but not a universal rule.
3. Convert reusable checks into evidence-based audit steps.
4. Add each check to the most specific reference file.
5. Keep `SKILL.md` short; update it only when workflow or reference routing changes.

## Useful patterns to extract

Prefer extracting:

- Issue format: priority, status, affected URLs, fix, verification.
- Sitemap requirements: canonical URLs, `200` status, valid XML, useful `lastmod`, sitemap index for large or multilingual sites.
- Crawl hygiene checks: `404`, `5xx`, redirect chains, links to redirected URLs, soft `404`.
- Multilingual checks: `hreflang`, self-reference, reciprocal alternates, `x-default`, locale-consistent internal links.
- Raw HTML vs rendered DOM checks for metadata, canonical, hreflang, JSON-LD, H1, main content, and links.
- URL hygiene checks: lowercase, hyphen separators, repeated slashes, parameters, canonical trailing slash policy.
- Structured-data matrix by page type.
- Social preview checks: Open Graph and Twitter/X Cards.
- CMS rules for image `alt` generation.
- External link classification.
- Private/account/auth page indexation checks.
- Old domain, old subdomain, and legacy URL handling.

## What to reject or rewrite

Reject or rewrite these patterns:

- Claims that structured data directly guarantees ranking growth.
- Claims that rich results, indexing, or Discover traffic are guaranteed.
- Fake `Review`, `AggregateRating`, author, price, or availability examples that are not backed by visible page content or source data.
- Blanket `rel="nofollow"` for all external links.
- Treating sitemap `priority` and `changefreq` as critical Google ranking signals.
- Hard universal limits such as “URL over 115 characters is an error.” Treat these as warnings unless a source or business rule requires otherwise.
- Search-engine-specific rules applied globally without naming the engine.

## Conversion template

Use this template when converting an agency-audit item into a skill reference:

```md
## <Check name>

When to run:
- <site type, page type, migration, region, framework>

Check:
- <repeatable verification step>

Expected state:
- <specific desired behavior>

Report as:
- Priority: <P0/P1/P2/P3 guidance>
- Evidence: <URL / snippet / tool output>
- Owner: <SEO/Frontend/Backend/DevOps/Content/Analytics>
- Verification: <how to re-check>

Notes:
- <engine-specific caveats or limitations>
```

## Skill update rule

Do not add every extracted check to `SKILL.md`. Use `SKILL.md` as a router. Put details in references.

Update `SKILL.md` only when:

- a new audit mode is needed;
- a new reference file is added;
- the finding template changes;
- a critical anti-hallucination rule is needed.
