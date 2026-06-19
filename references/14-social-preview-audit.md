# Social Preview Audit Reference

## Purpose

Use this reference to audit how pages appear when shared in messengers, social networks, and link preview systems.

This is not a direct ranking audit. It affects link presentation, trust, shareability, and CTR in external channels.

## Scope

Check:

- Open Graph tags;
- Twitter/X Card tags;
- preview images;
- canonical/share URL consistency;
- per-template uniqueness;
- image accessibility and response status.

## Open Graph checks

Expected fields:

- `og:url` equals the canonical final URL;
- `og:title` is page-specific and aligned with `<title>` or page intent;
- `og:description` is page-specific and aligned with meta description or page summary;
- `og:site_name` is stable;
- `og:type` is appropriate:
  - `website` for homepage/general pages;
  - `article` for editorial content;
  - product-specific type only when supported and accurate;
- `og:image` exists, returns `200`, and is share-ready.

Image guidance:

- Use a large image, commonly around `1200x630` for broad compatibility.
- Avoid tiny, cropped, transparent, or text-heavy images.
- Ensure the file is not blocked by robots, auth, hotlink protection, or CDN rules.
- Use stable absolute URLs.

## Twitter/X Card checks

Expected fields:

- `twitter:card`, commonly `summary_large_image` for content-rich pages;
- `twitter:title`;
- `twitter:description`;
- `twitter:image`;
- `twitter:site` / `twitter:creator` only if the official account is known and accurate.

Avoid placeholder handles.

## Per-template expectations

| Page/template | Preview requirement |
|---|---|
| Homepage | Brand-level title, description, and hero/share image. |
| Service page | Service-specific title, description, and image. |
| Article/case | Content-specific title, summary, and article/case image. |
| Product page | Product-specific title, image, and short value description. |
| Legal/private pages | Usually basic previews or no special optimization. |

## Validation methods

Use available tools:

- platform sharing debugger when possible;
- raw HTML inspection;
- HTTP checks for image status, content type, size, and cache headers;
- manual test by sharing a URL in target channels if allowed.

## Common issues

- same OG title/description on every page;
- `og:url` differs from canonical;
- image URL returns `404`, redirects, or requires auth;
- image too small or wrong aspect ratio;
- article pages use `website` type instead of `article`;
- social tags are client-side only;
- preview image is generated dynamically but not cacheable or too slow.

## Reporting snippet

```md
### [P2] Article pages use generic social previews
- Area: Social preview
- Affected URL(s): /blog/<slug>
- Observation: Article pages share the homepage `og:title`, `og:description`, and `og:image`.
- Evidence: <raw HTML snippet>
- Risk: Shared links look generic and may reduce trust/CTR in social and messenger channels.
- Recommendation: Generate per-article OG/Twitter tags from article title, description, canonical URL, and image.
- Owner: Frontend / CMS
- Verification: Re-check raw HTML and platform sharing debugger after cache refresh.
```
