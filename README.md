# defygroup.ai — single page rebuild

Static site. No build step, no framework, no external dependencies at runtime.
Drop the contents of this folder at the web root and it works.

## Deploying to GitHub Pages
1. Push everything in this folder to the repo root of the branch Pages serves.
2. `CNAME` already contains `defygroup.ai`.
3. Confirm Pages is set to that branch, root folder. Done.

All paths are relative, so this works three ways: double-clicked straight off
your desktop, hosted at the domain root, or hosted in a subfolder like
`/preview/`. All three are tested.

## What's in here
- `index.html` — the whole page. CSS is inline, one small script for the FAQ accordion.
- `fonts/` — Playfair Display + DM Sans, self-hosted. No Google Fonts call, so no
  render-blocking third-party request and no visitor data leaving the domain.
- `media/` — five agent visuals (generated on the SOMIN platform) and four team
  portraits (matted onto a shared background so the set reads as one shoot).
- SEO / GEO layer — `robots.txt`, `sitemap.xml`, `feed.xml`, `site.webmanifest`,
  `humans.txt`, and for answer engines `llms.txt`, `llms-full.txt`, `ai.txt`.
- `og-cover.jpg` — 1200×630 social preview.
- Favicons at 16/32/48/180/192/512 plus `.ico` and `.svg`.

## Structured data
Seven JSON-LD blocks in `<head>`: Organization, WebSite, WebPage, Service (with an
offer catalog, one entry per agent), ItemList of the five agents, HowTo, and FAQPage
with twelve Q&As. The FAQ block is the one most likely to get picked up as a rich
result, and it mirrors the visible FAQ exactly, which is what Google requires.

## Open items
- All six portraits are in and share one treatment: cut out, matted onto the same
  #181818 surround, face width normalised to 323px, one duotone curve. If anyone's
  photo changes, run it through the same pipeline rather than dropping the raw file in.
- **Check the photo/name pairing** on Eric and Danil. LinkedIn blocks scraping, so
  the pairing came from the order the files arrived in, not from the profiles.
  If it's wrong it's a two-second fix: swap `media/eric.jpg` and `media/danil.jpg`.
- **No pricing anywhere**, by design. The FAQ answers "what does it cost" by
  pointing at email.
- The CRM agent is labelled "in final build" throughout, per the playbook's own
  instruction not to sell it as shipped.
