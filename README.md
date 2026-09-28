# Studio Klay — Responsive Landing Page, 3 Concepts (revision 3)

Three standalone, responsive landing-page concepts for the independent ceramic studio
**Studio Klay**. Each file is a single self-contained HTML document (fonts embedded as
base64 woff2, all illustration is inline SVG) — just open it in a browser.

| File | Concept | Mood |
|---|---|---|
| `concept_01_earthen.html`  | **Earthen** | Warm earthy palette, raw/contemporary artisanal, calm + flat, centered hero |
| `concept_02_nocturne.html` | **Nocturne** | Modern dark, parallax on scroll + text, motion & micro-interactions |
| `concept_03_playful.html`  | **Clay Play** | Cartoonish: pink / blue / yellow, thick outlines, sticker shadows, bouncy |

## Layout grid
* **Desktop:** 12 columns, 24px gutters, max width 1360–1440px.
* **Mobile (≤767px):** 4 columns, 12–14px gutters.
* Columns are declared per element with `class="c"` and `--sp` (desktop span),
  `--cs` (desktop start column) and `--spm` (mobile span).
* **Press `G`** on any page to toggle a live grid overlay (12 cols desktop / 4 cols mobile).

## Typography
* **Logo:** Tenor Sans (letterspaced, uppercase). Concept 01 keeps the specified brand
  colour `#B85A3C` and is set at ≥24px so it clears WCAG AA for large text (4.30:1).
* **Headlines / body:** Plus Jakarta Sans (variable, 200–800).
* Both faces are embedded in every HTML file; originals also in `/fonts` (`.ttf` + `.woff2`).

---

# Revision 3 — what changed

**Output A = desktop (12-col, 1440px) · Output B = mobile (4-col, 390px).** Both verified per concept.

### Global (all three)
* **Accessibility scaffolding:** skip-to-content link, `<main id="main">` landmark, labelled `<nav>`,
  `:focus-visible` rings, footer headings re-levelled (h4→h3), `autocomplete="email"` + labelled forms,
  every decorative SVG `aria-hidden`, meaningful illustration groups get `role="img"` + alt text,
  duplicated marquee runs hidden from screen readers.
* **Mobile menu (shared module):** `aria-expanded` / `aria-controls` / `aria-haspopup`, `role="dialog"`
  + `aria-modal`, body scroll-lock while open, Escape closes, focus moves to the close button and
  returns to the burger, Tab is trapped inside, auto-closes when resized to desktop.
* **Strict WCAG AA contrast + ≥44px tap targets** re-audited at 390/768/1024/1440 — zero failures.
* **Asset clipping** audited (`source/clip.py`): no SVG is cut by an `overflow:hidden` ancestor or the
  viewport edge (hero vase/badge in concept 3 pulled inside the stage; card hover lift reduced).

### Concept 01 — Earthen
* Studio text block now spans columns 1–6 so its 2-up stat grid lands exactly on cols 1–3 / 4–6;
  the newsletter row bottom-aligns headline and form.
* **Mobile workshop table → cards:** each session is a bordered card (date · 44px arrow button ·
  title · description · seats footer); the description, hidden on tablet, is restored on mobile.

### Concept 02 — Nocturne
* **Hamburger bug fixed:** the overlay was 97% translucent with a backdrop blur, letting the hero
  bleed through, and sat below the fixed progress bar; it is now opaque, z-indexed above all fixed
  chrome, scrollable, with a proper 3-bar icon. Rolling nav labels no longer read twice to AT;
  count-up stats carry stable `aria-label`s; cursor preview/glow/progress bar are `aria-hidden`.

### Concept 03 — Clay Play
* **Mobile product stack aligned:** all cards equal height (291px) with a fixed-height stage and
  flexible info block, so bottoms line up in the carousel and in the desktop grid.
* Carousel is a labelled `role="region"` with `aria-roledescription="carousel"`, focusable, with real
  `<button type="button">` dots (`aria-current`) instead of orphan tab roles; star rating exposed as
  one "Rated five stars" image; price stickers stay readable while vessel art is decorative.

---

# Revision 2 — what changed

### Concept 01 — Earthen
* **Alignment.** Hero spec strip is now a 4-column sub-grid (was centred flex); the shelf
  caption strip is a true 12-col row (each caption spans the same 2 columns as its vessel);
  the "All 24 objects" link now ends on column 12 (was 11) and the workshops note starts on
  column 9, so every section header, text block and bottom strip shares the same column edges.
* **Contrast (all AA).** New tokens: `--clay-text #96452A` (6.18:1) for dates/prices/numerals,
  `--umber #6E5138` (6.78:1) for eyebrows and captions, `--muted #5E564D` (7.0:1) for secondary
  copy, `--clay-fill #9E4A2C` for the solid button (5.66:1 with its label). Dark newsletter block
  text and placeholder raised. Brand `#B85A3C` retained for the logo/mark at large size.
* **Tap targets.** Logo, inline links, footer links, newsletter field/button, nav items and
  mobile menu rows are all ≥44px; footer link lists are 2-up on mobile.
* **Whitespace.** Desktop section padding 128→94px max, hero 132→92px, section-head margin
  62→42px, footer and meta rhythm tightened (full page 6020px → 5440px).

### Concept 02 — Nocturne
* **No more collisions.** The hero illustration was an absolutely-positioned overlay that could
  run under the navbar and behind the headline; it now lives in its own 12-column "shelf" band
  below the type with a floor line and captions, so type, navbar and illustration never overlap
  at any width. Background rings/bloom were pulled in, and the ghost-outline headline line is now
  solid ember (`#E2663C`, 5.84:1) instead of a watermark-like stroke. Parallax amplitudes halved.
* **Contrast.** Secondary/metadata `--dim` #9B918A → **#BDB4AD** (9.9:1), footer + nav links
  → **#E3DCD5** (11:1), legal/placeholder #6E6660 → **#ADA49D** (7.9:1), quote scrub idle state
  .16 → .45 opacity, CTA body copy raised to 90% white.
* **Tap targets.** Nav roll links wrapped so the anchor is 44px tall (animation intact), logo,
  "view all", footer links, subscribe button and email input ≥44px; the newsletter field stacks
  on mobile. Added a 768–920px header breakpoint so the nav + CTA never clip.

### Concept 03 — Clay Play
* **Mobile scroll length cut ~35%** (5845px → ~4550px): products are now a **swipeable
  scroll-snap carousel** with 44px dot controls, a "swipe for more" hint and keyboard/click
  paging; "how it works" cards collapse into compact icon+text rows; section, panel, hero and
  footer rhythm compressed; footer link lists go inline; the 4th class row is hidden on mobile.
* **Contrast.** `--blue` darkened to **#2B4FD6** so white body copy on the newsletter panel is
  6.6:1 (was 4.3–4.6:1 with cream/white); the "Newsletter" kicker no longer inherits white on
  yellow (now ink, 11.2:1); input placeholder set to #4A4566. All pink surfaces use ink text (6.4:1).
* **Fixed illustrations.** The jug symbol was redrawn (handle now attaches cleanly and no longer
  clips its viewBox — regenerated for all three concepts), the cup handle reattached to the body,
  the avatar mascot was a mis-scaled `<use>` crop and is now a properly transformed face badge,
  the newsletter bottle no longer overlaps the form on mobile, and the headline squiggle became a
  behind-the-text highlighter so it stops colliding with the next line.
* **Touch.** Buttons ≥48px, pills/logo ≥44px, footer links ≥44px, email input 52px, carousel dots 44px.

All three were verified with an automated pass (`source/audit.py`) at 390 / 768 / 1024 / 1440px:
zero WCAG AA contrast failures and zero sub-44px interactive elements.

---

## Concept 02 motion
Scroll-progress bar · hero line-mask reveal · multi-speed parallax (rings, glow, shelf vessels,
headline lines) · depth parallax still-life · reveal-on-scroll with stagger · count-up stats ·
word-by-word scroll-scrubbed quote · magnetic buttons with fill sweep · 3D tilt cards with
pointer glow · cursor-following vessel preview on the workshop list · infinite marquee.
All motion respects `prefers-reduced-motion`.

## Concept 03 interactions
Googly eyes that track the pointer, sticker hover-pop (translate + rotate + shadow growth),
press-down buttons, floating/spinning props, wavy section divider, marquee, mobile carousel.

## Text
All copy is Lorem Ipsum placeholder except the requested hero headline
“Slow down. Shape something real.” and its subhead.

## Source
`/source` holds the editable templates (`source/src/*.html` with the `__FONT_CSS__` /
`__VESSEL_DEFS__` tokens), `source/build.py` (inlines fonts + the SVG symbol set into
`/tmp/outputs`), `source/tools/gen_vessels.py` (procedurally generates the ceramic silhouette
profiles in `vessel_defs.svg`), and `source/audit.py` + `cr.py` (the contrast / tap-target checker).
Rebuild with: `cd source && python3 build.py`
