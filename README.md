# Vyoma Website

Static website for **Vyoma Wellness Group**: Vyoma Incense (five signature fragrances in a 5-Pack and a 10-Pack Starter Kit) and Vyoma Wellness (the nightly ritual app, coming soon). Plain HTML and CSS: no build step, no server.

> This repo is **public** and every file in it is served on the live site. Business plans, pitch decks, costs and strategy docs live in a separate private repo. Never commit them here.

## Files

| File | Page |
|------|------|
| `index.html` | Home: the group, both brands, the collection |
| `fragrances.html` | Vyoma Incense: five fragrance profiles, packs, burn-with-care directions |
| `wellness.html` | Vyoma Wellness: the app, the four-step ritual, waitlist form |
| `wholesale.html` | Wholesale program for stores and studios |
| `contact.html` | Contact form (Formspree) and FAQ; `?type=wholesale\|order\|gifting\|samples\|app` pre-selects the enquiry type |
| `policies/` | Legal center plus terms, privacy, refund, shipping and accessibility policies |
| `shared.css` | Shared stylesheet (palette, nav, footer, v3 components) |
| `assets/` | Web-sized logos used by every page |
| `_headers` | Response headers for Cloudflare Pages |
| `Vyoma_*.png` | Full-size source logos (not referenced by pages) |

Forms post to Formspree (`https://formspree.io/f/maqrjwyo`). The waitlist form on `wellness.html` sends `inquiry_type = Vyoma Wellness app waitlist`.

## Hosting

The site currently runs on GitHub Pages from `main` (root) at `https://harshaeeb.github.io/vyoma-website-c/`. For Cloudflare Pages, use: framework preset **None**, build command **empty**, output directory **`/`**, production branch **`main`**. See DEVLOG.md for details.

## Local preview

Open any `.html` file directly in a browser.
