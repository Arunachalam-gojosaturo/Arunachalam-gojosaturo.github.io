# Deploying this site on GitHub Pages

## 1. Create the right repo
For the site to live at the clean root URL `https://arunachalam-gojosaturo.github.io/`
(instead of a `/repo-name/` subpath), the repo **must** be named exactly:

```
Arunachalam-gojosaturo.github.io
```

Create it on GitHub (public, no README) if it doesn't exist yet.

## 2. Push these files
```bash
git clone https://github.com/Arunachalam-gojosaturo/Arunachalam-gojosaturo.github.io.git
cd Arunachalam-gojosaturo.github.io
# copy index.html, robots.txt, sitemap.xml into this folder
git add .
git commit -m "Launch portfolio site"
git push origin main
```

## 3. Enable Pages
Repo → **Settings → Pages** → Source: `Deploy from a branch` → Branch: `main` / `root`.
Your site goes live in 1–2 minutes at `https://arunachalam-gojosaturo.github.io/`.

If you'd rather host it under a different repo (e.g. `portfolio`), the site will
live at `https://arunachalam-gojosaturo.github.io/portfolio/` instead — in that
case update the `canonical`, `og:url`, and `sitemap.xml` URLs in `index.html`
to match.

## 4. Get it into Google
1. Go to [Google Search Console](https://search.google.com/search-console), add
   the property `https://arunachalam-gojosaturo.github.io/`.
2. Verify ownership — easiest method is the "HTML tag" option: it gives you a
   `<meta name="google-site-verification" ...>` tag; paste it into `index.html`'s
   `<head>`.
3. Submit `sitemap.xml` under **Sitemaps**.
4. Use **URL Inspection → Request indexing** on the homepage to speed things up.

Because your GitHub bio, README, and AUR packages already rank for
**"Arunachalam Arch Linux"**, this site reinforces the same identity (same
photo, same name, same keywords in the title/description/schema), which helps
Google connect the dots and rank it alongside your existing results rather
than starting from zero.

## 5. Why it's already optimized
- **Fast image load**: your GitHub avatar is pulled directly from GitHub's own
  CDN (`avatars.githubusercontent.com`) — no upload needed, always in sync if
  you change your GitHub photo.
- **Structured data**: a `Person` JSON-LD block tells Google exactly who you
  are, your job title, location, and links out to GitHub/LinkedIn/AUR — this
  is what can trigger a knowledge panel or rich result over time.
- **Meta tags**: title, description, Open Graph, and Twitter Card are all set
  so links shared on LinkedIn/WhatsApp/Twitter render with your photo and a
  proper preview card.
- **One canonical URL**: `<link rel="canonical">` avoids duplicate-content
  confusion between `www` and non-`www`, or trailing slashes.
- **Semantic HTML + alt text**: headings, `<nav>`, `<main>`, `<article>`, and
  descriptive `alt` text on the photo (rather than empty or filename-based
  alt) all feed image search and accessibility.

## 6. Optional: custom domain
If you buy a domain later, add a `CNAME` file (one line, your domain) to the
repo root and point your DNS `A`/`ALIAS` records at GitHub Pages per
[GitHub's custom domain docs](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site).
