# Ponnavaikko — Jekyll Site (Minimal Mistakes) — UTF-8 FIX

## What’s fixed
- Converted legacy Windows-1252 HTML files to **UTF‑8** (Liquid error resolved)
- Consolidated content into Markdown pages and removed redundant legacy HTML includes
- Disabled pagination warning in `_config.yml`
- Added `faraday-retry` gem to silence Faraday middleware notice

## Local preview
```bash
bundle install
bundle exec jekyll serve
# visit http://127.0.0.1:4000
```

## Deploy on GitHub Pages
- Push this repo to GitHub (ideally named `ponnavaikko.github.io`).
- In Settings → Pages, publish from `main` (root).
- Add your custom domain `ponnavaikko.com` in Pages settings and set DNS.
