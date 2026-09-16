# flightec-staging

Static, single-file staging build of the FLIGHTEC marketing site. The whole
site — HTML, CSS and JS — lives in `index.html`, so there's nothing to build
or install; GitHub Pages just serves it as-is.

## Deploy to GitHub Pages

1. Create a new GitHub repository named **`flightec-staging`** (the repo
   name becomes part of the URL, so keep it exactly this if you want the
   `flightec-staging` URL below).
2. Add `index.html` (from this folder) to the repo — either drag-and-drop it
   in the GitHub web UI ("Add file" → "Upload files") or via git:

   ```bash
   git clone https://github.com/<your-username>/flightec-staging.git
   cd flightec-staging
   cp /path/to/index.html .
   git add index.html README.md
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
redeploys automatically on every push to the Pages branch. No other files
or build steps are involved.

## Notes

- This is a **staging** build for internal review and client sign-off, not
  the final production domain.
- The page is fully self-contained (fonts load from Google Fonts over
  HTTPS; everything else — CSS, JS, images — is inlined), so it will render
  identically wherever it's hosted.
- Dark mode is the default theme; the toggle in the header switches to
  light.
