# flightec-v2 — GitHub Pages deploy

Static build of the FLIGHTEC site. **This round changes the file
structure** — real photos now live as separate files in an `img/` folder
next to `index.html`, instead of being embedded inside the HTML. No
AI/builder tooling is present in this build — it is pure production
HTML/CSS/JS.

**Important correction this round:** the version I'd been iterating on
had drifted from the version you actually wanted live — it was missing
the interactive hero mouse/touch reveal effect, was showing placeholder
gradients instead of real photos on the three "Below" (Wireline Logging)
service cards, and was using two separate Google Maps iframes instead of
the single Africa map with custom Windhoek/Knysna pins. I've rebuilt
this round directly from the correct file you sent through, applying the
same favicon/JSON-LD/dark-theme/image-extraction work on top of *that*
one instead. Flagging honestly: my working source files (the ones I use
to keep generating future rounds) were out of sync with this correct
version, so I've treated your upload as the new baseline going forward —
worth double-checking the next round's changes extra carefully since
this was a real gap on my end, not just a mix-up on yours.

Typeface: the site uses Aptos (the brand's own font) throughout — Bold
for all headings/titles, Regular for everything else — embedded directly
in the file rather than loaded from Google Fonts, so there's no external
font request for that.

- `index.html` — the production build. Upload this to the
  `flightec_staging` repo root, overwriting the existing one.
- `img/` — **new folder, 18 files** — every real photo the site uses,
  plus the two logo files. Upload the whole folder to the repo root,
  alongside `index.html` (see steps below). Also provided zipped
  (`flightec-v2-live-img-folder.zip`) as a fallback if dragging a folder
  doesn't work smoothly in your browser.
- `og-share.jpg`, `logo-square.png` — unchanged from before, still need
  to exist at the repo root (you already uploaded these; nothing to redo
  there).
- `README.md` — this file.

## Deploy to GitHub Pages

1. Open the `flightec_staging` GitHub repository
   (`https://conversionadvantage00.github.io/flightec_staging/`).
2. Go to the repo root and use **Add file → Upload files** (not the
   inline text editor — it has previously corrupted a file on this
   project).
3. Drag in `index.html`, confirming you want to replace the existing
   file with the same name — same as every previous round.
4. **New this round:** also drag in the whole `img` folder (not its
   contents individually — drop the folder itself onto the upload area).
   Modern GitHub's upload page accepts a dropped folder and recreates it
   at `img/` in the repo automatically. If your browser doesn't let you
   drag a folder (some browsers only accept files), unzip
   `flightec-v2-live-img-folder.zip` first and drag the resulting `img`
   folder in instead — same result.
5. Commit the upload (both `index.html` and the new `img/` folder can go
   in the same commit). GitHub Pages redeploys automatically from the
   existing **Settings → Pages** configuration — nothing else to change.
6. The live site updates in place within a minute or two. Do a quick
   pass afterward: hero photo shows immediately, and the About/Services
   photos should fade in as you scroll (that's expected — see below).

## What's in this build

- **Images extracted out of the HTML into real files (the big one this
  round).** Previously every photo was embedded directly inside
  `index.html` as base64 text, which made that one file **7.7MB**. That's
  now down to **~300KB** — a 96% reduction — with the photos living
  instead as 16 ordinary `.jpg` files (plus 2 logo `.png` files) in the
  new `img/` folder. Why this matters in practice: the browser can now
  fetch, cache and load each image independently instead of parsing one
  giant blob before showing anything, page loads noticeably faster
  (especially on mobile/slower connections), and repeat visits reuse
  cached images instead of re-downloading the whole page every time.
  - The hero photo loads immediately (it's above the fold on first
    paint), same as before.
  - Every other real photo — the About Flightec row images, the
    Magnetic/Radiometric/Topographic service card photos, and the
    "Regional vs Flightec" comparison images inside each popup — now
    **lazy-loads**: it only downloads once you scroll near it (or, for
    the popup comparison images, the moment you actually open that
    popup). Most visitors who don't open every popup will never download
    those images at all, which is a further real saving beyond the raw
    file-size number above.
  - Also deleted a genuinely dead ~230KB background texture image that
    was left over from before the site went dark-mode-only — it was
    being fully hidden by a later CSS rule and could never actually
    render, so removing it is a pure size win with zero visual change.
  - The still-placeholder "Below" group images (Optical Borehole
    Imaging, Magnetic Susceptibility Logging, Natural Gamma Ray Logging)
    are unaffected — those are CSS gradients, not photos, so there was
    nothing to extract there.
- **Favicon added.** There wasn't one before (blank browser tab icon).
  Since there's no dedicated square icon-only mark among the logo assets
  you've sent through (the wordmark is wide, not square), this is a
  generated placeholder — a bold "F" in the brand's blue-to-navy gradient
  on a dark rounded square. Swap it for the client's real icon mark the
  moment they have one; it's a quick change.
- **Structured data added** (an `application/ld+json` Organization block)
  — helps Google show the logo/knowledge-panel style results, and lists
  the LinkedIn page. Costs nothing at runtime.
- **Fixed a flash-of-light-theme bug**: the `<html>` tag was still
  statically set to `data-theme="light"` even though the site always
  loads dark (a script flips it after load) — on a slow connection this
  could show a brief flash of the light background first. Now set to
  `"dark"` from the start.
- **New file: `logo-square.png`.** A square-padded version of the real
  logo, used only by the structured-data block above (schema.org wants a
  roughly square logo image, not the wide 1200×630 social-share banner).
  Upload it to the repo root alongside `og-share.jpg` — it's the only new
  file this round adds.
- **Not yet done, deliberately held back**: `robots.txt` and
  `sitemap.xml` need the final production domain to be correct, so
  they're ready to generate the moment that's confirmed — see the Go-Live
  guide. Same for updating the `canonical`/`og:url`/`og:image` tags away
  from the GitHub Pages URL.
- **Services cards — "Learn More" alignment and refined type**: the
  "Learn More" link now sits flush against the bottom of every "Above"
  card, lined up across Magnetic, Radiometric and Topographic regardless
  of how much body copy each one has. The card title and body copy also
  got a small typographic polish (bolder heading, tighter letter-spacing,
  slightly more line-height on the body) so they read a bit less plain.
- **About Flightec — "03 Data Processing"** now shows your new aerial
  elevation/point-cloud photo as its background image, set to cover.
- **Where We Operate**: added a "We Operate From" headline above the two
  map cards, and a small label under each — "Head Office" under
  Windhoek, "Research & Development" under Knysna.
- **LinkedIn**: added a LinkedIn icon in the footer, linking to
  https://www.linkedin.com/company/flightecza/ in a new tab.
- **Hero → About Flightec transition**: the hard line where the hero
  banner used to cut off into the "About Flightec" section below it is
  gone — the bottom of the hero now fades smoothly into that section's
  background colour instead.
- **Header button text colour**: "Schedule a Call" in the header pill is
  now white, not the dark charcoal it was rendering as.
- **Services cards (Capability section) are now fully clickable**: for
  the three "Above" cards (Magnetic, Radiometric, Topographic Surveys),
  clicking anywhere on the card opens its popup, not just the "Learn
  More" link — the link is still there as a visual cue. The "Below"
  card (Wireline Logging) is unchanged and still non-interactive, per
  the earlier client request.
- **Services cards are about 25% larger**: more padding, taller cards,
  bigger heading/body type, and a touch more breathing room between
  them in the grid — on both desktop and mobile.
- **Radiometric Surveys popup now shows 4 images instead of 2**: Uranium
  and Thorium in the first row, Potassium and Total Count in the second
  (all four are your newly supplied channel maps) — 2x2 on desktop,
  stacked in that same order on mobile.
- **Magnetic Surveys and Topographic Surveys service card images swapped**:
  Magnetic Surveys now shows the magnetometer/sensor-on-grass photo, and
  Topographic Surveys now shows the drone-in-flight photo (the reverse of
  the previous round).
- **Dark mode only**: the light/dark toggle has been removed from the
  header entirely — the site now always loads in dark theme, on every
  page and every device. (The light-theme CSS variables are still in the
  stylesheet as inert, unused code rather than deleted outright, in case
  you ever want them back — just say so.)
- **Header button**: now reads "Schedule a Call" instead of "Discuss
  Your Project" (both the desktop pill button and the mobile menu's
  version) — still scrolls to the contact form.
- **Header logo**: increased 25% (22px → 28px desktop, 19px → 24px
  mobile).
- **Header background**: now a near-white, still-translucent frosted
  panel (was a cooler grey-tinted glass before).
- **Hero banner**: replaced with your new image on both desktop and
  mobile, and the dark gradient overlay on top of it is now 50% lighter,
  since the photo itself is already quite dark.
- **Colour swap**: every use of `#8bb3cc` across the site (nav hover
  states, the hero eyebrow/accent text, ghost-button hover, the About
  section's active-tag highlight, and the "Learn More" links on the
  Above service cards) has been replaced with `#3e80aa`. It won't be
  used again going forward.
- **About Flightec — "01 Field Operations"** now shows your field photo
  (the drone laid out on its landing sheet with the support vehicle and
  crew) as its background image, swapped up to the higher-resolution
  version you sent through afterward.
- **Where We Operate** location cards are now live Google Maps embeds
  instead of the custom line-art maps — Windhoek on the left, Knysna on
  the right on desktop, stacked on mobile. (Note: the maps won't render
  in the claude.ai live-preview link above, since that sandbox blocks
  embedded frames from other sites — they'll load normally once this is
  live on your actual domain.)
- **Topographic Surveys popup** now has your real comparison images —
  Standard regional elevation data on the left (top on mobile), your
  Flightec DSM on the right (below it on mobile) — with the existing
  captions, closing line and "Discuss Your Mapping Requirements" button
  all unchanged, since they already matched what you sent through. All
  three "Above" popups (Magnetic, Radiometric, Topographic) are now on
  real photography.
- **Magnetic Surveys and Topographic Surveys service cards** (the small
  thumbnail cards in the Capability grid) now use real photography —
  Magnetic Surveys shows the drone-in-flight photo, and Topographic
  Surveys shows the magnetometer/sensor-on-grass photo. The Topographic
  Surveys **popup's** two comparison images (left/right) are still
  placeholders, same as before.
- **Contact section**: removed the "Discuss Your Project" button above
  Nathan Archer's details (the one further up, next to the form, is
  unaffected), and removed the "Opens your email client with these
  details filled in" note under the Send Message button.
- **Schedule a Call**: added a link under Nathan Archer's phone number.
  It currently points nowhere (`href="#"`) — send through the actual
  Calendly/booking link and I'll wire it in, a one-line change.
- **Magnetic Surveys popup** now opens with your combined hook + body
  copy: "Reveal geological structures and magnetic anomalies in greater
  detail. Flightec acquires high-resolution, low-altitude magnetic data
  to support structural mapping, target definition and exploration
  planning across complex terrain."
- **Radiometric Surveys popup** has the same treatment: "Map near-surface
  geology and alteration patterns more clearly. Flightec acquires
  high-resolution radiometric data..." — and now shows your real
  comparison images, Uranium on the left (top on mobile) and Total Count
  on the right (below it on mobile). Since these two images are specific
  radiometric channels rather than a "Regional vs Flightec" comparison,
  I renamed the two labels from "Regional radiometric dataset" /
  "Flightec project-specific radiometric survey" to "Uranium" / "Total
  Count" to match, and gave each a short one-line caption. Flag it if
  you'd rather keep the old Regional/Flightec framing alongside these
  images instead. The button already read "Discuss Your Radiometric
  Survey" and scrolls to the form, so no change was needed there.
- Topographic Surveys' popup also now leads with its hook line
  automatically, since it uses the same hook+body pattern in the data —
  let me know if you'd rather that one stay body-only for now.
- **Contact section** now lists a second contact block, "General
  Enquiries", with a clickable link to info@flightec.co.za, underneath
  the existing Nathan Archer (Sales Manager) block.
- **Section spacing tightened by 60%** across the whole page — About,
  Our Approach, Capability, How We Work, Where We Operate and Contact
  all had 120px (130px for Contact) of top/bottom breathing room; that's
  now roughly 48px, so the page reads much less spread out. The one
  gap left untouched, on purpose, is the space between the "Above" and
  "Below" service groups inside Capability.
- **Magnetic Surveys popup** now has your real comparison images —
  Regional dataset on the left (top on mobile), your Flightec survey on
  the right (below it on mobile) — each with its own caption line, plus
  the closing line ("See what greater magnetic resolution can reveal.")
  above the button. The other two Above popups (Radiometric, Topographic)
  pick up the same caption/closing-line treatment automatically, still on
  placeholder images until their photography comes through.
- **Our Approach** (Above / Below / Beyond) has new copy throughout —
  updated body text for all three cards, matching what you sent through.
- **How We Work** has been reworked: new heading ("First contact to
  final product."), and all four steps renamed and rewritten — Project
  Scope, Planning & Deployment, Data Acquisition, Processing & Final
  Product.
- One small wording fix: "Our engineers deign specialized technology"
  had a typo — changed to "design", since that's clearly what was meant.
  Flag it if you'd actually intended different wording there.
- **New hero banner image** on both desktop and mobile (the aerial/LiDAR
  point-cloud style image you sent through).
- **About Flightec**: the three row labels are now "Field Operations",
  "Sensors" and "Data Processing".
- **Our Approach**: the "Above. Below. Beyond." heading has been removed
  from this section (the hero still has its own "Above. Below. Beyond."
  title — that one wasn't touched).
- **Where We Operate**: added a bit more breathing room between "...across
  Southern Africa." and the "Successful regional delivery..." paragraph
  that follows it.
- **Light mode is now the default theme** on every page load (it was dark
  before). The toggle still lets a visitor switch to dark at any time —
  it just starts on light now.
- Hero: "Above. Below. Beyond." with "Beyond." in the accent colour.
- Every "Discuss Your Project" button scrolls to the contact form.
- Below-section (Wireline Logging) cards are now plain, non-interactive
  display cards — clicking them no longer does anything. Only the three
  "Above" cards' "Learn More" buttons open a popup.
- Fixed, contour-line background texture on desktop only. It's been
  removed entirely on mobile per client request — mobile now uses
  plain solid section colours throughout, same as before the texture
  was ever introduced.
- "How We Work" now looks the same on mobile as on desktop (the
  circular icon nodes and connecting number/heading, just stacked in
  one column instead of four across), instead of the different
  numbered-timeline style mobile had before.
- The 3 "Above" service popups (Magnetic, Radiometric and Topographic
  Surveys) have been rebuilt from scratch to match your mockup exactly:
  title, one paragraph of body copy, the "Regional" vs "Flightec"
  side-by-side image comparison, then the button — no hero photo, no
  extra image, no split-screen layout, on either desktop or mobile. The
  comparison images are now sized much larger on desktop — the popup
  panel itself is wider and the images fill most of it, matching your
  mockup's proportions closely. The two comparison images per popup are
  placeholders for now — send through the real photography whenever
  you have it and it's a quick, contained swap on our end.
- On desktop, service cards (both "Above" and "Below") grow and lift
  slightly on hover for a bit more presence — a subtle version of the
  effect referenced from Porsche's site, not the same scale.
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
  scroll back up. On desktop it's still one shared progress value across
  all four icons. On mobile, each icon now lights up independently, only
  once it actually reaches the centre of the phone's screen, rather than
  all following one shared progress value — this also fixes it firing
  too early.
- The "Capability" section (the services grid) no longer has its own
  slightly-different background colour on mobile — it now matches the
  sections around it, in both light and dark mode.
- Fixed a rendering issue where the "How We Work" connecting line was
  visibly cutting through the middle of the icon circles (most obvious
  now that light mode is the default) — the icon circles are opaque
  again and fully cover the line behind them, in both themes.
- "About Flightec" no longer auto-highlights the 01/02/03 rows as you
  scroll past them on mobile — that scroll-driven behaviour has been
  removed entirely. Tapping a row still switches the background image,
  same as before; it's just no longer automatic.
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
