# Vyoma Website

Static website for **Vyoma** — premium natural incense. Five pages, fully self-contained HTML (no build step, no server required).

## Files

| File | Page |
|------|------|
| `index.html` | Home |
| `fragrances.html` | Our Fragrances |
| `wellness.html` | Wellness Benefits |
| `wholesale.html` | Wholesale Program |
| `contact.html` | Contact |
| `shared.css` | Shared stylesheet (required by all pages) |
| `CNAME` | Custom domain for GitHub Pages |

All logo images are embedded as base64 inside the HTML files — no external image assets needed.

---

## Deploy to GitHub Pages (free hosting)

### First-time setup

1. **Create a new GitHub repository**
   - Go to [github.com/new](https://github.com/new)
   - Name it `vyoma-website` (or `yourusername.github.io` for a root domain)
   - Set to **Public**
   - Do NOT initialize with a README (you already have one)

2. **Initialize git in this folder**
   ```bash
   cd path/to/website
   git init
   git add .
   git commit -m "Initial Vyoma website launch"
   ```

3. **Push to GitHub**
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/vyoma-website.git
   git branch -M main
   git push -u origin main
   ```

4. **Enable GitHub Pages**
   - Go to your repo → **Settings** → **Pages**
   - Source: **Deploy from a branch**
   - Branch: `main` / `/ (root)`
   - Click **Save**
   - Your site will be live at `https://YOUR_USERNAME.github.io/vyoma-website/` within ~2 minutes

---

## Custom Domain (vyoma.com)

1. The `CNAME` file already contains `vyoma.com`
2. In GitHub Pages settings, enter `vyoma.com` under **Custom domain**
3. At your domain registrar (GoDaddy, Namecheap, etc.), add these DNS records:

   **For apex domain (vyoma.com):**
   | Type | Name | Value |
   |------|------|-------|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |

   **For www subdomain:**
   | Type | Name | Value |
   |------|------|-------|
   | CNAME | www | YOUR_USERNAME.github.io |

4. Check **Enforce HTTPS** in GitHub Pages settings once DNS propagates (~24 hours)

---

## Updating the site

After making any edits:
```bash
git add .
git commit -m "Update site content"
git push
```
GitHub Pages redeploys automatically within ~1 minute.

---

## Local preview

Open any `.html` file directly in your browser — no server needed. All assets are self-contained.

```bash
open index.html   # macOS
start index.html  # Windows
```
