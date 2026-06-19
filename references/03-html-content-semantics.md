# HTML, Metadata, Content, and Internal Links Reference

## Contents

- Titles and descriptions
- Headings and landmarks
- Semantic HTML
- Content quality and search intent
- Internal linking
- Images and media
- Local trust signals

## Titles and descriptions

Each important page should have:

- Unique `<title>`.
- Unique meta description.
- Title aligned with page intent.
- No template-wide duplicates like “Home” or only brand name.
- No keyword stuffing.

Quick checks:

- Title length is not the main goal; clarity and uniqueness matter more.
- Description does not directly rank the page, but affects snippet quality and click expectations.
- Title and H1 can differ, but should not contradict each other.

## Headings and landmarks

Expected structure:

```html
<header>...</header>
<nav>...</nav>
<main>
  <h1>Primary page topic</h1>
  <section>
    <h2>Section topic</h2>
    <article>
      <h3>Item topic</h3>
    </article>
  </section>
</main>
<footer>...</footer>
```

Check:

- One clear primary H1 per page/template.
- H2/H3 hierarchy is logical.
- Headings are not used only for visual styling.
- Important text is real text, not only image text.

## Semantic HTML

Prefer:

- `<a href="...">` for navigation.
- `<button>` for actions.
- `<main>`, `<nav>`, `<section>`, `<article>`, `<footer>` where meaningful.
- Tables for tabular data.
- Lists for lists.

Avoid:

- Clickable `<div>` used as links.
- Important navigation only in JavaScript handlers.
- Large text sections hidden from mobile users.

## Content quality and search intent

For every important page, verify:

- The page answers a specific user intent.
- The main service/product/topic is obvious above the fold.
- The page contains enough useful detail to be independently valuable.
- Claims are supported: examples, process, pricing, constraints, FAQ, cases, proof.
- Similar pages are not thin duplicates.

Commercial service page baseline:

- What is offered.
- Who it is for.
- Problems solved.
- Deliverables.
- Process.
- Timeline or factors affecting timeline.
- Pricing or price logic if possible.
- Proof/cases.
- FAQ.
- CTA/contact path.

## Internal linking

Check:

- Important pages are reachable by crawlable links.
- Main navigation and footer contain key pages.
- Related pages link to each other.
- Anchor text is descriptive.
- Orphan pages are identified.
- Broken internal links are fixed.

Bad:

```html
<div onclick="go('/services/web-apps')">Web apps</div>
```

Good:

```html
<a href="/services/web-apps">Web application development</a>
```

## Images and media

Check:

- Images have useful `alt` when informative.
- Decorative images use empty `alt=""` where appropriate.
- Important text is not embedded only inside images.
- Image dimensions are specified to reduce layout shift.
- Large images are compressed and responsive.
- Lazy loading is not applied to critical LCP media.

## Local trust signals

For local or regional businesses, check:

- Contact page.
- Address/region if relevant.
- Phone/email/messengers.
- Legal/business entity data where appropriate.
- LocalBusiness/Organization structured data where appropriate.
- Consistent name/address/phone across site and business profiles.
