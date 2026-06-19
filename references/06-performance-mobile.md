# Performance and Mobile Reference

## Contents

- Core Web Vitals
- LCP checks
- INP checks
- CLS checks
- Mobile-first checks
- Images, fonts, caching

## Core Web Vitals

Use field data when available. Lab data is useful for debugging but not identical to real-user data.

Primary metrics:

- LCP: loading performance of the main content.
- INP: interaction responsiveness.
- CLS: visual stability.

Do not invent exact values without measurement.

## LCP checks

Check:

- What is the LCP element.
- Whether hero image/text is server-rendered.
- Image size and format.
- Preload/fetch priority for critical image where appropriate.
- Server response time.
- Render-blocking CSS/JS.
- Client-side hydration delaying content.

## INP checks

Check:

- Heavy JavaScript on initial load.
- Large bundles.
- Expensive event handlers.
- Third-party scripts.
- Long tasks.
- Unnecessary client-side rendering.

## CLS checks

Check:

- Missing image/video dimensions.
- Late-loading fonts.
- Ad/banner/widget insertion.
- Skeletons that change size.
- Cookie banners and popups shifting layout.

## Mobile-first checks

Google primarily uses the mobile version for indexing. Verify:

- Important content and links are present on mobile.
- Mobile does not hide SEO-critical content available on desktop.
- Viewport meta tag is present.
- Tap targets are usable.
- No horizontal scroll.
- Popups do not block content.
- Structured data and metadata are same or equivalent on mobile.

## Images, fonts, caching

Check:

- Responsive images: `srcset`/`sizes` or framework equivalent.
- Modern formats: WebP/AVIF where suitable.
- Compression appropriate to visual quality.
- Lazy loading below the fold.
- Font loading avoids invisible text and layout shifts.
- Static assets have caching headers.
- Critical CSS and JS are not excessive.
