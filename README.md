# Airius Internal Portal — Static

Static-HTML version of the portal, kept in this **`static/` subfolder** so it stays
separate from the Apps Script files in the parent folder (`..`) and doesn't interfere
with them.

## Why
Fast-loading, presentational pages for embedding in Google Sites, without the Apps
Script cold-start / sandbox latency. No backend.

## Approach
- **Pages**: plain `.html` files (no Apps Script `<? ?>` scriptlets).
- **Shared CSS**: one `assets/stylesheet.css`, hosted on a static CDN (e.g. GitHub +
  jsDelivr) and referenced with `<link rel="stylesheet" href="...">`, so every page
  shares one source. (Google Drive is NOT used — it doesn't serve CSS with the correct
  `text/css` MIME type.)
- **Backend-only features** (admin, user roles, changelog, per-page boot toggle) stay
  in the Apps Script project in the parent folder.

## Status
Scaffold only — the extracted stylesheet and the static pages come next.

## Structure
```
static/
  README.md
  assets/            # shared CSS / images
```

> Note: if you ever push the Apps Script project with `clasp`, add this `static/`
> folder to `.claspignore` so it isn't uploaded.
