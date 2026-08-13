# Match Desk — Internship Allocation Engine (PWA)

A installable, offline-capable Progressive Web App version of Match Desk.

## What's included

```
matchdesk-pwa/
├── index.html          # The app (single-page, with PWA tags added)
├── manifest.json        # App name, icons, theme colors, display mode
├── service-worker.js    # Offline caching (cache-first for app shell)
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   └── icon-maskable-512.png
└── README.md
```

## Deploy on GitHub Pages

1. Create a new repository (or use an existing one) and push these files to it,
   keeping them at the **repo root** (or in a `/docs` folder if you prefer that
   workflow):

   ```bash
   git init
   git add .
   git commit -m "Add Match Desk PWA"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

2. In the repo, go to **Settings → Pages**, and under "Build and deployment"
   set **Source** to "Deploy from a branch", pick the `main` branch and the
   root (`/`) folder (or `/docs` if that's where you put the files).

3. Wait a minute for GitHub Pages to build, then visit the URL it gives you,
   e.g. `https://<your-username>.github.io/<your-repo>/`.

4. Open that URL on desktop Chrome/Edge or mobile Chrome/Safari — you should
   see an "Install app" prompt (or "Add to Home Screen" on iOS/Safari via the
   Share menu). Once installed it works offline after the first load.

## Notes

- `service-worker.js` caches the app shell (HTML, manifest, icons) on
  install, and caches Google Fonts / the XLSX CDN script on first fetch so
  the app keeps working without a connection afterward.
- If you rename the repo or serve the app from a subpath, no changes are
  needed — all paths in `manifest.json`, `service-worker.js`, and
  `index.html` are relative.
- To update the app later, bump `CACHE_NAME` in `service-worker.js` (e.g.
  `match-desk-v2`) so returning users get the new version instead of a
  stale cached copy.
- Icons were generated to match the app's existing violet/coral/sun brand
  gradient and "M" mark — swap them out in `icons/` if you'd like a custom
  logo instead.
