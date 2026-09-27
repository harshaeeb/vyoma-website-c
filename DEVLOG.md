# Dev Log — Vyoma Website

Handoff notes for picking this project back up. Repo is a static site, no build step (see [README.md](README.md) for file layout and deploy steps).

## Revamp (2026-09-27, branch `revamp-2026-09`)

**What changed**
- **Brand structure.** The site now presents **Vyoma Wellness Group** with two brands: **Vyoma Incense** and **Vyoma Wellness** (the nightly ritual app, coming soon). `wellness.html` is now the app page, with the four-step ritual and a Formspree waitlist form. It replaces the old "wellness benefits" page.
- **Products and prices.** Five fragrances, 13 sticks per box. The **5-Pack is $10** and the **10-Pack Starter Kit is $20** (suggested retail). Wholesale pricing isn't published; retailers get it on the line sheet via `contact.html?type=wholesale`. The old 20-stick $8.99 packs, cones, bulk bags and 40–50% discount tiers are gone.
- **Claims.** Removed:
  - health and medical claims (blood pressure, bacteria, cortisol, sleep, respiratory);
  - "organic," "fair trade," "charcoal-free" and "lab-tested," until the supplier's documentation supports them;
  - the placeholder testimonials, the market statistics and the "Bangalore / Malleswaram" origin (the supplier's location is unconfirmed; the site now says "India").

  Added "Burn with care" directions and an app disclaimer (not a medical device; never sleep with incense burning).
- **Images.** The base64 logos were replaced with web-sized files in `assets/`, taking pages from 400–840 KB to 12–22 KB.
- **Layout.** New responsive components are appended to `shared.css` ("v3 components"). Grids now collapse properly on phones.
- **Pages.** The nav and footer are identical on all 11 pages; the footer copyright reads "Vyoma Wellness Group". Contact email is standardized to `hello@vyomaincense.com`, matching the policy pages.
- **Hosting.** `_headers` adds response headers for Cloudflare Pages.

**Still open**
- Confirm the 5-Pack and 10-Pack contents (one or two of each fragrance, the starter-kit items, app access) before launch.
- Create the mailbox for `hello@vyomaincense.com`, plus the `privacy@`, `returns@`, `b2b@`, `legal@` and `accessibility@` addresses the policies use.
- Legal text still names "Vyoma LLC". Update it once the entity (Vyoma Incense LLC under Vyoma Wellness Group) is formed and counsel has reviewed it. The shipping policy also mentions international shipping, which isn't planned.
- The Instagram and Facebook links were removed from the footer; add them back when the handles exist.
- Once a custom domain is live, update the domain in the policies and the Formspree allowed-domains setting.

## State before the revamp (as of 2026-07-18)

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
