# bragadaniel14.github.io

Personal website and mini-blog source for GitHub Pages.

## Local structure

- `index.md`: home page (portfolio, contact, CV link)
- `mini-blog.md`: blog index split into `tech` and `christian`
- `ml-materials.md`: curated ML tutorials/resources
- `_posts/`: markdown blog posts
- `assets/css/site.css`: global styling
- `assets/Resume_Spring_2026_latest.pdf`: CV download file

## Post workflow (markdown)

1. Add a file in `_posts/` with name `YYYY-MM-DD-title.md`
2. Use front matter like:

```yaml
---
title: "Post title"
date: 2026-03-03
categories: [tech]
---
```

Use `categories: [tech]` or `categories: [christian]` to place the post in the correct tab section.

## Analytics (optional)

In `_config.yml`, set:

```yaml
analytics_plausible_domain: "your-domain.com"
```

If blank, no analytics script is loaded.

## GitHub Pages deployment

1. Create GitHub repo `bragadaniel14.github.io` under account `bragadaniel14`.
2. Push this repo:

```bash
git push -u origin main
```

3. In GitHub repository settings, ensure Pages is enabled from `Deploy from a branch` -> `main` (root).
