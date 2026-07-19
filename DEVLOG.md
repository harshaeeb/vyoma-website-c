# Dev Log — Vyoma Website

Handoff notes for picking this project back up. Repo is a static site, no build step (see [README.md](README.md) for file layout and deploy steps).

## Current state (as of 2026-07-18)

- Local `main` is in sync with `origin/main` (`https://github.com/harshaeeb/vyoma-website-c.git`), commit `a6772d4`, clean working tree.
- Pages: `index.html`, `fragrances.html`, `wellness.html`, `wholesale.html`, `contact.html`, plus `policies/` (hub + 5 legal pages: terms, privacy, refund, shipping, accessibility).
- Styling is split between `shared.css` and large embedded `<style>` blocks per page. Logos are embedded as base64 in the HTML — no external image dependencies at runtime (the `Vyoma_*.png` files in the repo root are source assets, not referenced directly by the pages).

## Color scheme (as of 2026-07-18)

The site was redesigned from a dark-crimson hero/footer/section look to a light, mature-luxury palette:

- `--blush` (`#F0DAD1`) and `--blush-dk` (`#E0BCAE`) are new tokens in [shared.css](shared.css) — medium-shade "highlight" backgrounds used for heroes, footers-turned-light-but-adjacent-accents, and alternating accent cards (fragrance profiles, testimonials, pricing tiers, promo boxes). They replace what used to be solid `--crimson-dk`/`--crimson`/`--maroon` full-bleed backgrounds.
- The `.section--dark` / `.section--crimson` class names in shared.css are historical — both now render as blush/blush-dk, not literal dark backgrounds. Don't be misled by the names when editing.
- Footer switched from dark crimson to light `--ivory-dk`; its horizontal logo is now the cream-on-light variant (`Vyoma_Header_03_creamCrimson.png`) instead of the white-on-dark variant, swapped via base64 replacement across all 11 pages.
- Along the way, fixed two pre-existing contrast bugs unrelated to the palette change: the "Five Steps of Sacred Craft" section on `fragrances.html` and the "Partner Journey" steps on `wholesale.html` had ivory/tan text sitting directly on plain ivory backgrounds (effectively invisible).

## Open items / known gaps

1. **No CNAME file.** It was deleted (`df59987 Delete CNAME`), so the custom-domain section of the README is stale — GitHub Pages is presumably serving from the default `github.io` URL, not `vyoma.com`. Revisit whether a custom domain is still wanted before following those README instructions.
2. **No test/build tooling.** This is intentionally a zero-dependency static site — verification is manual (open the HTML files, or check via GitHub Pages after push).

## Recent history

- Formspree activated on the contact form — [contact.html:192](contact.html) now points at the real endpoint (`https://formspree.io/f/maqrjwyo`), confirmed working end-to-end.
- `a6772d4` — Redesigned color scheme to light/blush luxury palette (see above); fixed two pre-existing contrast bugs.
- `365ca96` — Added this DEVLOG for session handoff.
- `a00d939` — Wired up Formspree on contact form (endpoint later activated, see above).
- `b3a1a8a` — Redesigned all 6 policy pages with full Vyoma branding (nav, hero, sticky TOC sidebar, footer, cookie banner) to match the main site.
- `999a2e5` — Added the `policies/` section and linked it into main site nav/footer.
- `df59987` — Deleted CNAME.
- `cbf0e2a` — Initial upload.

## Suggested next steps

- Decide on custom domain — either restore a CNAME + DNS setup, or drop that section from the README.
