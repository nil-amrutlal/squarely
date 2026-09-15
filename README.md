# Squarely

A free, browser-only tool that batch-converts photos to perfect 1:1 squares.
Drop in a folder of photos, pick **crop to fill** or **pad to fit**, and download
the whole set back as a single `.zip`. Nothing is ever uploaded — every photo is
read, resized, and zipped locally in the visitor's own browser.

## Features

- **Pad to fit** — adds a white border around the shorter side, so the whole
  photo stays visible with nothing cut off.
- **Crop to fill** — trims the longer side, centered on the photo, so the
  square has no border.
- Drag-and-drop or click-to-browse, batch of any size.
- Live thumbnail previews with each photo's original and squared dimensions.
- One-click download of the entire batch as a `.zip`.
- 100% client-side: no server, no accounts, no photo ever leaves the device.

## Running it locally

No build step or install needed. Just open `index.html` in a browser, or serve
the folder with any static file server, e.g.:

```
npx serve .
```

## Files

| File             | Purpose                                              |
|------------------|-------------------------------------------------------|
| `index.html`     | The entire app — markup, styles, and logic            |
| `jszip.min.js`   | Vendored zip library (no external CDN dependency)      |
| `og-image.png`   | Social/link preview image                             |
| `robots.txt`     | Search-engine crawling rules                           |
| `sitemap.xml`    | Search-engine sitemap                                  |

## Tech notes

- Squaring happens via the HTML canvas API (`drawImage` + `toBlob`), entirely
  in memory.
- Zipping happens via a locally bundled copy of [JSZip](https://stuk.github.io/jszip/).
- Fonts: Fraunces, IBM Plex Sans, and IBM Plex Mono, loaded from Google Fonts.

## Before going live

`index.html`, `robots.txt`, and `sitemap.xml` reference a placeholder domain
(`https://squarely.pages.dev/`). Swap that for your real live URL once you know it.
