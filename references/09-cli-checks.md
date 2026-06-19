# CLI Checks Reference

## Contents

- Status and headers
- robots.txt
- sitemap.xml
- Raw HTML
- Canonical/title/meta/H1 extraction
- Rendered HTML
- Lighthouse
- Notes

## Status and headers

```bash
curl -I -L https://example.com/
```

Check final status, redirect chain, canonical host, `X-Robots-Tag`, cache headers.

Check domain variants:

```bash
for url in \
  http://example.com \
  http://www.example.com \
  https://example.com \
  https://www.example.com; do
  echo "\n### $url"
  curl -I -L --max-redirs 5 "$url" | sed -n '1,20p'
done
```

## robots.txt

```bash
curl -s https://example.com/robots.txt
```

Look for `Disallow`, `Allow`, `Sitemap`, engine-specific blocks.

## sitemap.xml

```bash
curl -s https://example.com/sitemap.xml | head -80
```

If sitemap index exists, inspect child sitemaps.

Extract URLs:

```bash
curl -s https://example.com/sitemap.xml | grep -oE '<loc>[^<]+' | sed 's/<loc>//'
```

## Raw HTML

```bash
curl -sL https://example.com/ -o page.html
```

Inspect key tags:

```bash
grep -iE '<title|name="description"|rel="canonical"|name="robots"|application/ld\+json|<h1' page.html
```

## Rendered HTML

If browser automation is available, use it to save rendered DOM. If not, state that JS rendering was not fully checked.

Example with Playwright if installed:

```bash
node - <<'NODE'
const { chromium } = require('playwright');
(async () => {
  const browser = await chromium.launch({ headless: true });
  const page = await browser.newPage();
  await page.goto('https://example.com/', { waitUntil: 'networkidle' });
  console.log(await page.content());
  await browser.close();
})();
NODE
```

## Lighthouse

If Lighthouse is available:

```bash
lighthouse https://example.com/ --output html --output-path lighthouse.html --chrome-flags="--headless"
```

Do not treat Lighthouse SEO score as a full SEO audit. It covers only a subset of checks.

## Notes

- Use commands as evidence, but do not expose huge outputs in the report.
- Summarize relevant lines and attach snippets.
- If tools are unavailable, ask for exports or state the limitation.
