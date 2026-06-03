# Yelena Khait — Artist Portfolio

Static portfolio site for painter Yelena Khait. Showcases paintings, custom shoes,
and TikTok process videos, with a commission/contact form. Deployed via GitHub Pages.

## Stack
- Plain static site: hand-written HTML + CSS (no build step, no framework).
- Animation: GSAP + ScrollTrigger (loaded from CDN).
- Forms: Web3Forms (commission.html posts to khait3102@gmail.com).
- Fonts: Playfair Display (display/serif) + Outfit (body), via Google Fonts.
- Image cropping/processing: Pillow (Python). ffmpeg for .mov -> .mp4.

## Run locally
From the project root:
    python -m http.server 8000
Then open http://localhost:8000  (use a server, not file://, so the videos play.)

## Pages
- index.html        Main page (hero, gallery, TikTok, about, CTA, footer). Entry point.
- shoes.html        Custom shoes gallery.        [still on ORIGINAL warm palette]
- abstract.html     Abstract works, depth rows.  [still on ORIGINAL warm palette]
- commission.html   Order form (Web3Forms).      [still on ORIGINAL warm palette]

NOTE: index.html has been redesigned into a soft cool-blue palette. shoes/abstract/
commission still use the OLD warm-cream + magenta look and are not yet updated to match.

## Design system (index.html)
CSS variables live in :root at the top of index.html. Current cool palette:
  --bg #EEF3F8  --card #E2EBF3  --charcoal #1E2A38  --mid #6B7C8E  --pale #CBD8E6
  --accent #5E8FC9  --accent-dim #4A78B0  --sky #7FB2E0  --blush #E9B5C8
The blush/coral is a secondary accent that echoes warm tones in the hero art.
Buttons are pill-shaped (border-radius:40px). Eyebrow labels (small uppercase,
letter-spaced, with a short rule) are used above section headings for consistency.

## Responsive
Breakpoints at 1024px, 768px, 420px. Mobile menu = animated hamburger.
Orientation/resize handled via debounced ScrollTrigger.refresh(true) +
invalidateOnRefresh:true on every ScrollTrigger. Uses 100dvh and
-webkit-text-size-adjust.

## Hero & CTA use responsive <picture> (desktop vs mobile art)
Both swap images at max-width:768px via a <source> element:
- HERO:  desktop = art-sedona-horses-hero.png   mobile = art-rainy-window-hero.png
- CTA:   desktop = art-bear-cta.png              mobile = art-beach-sunset-cta.png
A dark scrim sits over each so white text stays legible. The CTA has a thin inset
"gallery frame" and a subtle parallax drift on the background image (GSAP yPercent).

## Artwork = photos of physical canvases (IMPORTANT)
Every file in assets/images/art/ is a PHOTO of a real canvas on a wall, so the
originals have pale wall/border margins around the painting. For full-bleed use
(hero, CTA) and for clean gallery cards, images are CROPPED tight to the canvas
edge with Pillow and saved as new files — never overwrite the original:
  -hero  = cropped for hero use      (e.g. art-sedona-horses-hero.png)
  -cta   = cropped for CTA use       (e.g. art-bear-cta.png)
  -crop  = cropped for gallery cards (e.g. art-cat-portrait-crop.png)
Cropping approach: detect the dark canvas-edge line / pale-wall transition per side,
then crop just inside it. Resolution matters: small originals look blurry when
upscaled full-width on desktop — prefer the larger source images for desktop heroes/CTA.

## Gallery (index.html)
Curated CSS-grid mosaic (not a uniform grid). Cards use .tall (row span 2) and
.wide (col span 2) to honor each painting's real aspect ratio. Flip cards: hover
or tap flips to a back face with title/medium/description. Responsive swap so a
painting that is the hero on one screen is hidden from the gallery there and shown
on the other (.only-mobile / .only-desktop). On mobile the spans are simplified to
avoid layout gaps (uniform cells; wide pieces and one fill piece go full-width).

## Socials
TikTok @paintingartist2188 · Instagram @yelenas__art · YouTube @yelenakhait6520

## Deploy (GitHub Pages)
Repo: lwilliams027/YennaPortfolio (CONFIRM exact name — may have trailing hyphen).
Serves index.html from the main branch. Typical flow:
  git add -A
  git commit -m "..."
  git push        (if rejected, the working fix has been: git push --force)

## Conventions / preferences
- TikTok videos must be locally-hosted .mp4 (embedded TikTok links are unreliable;
  .mov does not play in Chrome/Edge — convert with ffmpeg first).
- Keep all existing GSAP animations intact when restyling unless asked otherwise.
- When changing a hero/CTA image, also set object-position and re-check the scrim
  so the white title stays legible.
