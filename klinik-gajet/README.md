# Klinik Gajet

A free Jekyll site, built to run on **GitHub Pages** (RM0/month hosting).
Niche: iPhone/iPad/Mac care content for a Malaysian audience (battery
health, iCloud/storage confusion, accessories), monetized through
**display ads (Google AdSense)** and **affiliate links (Shopee, etc.)**.

Content is written in a mixed English + Bahasa Malaysia voice, structured
around a "clinic" concept — each article states a **Simptom** (symptom),
**Diagnosis**, and **Rawatan** (treatment), which doubles as a genuinely
useful structure for myth-busting content and as this site's visual
identity (see "Design notes" below).

---

## 1. Put this on GitHub Pages (no cost)

1. Create a new **public** GitHub repo.
   - If you name it exactly `yourusername.github.io`, the site publishes
     at `https://yourusername.github.io/`.
   - If you name it anything else (e.g. `klinik-gajet`), it publishes at
     `https://yourusername.github.io/klinik-gajet/` — in that case set
     `baseurl: "/klinik-gajet"` in `_config.yml`.
2. Push everything in this folder to that repo's `main` branch.
3. On GitHub: **Settings → Pages → Build and deployment → Source** →
   choose **"Deploy from a branch"** → branch `main`, folder `/ (root)`.
4. Wait 1–2 minutes, then visit the URL GitHub shows you.

GitHub Pages builds Jekyll sites automatically — you do **not** need to
run any build command yourself for this to work.

### Testing locally before you push (optional but recommended)

```bash
bundle install
bundle exec jekyll serve
# then open http://localhost:4000
```

You'll need Ruby installed. If you don't want to install Ruby, you can
skip local testing and just check the live GitHub Pages URL after each
push — it takes about a minute to rebuild.

### Custom domain (optional)

If you later buy a domain (e.g. `klinikgajet.my`), add a file named
`CNAME` in the root containing just the domain name, then point your
domain's DNS to GitHub Pages per
[GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
Update `url:` in `_config.yml` to match.

---

## 2. Fill in the real business details

Before this looks "live-ready," update:

- `_config.yml` → `url`, `baseurl`
- `privacy.md` → this is a **template**. Read it and adjust before you
  submit to AdSense — they check this page.
- `disclosure.md` → adjust wording if your monetization setup changes
  (e.g. if you add more affiliate networks beyond Shopee).
- Replace the Shopee links in `_posts/*.md` (`prescription:` front
  matter and any inline links) with your **real Shopee affiliate
  links** — the ones in this starter are placeholders pointing at
  `https://shopee.com.my/`.
- Swap the `<link rel="icon" href="data:,">` line in
  `_layouts/default.html` for a real favicon once you have one.

---

## 3. Writing a new article

Add a new file to `_posts/` named `YYYY-MM-DD-your-title-slug.md`:

```yaml
---
title: "Your Article Title"
ward: battery   # one of: battery, storage, accessories, screen
symptom: "One-line description of the problem/complaint."
diagnosis: "One-line description of what's actually going on."
treatment: "One-line description of the fix." # optional
verdict: myth   # optional: "myth" or "fact" — shows a small tag
excerpt: "1-2 sentence summary used on the homepage card and in <meta description>."
prescription:  # optional — this is where affiliate product recommendations go
  - name: "Product name (Shopee)"
    url: "https://your-real-shopee-affiliate-link"
    note: "why you're recommending it"
---

Your article content in Markdown goes here.
```

The `ward` field controls which category page the post appears on and
which accent color its card gets. If you want a fifth category later,
add it to the `wards:` list in `_config.yml` and create a matching
`ward/<slug>/index.html` page (copy an existing one as a template).

---

## 4. Turning on real ads (Google AdSense)

1. Apply at [adsense.google.com](https://adsense.google.com) — you'll
   need a live URL and content up (this repo already has enough pages
   and a privacy policy to apply, but approval is Google's call).
2. Once approved, Google gives you a snippet like:
   ```html
   <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXX"
   crossorigin="anonymous"></script>
   ```
   Paste that once in `_layouts/default.html`, right before `</head>`.
3. For each ad unit Google gives you, replace the placeholder div in
   `_includes/ad-slot.html` with your `<ins class="adsbygoogle">` unit
   code — or just paste the ad unit code directly wherever
   `{% include ad-slot.html %}` is called, if you want different ad
   units in different spots.

Until you're approved, the dashed placeholder boxes show where ads will
go, so the layout doesn't look broken or shift around later.

---

## 5. Affiliate links (Shopee &amp; others)

- Get your affiliate link for each product from the
  [Shopee Affiliate Program](https://affiliate.shopee.com.my/) (or
  whichever program you're approved for).
- Put the real link in a post's `prescription:` front matter (see
  section 3) — these render in the "Preskripsi" box at the end of the
  article, styled as a product recommendation rather than a banner ad.
- Every prescription link already has `rel="sponsored nofollow"` set,
  which is what Google recommends for paid/affiliate links — don't
  remove it.
- Keep using the `disclosure.md` page and don't remove the disclosure
  note under the Preskripsi box — Shopee, Google, and Malaysian
  consumer-protection norms all expect affiliate relationships to be
  disclosed, and it keeps reader trust.

---

## 6. Design notes

- Fonts: **Fraunces** (headlines/labels) + **IBM Plex Sans** (body),
  loaded from Google Fonts in `_layouts/default.html`.
- Colors and all other design tokens live at the top of
  `assets/css/style.css` as CSS custom properties — change `--teal`,
  `--mustard`, `--alert`, `--bg`, etc. there to re-theme the whole site.
  The teal, mustard, and alert colors also double as the color-coding
  for the Battery / Storage / Accessories wards, so if you rename or
  reorder wards in `_config.yml`, make sure the `color:` field for each
  still matches one of `teal`, `mustard`, or `alert`.
- The "chart" (Simptom / Diagnosis / Rawatan) at the top of each article
  and the "Preskripsi" box are the site's signature visual devices —
  they're what make the affiliate recommendations feel like part of the
  content instead of a bolted-on ad.

---

## 7. What's next / ideas not built yet

- An actual logo/favicon (currently text-only wordmark).
- A search box (fine to skip until you have 20+ posts).
- A newsletter signup, if you want an owned audience beyond SEO/social.
- Structured data (`jekyll-seo-tag` is already enabled, which covers
  the basics — Article schema markup would be a next step for richer
  Google search results).
