# Handoff: Dr Pejčinoski — Dental Practice Website

## Overview
Marketing website for Stomatološka ordinacija Dr Pejčinoski, a dental practice in Novi Sad (Podbara) operating since 2004. Single-page site: header/nav, hero, services grid, "why us" + stats band, "no fear of the dentist" section, trust/testimonials section, contact form + map, footer, floating contact bubble.

## About the Design Files
The bundled file (`Dr Pejcinoski.dc.html`) is a **design reference built in HTML** — a working prototype showing intended layout, styling, copy, and interaction behavior. It is not production code to copy verbatim. Recreate these screens in the target codebase's actual environment (e.g. a static site generator, WordPress theme, or a framework like Next.js/React — whichever the team uses) using that environment's conventions. If no codebase exists yet, plain semantic HTML/CSS/vanilla JS matching this design is the simplest faithful choice.

## Fidelity
**High-fidelity.** Colors, typography, spacing, and copy (in Serbian) are final. Recreate pixel-accurately, including hover/active states and the responsive breakpoints below.

## Screens / Sections
All sections live in one scrolling page (no routing).

### 1. Header (sticky)
- Sticky top, `rgba(255,255,255,0.92)` background with `backdrop-filter: blur(10px)`, bottom border `#e3ebf0`.
- Max width 1200px, centered, `padding: 16px 32px`, flex row, space-between.
- Logo: stacked text — "DR PEJČINOSKI" (700 weight, 20px, letter-spacing 0.06em, color `#1c3a52`) over "STOMATOLOŠKA ORDINACIJA" (500 weight, 10.5px, letter-spacing 0.14em, color `#7c8f99`).
- Desktop nav (hidden ≤760px): links "Usluge", "Zašto mi", "Poverenje" — `#4f6472`, 500 weight, 14.5px, hover → `#1c3a52`.
- Phone button: `tel:021551089`, dark navy pill (`#1c3a52`, radius 10px, padding 12px 22px), phone icon + "021 551-089"; hover `#142a3c`; has a radial-gradient mouse-follow "shine" overlay on mousemove.
- Hamburger button (shown ≤760px only): 46×46px, white, bordered `#dde7ec`, radius 10px, opens a slide-down mobile menu (max-height animated 0→320px) listing Usluge / Zašto mi / Poverenje / "Zakaži termin".

### 2. Hero
- Two-column grid: text column (`minmax(0,1fr)`) + photo column (`1.15fr`); stacks to 1 column on mobile with photo fixed at 320px height below text.
- Text column: padding `72px 56px 72px 112px` (mobile: `56px 24px 32px`), max-width 620px.
  - Eyebrow: "Ordinacija Dr Pejčinoski / Novi Sad" — `#2f8f85`, 600 weight, 13px, uppercase, letter-spacing 0.12em.
  - H1 (300 weight, 50px, line-height 1.12; mobile 42px/34px): "Stomatološka nega zasnovana na *tradiciji*." — the word "tradiciji" in `#2f8f85`, normal style.
  - Paragraph, `#4f6472`, 17px, max-width 460px: practice description, on Podbara, since 2004.
  - CTA button "Zakažite pregled" → `#kontakt` anchor, same navy pill + shine-on-hover pattern as phone button.
- Photo column: full-bleed `image-slot` (placeholder "Fotografija ordinacije / pacijenta"), with a left-edge white gradient fade overlay for blending into the text column.

### 3. Usluge (Services) — id="usluge"
- Centered header: eyebrow "Naše usluge" + H2 "Sve što vaš osmeh **može da poželi**" (400/600 weight mix, 40px).
- **Desktop (≥1281px)**: 4-column CSS grid of 8 service cards (`.svc-full-grid`).
- **Below 1281px**: horizontal snap-scroll carousel (`#svc-carousel`, 3-card width, hidden scrollbar) with two round arrow buttons below (46×46px, white/bordered, hover fills navy).
- Each card: white bg, border `#e3ebf0` (18px radius), padding `34px 28px 26px`, min-height 340px. Contains: an 78×78 circular icon badge (navy bg, white masked icon), title (600/20px), description (14.5px, `#4f6472`), and a "Više →" link pinned to bottom via `margin-top:auto` with a top divider.
- **Interaction**: on hover, a navy "curtain" animates up from the bottom to fill the whole card (height 0%→100%, border-radius morphs from pill-top to full-rounded), text flips to white, icon badge inverts (white circle grows in, icon mask switches fill), card lifts (`translateY(-8px)`) with a soft shadow. On tap (mobile/carousel context) scrolls the carousel forward by one card width.
- The 8 services: Konzervativna stomatologija, Estetska stomatologija, Izbeljivanje zuba, Dečija stomatologija, Stomatološka protetika, Ortodoncija, Oralna hirurgija, Bolesti usta i zuba — each with its own masked icon image (see Assets).

### 4. Zašto mi (Why us) + Stat band — id="zasto"
- Centered header: eyebrow "Po čemu se razlikujemo" + H2 "Ono čemu se pacijenti **rado vraćaju**".
- 3-column auto-fit grid (min 230px) of feature items: circular 66px icon badge (`#eef3f6` bg, navy icon), title (600/19px), description (14.5px). Items fade+slide up into view on scroll (`IntersectionObserver`, staggered 110ms per sibling, 620ms cubic-bezier ease).
  - Features: "Tradicija i kontinuitet", "Lični pristup", "Preporuke kao poverenje" (no heart icon — intentionally removed per earlier revision).
- **Stat band** (full-bleed, diagonal gradient `#142a3c → #1c3a52 → #2f8f85`, two faint radial-gradient dot decorations): 4-column grid (2-column on mobile, gap 28/16px) of stat items, each a big number/label pair in white:
  - "{{20}}+" animated count-up (eased cubic, runs once on first scroll-into-view) / "godina tradicije"
  - "Besplatno" / "prvi pregled i konsultacija"
  - "Po zakazivanju" / "jednostavno dogovaranje termina"
  - "Član komore" / "privatnih doktora stomatologije Srbije"
  - Number size 34px/700 weight; mobile reduces to 24px.

### 5. Bez straha (No fear) section
- 2-column grid (stacks on mobile), gap 60px, padding `84px 32px 100px`.
- Left: full-height rounded photo (`image-slot id="fear-photo"`, 16px radius, drop shadow) — **currently placeholder, awaiting real photo**.
- Right: eyebrow "Bez straha", H2 "Imate **strah od stomatologa?** Niste sami." (400/600 mix, 38px), body copy about working patiently with anxious patients, CTA "ZAKAŽITE PRVI PREGLED" (same navy shine-button pattern).

### 6. Poverenje (Trust) — id="poverenje"
- Full-bleed `#eef3f6` background, faint decorative wavy SVG line behind content (opacity 0.06, navy stroke).
- Centered header: eyebrow "Naš pristup", H2 "Poverenje koje traje **generacijama**", supporting paragraph.
- 3-column auto-fit grid of trust cards (white, border `#dde7ec`, 16px radius, padding `30px 26px`, centered text): 54px icon badge + title (600/17px) + description (14px).
  - Cards: "Tradicija od 2004.", "Lični pristup", "Preporuke pacijenata" — **copy is generic placeholder; swap in real patient quotes or Google review excerpts when available.**
- Below the grid: pill-shaped "Pronađite nas na Google mapi" link (white, bordered, Google "G" multicolor icon SVG) linking to a Google Maps search for the practice, lifts on hover.

### 7. Kontakt (Contact) + Map — id="kontakt"
- White card (border `#dde7ec`, 26px radius, heavy soft shadow, padding 54px) containing a 2-column grid (1fr / 1.1fr, stacks on mobile):
  - **Left**: eyebrow "Kako Vam možemo pomoći", H2 "Zakažite **konsultaciju**", intro paragraph, then 4 contact-info rows (each a 48px navy circular icon + label/value pair): Telefon (021 551-089 · 064 202-38-13), Email (pejcinoskisanja@gmail.com), Adresa (Milovana Glišića 5, Novi Sad / Podbara), Radno vreme ("Isključivo po prethodnom zakazivanju").
  - **Right** (left border divider, `padding-left: 48px`; divider becomes a top border on mobile): booking form — Ime/Prezime (2-col), Telefon/Email (2-col), "Tip upita" select (Redovni pregled / Stomatološka protetika / Estetska stomatologija / Oralna hirurgija / Konsultacija), optional message textarea, submit button "POŠALJI ZAHTEV" (navy shine button, full width), fine-print consent line. On submit → success state: checkmark badge, "Hvala na prijavi!", "Pošalji novu prijavu" reset button.
  - All inputs: 1px border `#cfdce3`, 10px radius, 13px padding, focus border → `#1c3a52`.
- Below the card: embedded Google Maps iframe (300px height, 16px radius) centered on Milovana Glišića 5, Novi Sad.

### 8. Footer
- White background, top border `#e3ebf0`. 3-column grid (1.4fr/1fr/1fr; 2-col on mobile with logo column spanning full width): practice name/tagline + blurb, "NAVIGACIJA" links (Usluge/Zašto mi/Kontakt), "KONTAKT" block (phone/email/address with small icons).
- Bottom bar: "© 2026 Dr Pejčinoski - Stomatološka ordinacija · Sva prava zadržana", `#8fa3ad`, 13px.

### 9. Floating contact bubble
- Fixed bottom-left (24px/24px), 76px navy circle, chat icon + "Live" label, links to `#kontakt`. Persistent across scroll.

## Global interactions & behavior
- **Shine/glow buttons**: every primary navy CTA (phone button, hero CTA, fear-section CTA, submit button) has a hidden radial-gradient circle that follows the cursor on `mousemove` and fades out on `mouseleave` (`glowMove`/`glowLeave` handlers) — a subtle spotlight effect, not a static gradient.
- **Click ripple**: any `pointerdown` anywhere on the page spawns a short-lived (650ms) expanding radial-gradient ripple at the click point (`clickRipple` keyframe, scale 0.2→1, fade out).
- **Touch sheen**: on touch devices, a large soft radial "glow" (320px) follows the finger during touchstart/touchmove, fading out ~420ms after movement stops.
- **Scroll-reveal**: `[data-reveal]` feature items fade up into place via `IntersectionObserver`, staggered per sibling.
- **Stat count-up**: the "20+ years" stat animates from 0 on first scroll-into-view of the stat band (cubic ease-out, 1400ms), runs once.
- **Service card hover/curtain**: described in section 3 above.
- **Services carousel**: horizontal snap-scroll with two arrow buttons scrolling by one card width; visible only below 1281px (desktop shows the full static 4-col grid instead — these are mutually exclusive via CSS, not JS).
- **Mobile menu**: hamburger toggles a max-height-animated dropdown under the header.
- **Contact form**: client-side only in this prototype — `onSubmit` prevents default and flips to a static success state (no real submission wired up; no field validation beyond native `required`).

## Responsive breakpoints
- **≤1281px**: services switch from 4-col grid to carousel.
- **≤900px**: hero becomes 1 column (photo 320px tall below text); services carousel cards go full-width; 2-col sections (fear section, contact grid) stack; stat band becomes 2 columns, smaller numbers (24px).
- **≤760px**: desktop nav hidden, hamburger shown; header padding/logo sizes shrink; footer becomes 2 columns; H1→42px, H2→30px.
- **≤480px**: H1→34px; phone number text hidden from header button (icon only); stat numbers 24px/labels 11px; contact card padding/radius reduced.

## Design Tokens
**Colors**
- Navy (primary/CTA/ink): `#1c3a52` (hover-dark `#142a3c`), deep navy accent `#1c3242`, `#142a3c`
- Teal (accent/eyebrow/links): `#2f8f85` (hover `#246f67`), stat-band gradient end
- Body text: `#4f6472`; muted labels: `#7c8f99`, `#8fa3ad`
- Borders: `#e3ebf0`, `#dde7ec`, `#cfdce3`
- Light surface: `#eef3f6`
- White: `#ffffff`
- Stat-band gradient: `linear-gradient(120deg, #142a3c 0%, #1c3a52 55%, #2f8f85 100%)`

**Typography**
- Font: Hanken Grotesk (Google Fonts, weights 300/400/500/600/700), fallback `-apple-system, system-ui, sans-serif`
- H1: 300 weight, 50px (desktop) / 34–42px (mobile), line-height 1.12
- H2: 400/600 mixed weight, 36–40px, line-height ~1.14–1.16
- H3 (card titles): 600 weight, 17–26px
- Body: 14–17px, line-height 1.6
- Eyebrow labels: 600 weight, 13px, uppercase, letter-spacing 0.12em, teal

**Spacing / radii / shadows**
- Section vertical padding: 84–100px desktop, 64px mobile
- Card radius: 14–26px depending on component (buttons 10px, pills 999px, circular badges 50%)
- Shadows: soft, large-blur, low-opacity navy (e.g. `0 44px 90px -56px rgba(20,30,40,0.35)` on the contact card; `0 14px 30px -14px rgba(20,30,40,0.35)` on arrow buttons)

## Assets
- `zub.png` — tooth mark/favicon-type asset (note: an earlier orange tooth watermark was deliberately removed from the "why us" section background per design direction; do not reintroduce it).
- `icons/` — masked service + step icons (`bolesti.png`, `estetska.png`, `izbeljivanje.png`, `decija.png`, `protetika.png`, `ortodoncija.png`, `oralna-hirurgija.png`, `implantologija.png`, plus `step-kontakt.png`, `step-pregled.png`, `step-terapija.png`, `step-kontrola.png` — the step icons are currently unused in the shipped page but present in the logic class's data, left over from a removed "Kako funkcioniše" section; safe to ignore/delete).
- `image-slot.js` — the placeholder/drag-drop image component used for `hero-photo` and `fear-photo` slots. Replace both with real photography before launch — **`fear-photo` has no image at all yet.**
- `uploads/HERO.png` — the current hero photo.
- Google "G" logo SVG is inlined directly in the trust section (official 4-color Google "G" mark).
- Google Fonts: Hanken Grotesk, loaded via `<link>` to `fonts.googleapis.com`.

## Files
- `Dr Pejcinoski.dc.html` — the full page design (structure + inline styles + interaction logic in one file).
- `icons/` — service/step icon assets referenced via CSS mask.
- `image-slot.js` — placeholder image component dependency.
- `zub.png` — tooth asset.
- `uploads/` — uploaded photo(s) currently in use.

## Open items for the developer
- Replace `fear-photo` placeholder with a real photo (relaxed patient interaction) — not yet supplied.
- Trust-section copy is generic; swap in real patient testimonials/Google reviews once confirmed by the client.
