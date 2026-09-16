# flightec-staging

Static staging build of the FLIGHTEC marketing site. All the HTML, CSS and
JS lives in `index.html` (nothing to build or install — GitHub Pages just
serves it as-is), plus one extra file, `og-share.jpg`, used for link-preview
thumbnails (see below).

## Deploy to GitHub Pages

1. Create a new GitHub repository named **`flightec-staging`** (the repo
   name becomes part of the URL, so keep it exactly this if you want the
   `flightec-staging` URL below).
2. Add **both** `index.html` and `og-share.jpg` (from this folder) to the
   repo root — either drag-and-drop them in the GitHub web UI ("Add file" →
   "Upload files", you can select multiple files at once) or via git:

   ```bash
   git clone https://github.com/<your-username>/flightec-staging.git
   cd flightec-staging
   cp /path/to/index.html /path/to/og-share.jpg .
   git add index.html og-share.jpg README.md
   git commit -m "Staging build"
   git push
   ```

3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Under **Branch**, choose `main` (or whichever branch you pushed to) and
   folder `/ (root)`, then **Save**.
6. GitHub will publish the site within a minute or two at:

   ```
   https://<your-username>.github.io/flightec-staging/
   ```

   (Check the Pages settings screen — it shows the live URL once the first
   deployment finishes.)

## Updating the site later

Replace `index.html` with a newer export and push again — GitHub Pages
redeploys automatically on every push to the Pages branch. You only need to
re-upload `og-share.jpg` if the share image itself changes.

## Link previews (WhatsApp, iMessage, Slack, etc.)

`index.html` has Open Graph / Twitter Card meta tags pointing at
`og-share.jpg`, hardcoded to the absolute URL
`https://conversionadvantage00.github.io/flightec_staging/og-share.jpg`.
That's what makes a thumbnail image, title and description show up when the
link is pasted into WhatsApp, iMessage, Slack, LinkedIn, etc.

Two things to know:

- **The image must be at that exact URL** — `og-share.jpg` sitting in the
  repo root, same repo name (`flightec_staging`). If the repo or file name
  ever changes, the meta tags in `index.html` need to be regenerated to
  match (ask Claude to rebuild with the new URL).
- **Chat apps cache the preview.** The very first time a link is shared
  from a given domain, WhatsApp/iMessage/etc. fetch and cache the image —
  so if you test the link before `og-share.jpg` is live, or change the
  image later, you may keep seeing the old (or no) preview in that chat
  thread even after the file is fixed. A fresh chat, a different contact,
  or a cache-busting query string on the link (e.g. adding `?v=2` to the
  URL you paste) usually forces a re-fetch.

## Notes

- This is a **staging** build for internal review and client sign-off, not
  the final production domain.
- The page is fully self-contained (fonts load from Google Fonts over
  HTTPS; everything else — CSS, JS, images — is inlined), so it will render
  identically wherever it's hosted.
- Dark mode is the default theme; the toggle in the header switches to
  light.
