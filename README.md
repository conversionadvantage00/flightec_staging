# flightec-v2 (PDF restructure — now replacing the live site)

Static build of the **PDF-restructured** FLIGHTEC site: new nav, services
split into "Above" (airborne) and "Below" (wireline logging) groups, a new
"Where We Operate" section, and an expanded contact form. Same visual
design system (fonts, colors, dark/light theme, buttons, cards, animations)
as the previous live site — only the copy, information architecture and
section list changed, per the client's PDF.

**At your request, this version now replaces the previous live site** at
the same URL/repo it was already on — `flightec_staging` —
`https://conversionadvantage00.github.io/flightec_staging/`. The
`index.html` in this delivery has that exact URL baked into its
canonical link and Open Graph/Twitter share tags.

- `index.html` — the production-style build (no editor toolbar). Upload
  this to the `flightec_staging` repo root, overwriting the existing one.
- `README.md` — this file.
- `og-share.jpg` — the link-preview image (WhatsApp, iMessage, Slack,
  etc. read this via the og:image tag). Upload it to the repo root too,
  overwriting the existing `og-share.jpg`.
- `flightec-v2-editable.html` (sent earlier) — a working-draft copy with
  an in-browser edit toolbar (click text to edit, export a clean HTML
  copy) for reviewing and tweaking copy. Not meant to go live anywhere.

## Deploy to GitHub Pages (replacing the current live site)

1. Open the existing `flightec_staging` GitHub repository.
2. Upload `index.html` and `og-share.jpg` to the repo root via "Add file
   → Upload files" (not the inline text editor — it has previously
   corrupted a file on this project), confirming you want to replace the
   existing files with the same names.
3. GitHub Pages will redeploy automatically from the same **Settings →
   Pages** configuration already in place — no need to change anything
   there.
4. The site updates in place at
   `https://conversionadvantage00.github.io/flightec_staging/` within a
   minute or two.

## What's changed vs. the live site

- Page order: Hero → About ("Who We Are") → **Our Approach** (pillars,
  unchanged, same place as the live site) → Services → **How We Work**
  (process steps, unchanged, same place as the live site) → **Where We
  Operate** (new) → Contact.
- Services restructured into two labeled groups, "Above" (airborne) and
  "Below" (wireline logging), using the same classic card design as the
  live site — hover photo, heading, one supporting line and a "Learn More"
  button that opens the same popup modal, just re-grouped and re-worded per
  the client's PDF. Comparison callouts and visual-to-be-added placeholders
  from the PDF appear inside that popup, not on the card itself.
- New "Where We Operate" section listing current approved operating areas
  (South Africa, Namibia, Botswana, Lesotho).
- Contact form expanded to 10 fields (name, company, email, phone, project
  location, service required, survey area, project stage, timeline,
  objective) plus an additional-information textarea.
- The editable working-draft file now has dedicated, always-visible Fit
  and Position controls for the hero image's desktop and mobile versions
  separately (previously only whichever one was on-screen could be
  adjusted).
- Your copy edits from the exported working draft are applied: the hero
  headline is now "Above. Below. Beyond." (colored the same gold accent as
  the original site's hero, per your request) with "Precise, high-resolution
  data for mining and mineral exploration." as the small eyebrow line above
  it, and "Airborne Geophysical Surveys and Mapping." / "Wireline Logging"
  are capitalized as you set them.
- Every photo panel in the editable file — including the three Below
  services that didn't have real photography yet (Optical Borehole Imaging,
  Magnetic Susceptibility Logging, Natural Gamma Ray Logging) — now has an
  "Upload Photo…" button, so you can drop in a real image for any slot,
  then use Fit/Position to adjust it. Uploaded photos are embedded directly
  in the exported HTML file, so nothing else needs to be sent anywhere.
- Each "Learn More" popup can now show a second, supporting image beneath
  the copy (above the button) in addition to the existing hero photo. This
  is wired up for Magnetic Surveys, Radiometric Surveys and Optical
  Borehole Imaging. Clicking that image opens it full-size in a lightbox.
- The Optical Borehole Imaging popup no longer shows the old "Visual to be
  added" placeholder now that it has a real supporting image.
- The contact form now only shows Name, Company, Email, Contact Number,
  Project Location and Service Required up front. The remaining four
  fields (Approximate Survey Area, Project Stage, Required Timeline,
  Project Objective) stay hidden until a service is selected from the
  dropdown, so the form doesn't look as long on first glance.

## Need one more image from you

You asked for a supporting image in four popups — Magnetic Surveys,
Radiometric Surveys, Topographic Surveys and Optical Borehole Imaging —
but only three distinct new photos came through with that message. I
matched them by content:

- Magnetic Surveys ← the smooth, colorful anomaly-style map
- Radiometric Surveys ← the more grainy/textured colorful map
- Optical Borehole Imaging ← the sepia core/log strip composite

That leaves **Topographic Surveys** without a supporting image for now —
its popup currently shows just the hero photo and copy, no second image.
Could you send the one meant for that slot? And flag it if I matched any
of the other three to the wrong service.

## Known open items — need your input

- **A likely typo in the client's PDF**: the About section copy read
  "...build a clear understanding subsurface..." — I've inserted "of the"
  ("...understanding of the subsurface...") since that reads as a dropped
  word rather than intentional phrasing. Flag if you'd rather match the
  PDF text exactly, typo and all.
- **Automated email routing**: the contact form currently opens the
  visitor's own email client via a `mailto:` link addressed to
  `info@flightec.co.za` — a static HTML file can't route to a specific
  person's inbox or send an automatic acknowledgement reply. If the brief
  calls for that, I'd need either a real staff email address to point the
  mailto at, and/or a backend form service (e.g. Formspree, Netlify Forms)
  to handle real submissions and auto-replies.
- **Structural interpretation**: the PDF's own layout drops Pillars/Process
  and adds Where We Operate, so I followed the PDF's structure while
  keeping the *visual design system* identical — flagging this since your
  instruction emphasized keeping "structure... exactly the same," in case
  you meant something narrower.

## Notes

- No credentials or GitHub deploy actions were performed on your behalf —
  same as the live site, you'll need to do the actual GitHub upload
  yourself.
