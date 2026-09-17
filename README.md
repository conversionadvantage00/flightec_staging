# flightec-v2 — GitHub Pages deploy

Static build of the FLIGHTEC site (single self-contained `index.html`, no
external files needed except the previously-uploaded `og-share.jpg`, which
does not need to change with this update). No AI/builder tooling is
present in this file — it is pure production HTML/CSS/JS.

- `index.html` — the production build. Upload this to the
  `flightec_staging` repo root, overwriting the existing one.
- `README.md` — this file.

## Deploy to GitHub Pages

1. Open the `flightec_staging` GitHub repository
   (`https://conversionadvantage00.github.io/flightec_staging/`).
2. Go to the repo root and use **Add file → Upload files** (not the
   inline text editor — it has previously corrupted a file on this
   project).
3. Drag in `index.html`, confirming you want to replace the existing
   file with the same name.
4. Commit the upload. GitHub Pages redeploys automatically from the
   existing **Settings → Pages** configuration — nothing else to change.
5. The live site updates in place within a minute or two.

## What's in this build

- Hero: "Above. Below. Beyond." with "Beyond." in the accent colour.
- Every "Discuss Your Project" button scrolls to the contact form.
- Below-section service cards are fully clickable (no separate "Learn
  More" button) and open a detail popup.
- Fixed, contour-line background texture behind all content sections,
  with separate light/dark-theme images.
- Contact form: Name, Company, Email, Contact Number, Project Location,
  Service Required (a closed dropdown that opens into a multi-select
  checklist), Additional Information. Submitting opens the visitor's
  email client addressed to **nathan.archer@flightec.co.za** with the
  form details pre-filled as the subject/body (a static HTML file can
  only hand off to the visitor's own mail client — it can't silently
  send mail itself or auto-acknowledge the sender; that would need a
  form backend such as Formspree or Netlify Forms).
- Contact section also lists Nathan Archer (Sales Manager) directly,
  with clickable email and phone links.
- "How We Work" is a 4-step, icon-based sequence where the connecting
  line and each step light up as you scroll — it's scroll-linked (tied
  to scroll position, not a one-off animation), unwinds cleanly if you
  scroll back up, and works the same way on mobile.
- Two custom line-art location cards replace the old Google Maps embed:
  Western Cape (pulsing pin on Knysna) and Namibia (pulsing pin on
  Windhoek), in the accent colour, styled to match the rest of the
  site's icons.
- Rounded corners (10–15px) throughout on cards, pillars and the contact
  form panel.
- Footer logo is the colour version.

## Open item — not yet acted on

The colour footer logo has lower contrast against the dark footer
background in both themes than the previous white logo did. Let us know
if you'd like a light backdrop behind it there, or the white version
kept just for the footer, and it'll be a quick follow-up.

## Notes

No credentials or GitHub deploy actions were performed on your behalf —
you'll need to do the actual upload yourself via the steps above.
