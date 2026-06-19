# JavaScript Rendering Reference

## Contents

- When JS rendering matters
- Raw HTML vs rendered HTML
- SPA risks
- Lazy loading risks
- JS navigation risks
- Framework-specific notes

## When JS rendering matters

Use this reference for React, Vue, Angular, Next.js, Nuxt, Remix, SvelteKit, SPA, PWA, headless CMS, and sites where content appears after client-side API calls.

## Raw HTML vs rendered HTML

Compare:

- Raw HTML from `curl` / “View source”.
- Rendered DOM from browser automation / DevTools.

Critical SEO content should be present or reliably renderable:

- H1 and main copy.
- Product/service/category listings.
- Internal links.
- Metadata/canonical.
- Structured data.

If raw HTML is mostly an empty root node, document the risk and test rendering.

## SPA risks

Common issues:

- All routes return the same HTML without route-specific metadata.
- Pages require client-side JS before any meaningful content exists.
- Navigation uses click handlers instead of real links.
- Dynamic routes lack unique titles/descriptions/canonicals.
- Auth/session checks hide public content.
- API errors create empty pages with `200` status.

## Lazy loading risks

Check:

- Lazy-loaded content appears when crawlers or users can reach it.
- Infinite scroll has crawlable pagination or linked pages.
- Critical content is not loaded only after user interaction.
- Images have dimensions and are not all deferred when above the fold.

## JS navigation risks

Crawlable links should use actual anchors:

```html
<a href="/category/widgets">Widgets</a>
```

Do not rely only on:

```html
<div onclick="router.push('/category/widgets')">Widgets</div>
```

## Framework-specific notes

For SSR/SSG frameworks:

- Prefer server-rendered content for SEO-critical pages.
- Ensure route-level metadata is generated server-side.
- Ensure canonical and structured data are present per route.
- Avoid making the whole app a client-only component when not necessary.

For pure SPAs:

- Consider SSR, SSG, dynamic rendering alternatives, or pre-rendering for public SEO pages.
- Verify rendered HTML with a crawler capable of JavaScript rendering.

## SEO-critical metadata rendering

Do not check only visible content. Compare raw HTML and rendered DOM for:

- `<title>`;
- meta description;
- canonical;
- robots meta;
- hreflang alternates;
- Open Graph tags;
- Twitter/X Card tags;
- JSON-LD;
- H1;
- primary content;
- internal links.

If these appear only after client-side hydration, report a rendering risk for SEO-critical templates. For SSR/SSG-capable frameworks, recommend server-rendering route-specific metadata and primary content.

## Evidence collection

Use two evidence columns when possible:

```md
- Raw HTML evidence: <curl/view-source snippet>
- Rendered DOM evidence: <browser/devtools/crawler snippet>
```

If a crawler cannot render JavaScript, state that the JS-rendered state was not verified.
