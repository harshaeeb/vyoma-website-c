# Dev Log — Vyoma Website

Handoff notes for picking this project back up. Repo is a static site, no build step (see [README.md](README.md) for file layout and deploy steps).

## Current state (as of 2026-07-18)

- Local `main` is in sync with `origin/main` (`https://github.com/harshaeeb/vyoma-website-c.git`), commit `a00d939`, clean working tree.
- Pages: `index.html`, `fragrances.html`, `wellness.html`, `wholesale.html`, `contact.html`, plus `policies/` (hub + 5 legal pages: terms, privacy, refund, shipping, accessibility).
- Styling is split between `shared.css` and large embedded `<style>` blocks per page. Logos are embedded as base64 in the HTML — no external image dependencies at runtime (the `Vyoma_*.png` files in the repo root are source assets, not referenced directly by the pages).

## Open items / known gaps

1. **Formspree is not activated yet.** [contact.html:192](contact.html) still has the placeholder endpoint `https://formspree.io/f/YOUR_FORM_ID`. The form UI, loading/success/error states, and honeypot field are all wired up — someone just needs to sign up at formspree.io, create a form, and swap in the real form ID.
2. **No CNAME file.** It was deleted (`df59987 Delete CNAME`), so the custom-domain section of the README is stale — GitHub Pages is presumably serving from the default `github.io` URL, not `vyoma.com`. Revisit whether a custom domain is still wanted before following those README instructions.
3. **No test/build tooling.** This is intentionally a zero-dependency static site — verification is manual (open the HTML files, or check via GitHub Pages after push).

## Recent history

- `a00d939` — Wired up Formspree on contact form (endpoint still placeholder, see above).
- `b3a1a8a` — Redesigned all 6 policy pages with full Vyoma branding (nav, hero, sticky TOC sidebar, footer, cookie banner) to match the main site.
- `999a2e5` — Added the `policies/` section and linked it into main site nav/footer.
- `df59987` — Deleted CNAME.
- `cbf0e2a` — Initial upload.

## Suggested next steps

- Activate Formspree (get real form ID) so the contact form actually delivers submissions.
- Decide on custom domain — either restore a CNAME + DNS setup, or drop that section from the README.
