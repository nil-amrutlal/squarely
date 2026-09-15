# Deploying Squarely

You didn't specify a host, so this bundle is set up for **Cloudflare Pages** — it's
free, needs no server, gives you a live URL in a couple of minutes, and pairs with
the "host-provided analytics" option you picked (Cloudflare's own Web Analytics,
zero code to add). If you'd rather use Netlify, GitHub Pages, or your own server,
the same five files work anywhere that serves static files — just skip to
"Other hosts" below.

## Files in this bundle

- `index.html` — the whole tool (fonts and JSZip load from Google Fonts /
  a bundled local copy — no build step needed)
- `jszip.min.js` — vendored locally so the zip download never depends on a
  third-party CDN being reachable
- `og-image.png` — the preview image shown when the link is shared on social/chat
- `robots.txt`, `sitemap.xml` — basic SEO plumbing

## Deploy to Cloudflare Pages (free)

1. Create a free account at dash.cloudflare.com if you don't have one.
2. Go to **Workers & Pages → Create → Pages → Upload assets**.
3. Drag this whole folder in (or a zip of it) and deploy. Cloudflare gives you
   a live URL immediately, like `squarely-abc.pages.dev`.
4. In the project's settings you can rename the subdomain (e.g. to
   `squarely.pages.dev`, if free) or attach a custom domain you own, under
   **Custom domains**.
5. To turn on free traffic analytics: open the project → **Analytics** tab →
   enable **Web Analytics**. No code changes needed for a Cloudflare Pages site.

## Before/after your final URL is known

Three files reference a placeholder domain (`https://squarely.pages.dev/`) —
`index.html` (canonical link + Open Graph/Twitter tags), `robots.txt`, and
`sitemap.xml`. Once you know your real live URL, do a find-and-replace of
`https://squarely.pages.dev` with that URL across those three files and
redeploy. This matters for SEO (canonical tags and sitemaps need to point at
the real address) but not for the tool itself, which works regardless.

## Other hosts

Netlify: drag the folder onto app.netlify.com/drop — same idea, instant URL.
GitHub Pages: push these files to a repo, enable Pages in repo settings.
Any own server: copy the files into your web root; no server-side code runs,
it's a fully static site.
