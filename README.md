# Flightec Website

Website for **Flightec**, Southern Africa's specialist partner in mining and mineral exploration: airborne geophysical surveys, wireline logging and data processing.

Staging URL: https://conversionadvantage00.github.io/flightec_staging/

Built and maintained by [Conversion Advantage](https://conversionadvantage.co.za/).

---

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | The complete site. Styles, scripts, fonts (Aptos) and images are all embedded, so this single file is the whole website. |
| `og-share.jpg` | Social sharing image (1200 × 630) referenced by the Open Graph and Twitter meta tags. Keep it in the repository root. |
| `README.md` | This file. |

There is no build step and there are no dependencies.

## Deploying

1. Commit `index.html` (and `og-share.jpg`) to the root of the `main` branch.
2. In the repository, go to **Settings → Pages**.
3. Set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then save.
4. The site will be live at the staging URL above within a minute or two. Later pushes to `main` redeploy automatically.

If the site moves to its own domain, update the `canonical`, `og:url` and `og:image` / `twitter:image` URLs in the `<head>` of `index.html`.

## Page sections

Hero · About Flightec · Our Approach · Capability (Above / Below services) · How We Work · Where We Operate · Contact (form, contacts and office maps) · Footer

## Interactive features

**Hero reveal (desktop only).** Moving the mouse over the hero uncovers the magnetic survey image in small square blocks that fade back out. It only runs on devices with a mouse at 1024px and wider, and is switched off for visitors who have "reduce motion" enabled. The settings are data attributes on the hero `<section>`:

| Attribute | Current | Controls |
| --- | --- | --- |
| `data-cell-size` | `16` | Square size in pixels |
| `data-radius` | `3` | Brush size, measured in squares |
| `data-hold` | `150` | Milliseconds a square stays fully revealed |
| `data-fade` | `200` | Milliseconds a square takes to fade out |
| `data-jitter` | `1` | How ragged the brush edge is (0 to 1) |

**Service popups.** The three "Above" service cards open a detail panel with an intro, numbered survey figures and a call to action that jumps to the contact form. Popup content (titles, text, figure images and button labels) lives in `POPUP_DATA` at the top of the page script.

**Office maps.** Windhoek (Head Office) and Knysna (Research & Development) are embedded Google Maps. To change a location, replace the `src` of the relevant `<iframe>` with a new embed link from Google Maps (**Share → Embed a map**).

**Contact form.** Submitting the form opens the visitor's email client with a pre-filled message to the sales contact. No server or form service is required.

## Motion and accessibility

- All looping and entrance animation is disabled for visitors who prefer reduced motion.
- Cursor-driven effects (hero reveal, card highlights) only run on devices with a mouse. Touch devices get the static design.
- Keyboard users get a visible focus ring on links and buttons, and the popups close with the Escape key.

## Browser support

Current versions of Chrome, Edge, Safari and Firefox on desktop and mobile.

---

© 2026 Flightec. All rights reserved.
