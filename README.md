# Insulin Dose Calculator (PWA)

Runs on iPhone and Android from the browser and installs to the home screen. Works offline after first load.

## Deploy to GitHub Pages (free)

    git init && git add . && git commit -m "insulin dose calculator"
    gh repo create insulin-dose --public --source=. --push
    gh api -X POST repos/{owner}/insulin-dose/pages -f build_type=workflow 2>/dev/null || true

Or in the repo web UI: Settings → Pages → Source: "Deploy from a branch" → main / (root).
Your URL will be https://<you>.github.io/insulin-dose/

Any static host works (Netlify, Cloudflare Pages, S3+CloudFront, OCI Object Storage static site). It must be HTTPS for install/offline to work.

## Install on the phone

- **Android (Chrome / Samsung Internet):** open the URL → ⋮ menu → "Add to Home screen" / "Install app".
- **iPhone (Safari only):** open the URL → Share → "Add to Home Screen".

## Test locally

    python3 -m http.server 8080      # then open http://localhost:8080

## Files

- index.html — the whole app (HTML + CSS + JS, no dependencies)
- manifest.json — install metadata (name, icon, colors)
- sw.js — service worker for offline caching
- icon.svg, icon-192.png, icon-512.png — app icons

Bump `CACHE` in sw.js (v1 → v2) whenever you change index.html so phones pick up the new version.

## Fonts

The dedication line is set in [Nunito Sans](https://github.com/Fonthausen/NunitoSans)
(`nunito-sans-500.woff2`, latin subset), self-hosted so the app keeps its
typography offline. Copyright 2016 The Nunito Sans Project Authors, licensed
under the SIL Open Font License 1.1 — see `OFL.txt`.
