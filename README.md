# Andrew Dreyer Memorial Fund — page redesign prototype

A self-contained HTML/CSS prototype of a "warm-modern" redesign for
**https://www.brantlake.com/about-camp/andrew-dreyer-memorial-fund/**

Open `index.html` in any modern browser. No build step, no JS framework — just HTML, CSS, and Google Fonts.

This is a **reference design**, not a deployable WordPress page. Hand it to the BLC webmaster as a visual + structural blueprint to adapt into the existing brantlake.com theme.

---

## Direction

- **Aesthetic:** warm modern — brighter, airier, photo-forward, friendly.
- **Goal:** turn a flat CMS text page into an emotional fundraising appeal that converts.
- **Brand fit:** stays inside the existing Green & Gray identity. No new fonts beyond the site's existing Montserrat (plus one optional accent: Fraunces, for emotional pull-quote moments).

The companion critique with rationale lives at
`~/.claude/plans/can-you-leverage-this-memoized-fox.md`.

---

## Brand tokens used

| Token         | Hex       | Where it's used                                    |
|---------------|-----------|----------------------------------------------------|
| Deep pine     | `#063430` | Hero overlay, donate band, footer, primary text    |
| Pine-teal     | `#276f67` | Secondary surfaces, hero gradient                  |
| Leaf green    | `#0c8c3c` | Buttons, links, stat accents — **accent only**     |
| Leaf deep     | `#097030` | Hover/active states (AA-safer for white-on-leaf)   |
| Warm cream    | `#FAF8F3` | Page background                                    |
| Cream warm    | `#F2EDE0` | Alt section background                             |
| Rule          | `#DCD6C6` | Hairline borders                                   |
| Ink           | `#1B2826` | Body text                                          |
| Ink soft      | `#4A5856` | Muted body / captions                              |

All values are declared as CSS custom properties at the top of `index.html` under `:root`, so any global retoning is one place.

---

## Type

- **Body & headings:** Montserrat (loaded from Google Fonts, weights 300–800).
- **Emotional accents only:** Fraunces italic for the pull-quote, the "wordmark" under Andrew's name, and the `01/02/03` step numerals. Drop Fraunces entirely if Montserrat-only is preferred.

---

## Page structure

1. **Hero** — full-bleed photo, deep-green gradient overlay, big H1, italic sub, primary `Donate` button + secondary "Read Andrew's story ↓" link.
2. **Who was Andrew** — portrait + short personal copy on a warm cream surface.
3. **How the Fund works** — three rounded cards: *You give → Directors match half → A boy goes to camp.*
4. **Impact** — four stat cards + a single Fraunces pull-quote testimonial with a leaf-green left rule.
5. **Donate band** — full-width deep-green section with suggested amount chips, large leaf-green `Donate Securely` button, and 501(c)(3) fine print directly under it.
6. **Contact** — clean two-column layout with a contact card for Bill Frischling and a small ACA / heritage badge.
7. **Sticky mobile mini-CTA** — small floating `Donate` button shown on viewports under 768px so the conversion is always one tap away.

---

## What the webmaster needs to swap in

All placeholder spots are marked in the HTML with `<!-- PLACEHOLDER: ... -->` comments and in copy with `[bracketed]` labels.

| Spot                          | What to supply                                                        |
|-------------------------------|-----------------------------------------------------------------------|
| Hero background image         | High-res candid camp photo (waterfront, canoes, cabin group, etc.). Swap the URL in `.hero::before` `background`. |
| Andrew's portrait             | Replace the `.portrait` figure block with a real photo of Andrew (if the family is comfortable). |
| Donate buttons (3 places: hero, donate band, sticky mobile) | Replace `https://secure.usaepay.com/` with the live hosted-form URL from the current site. |
| Suggested amount chips        | If usaepay supports preset amounts via query params, wire each chip to its own URL (otherwise they're visual anchors only — remove them or leave the active default). |
| Stat numbers                  | Total boys sponsored, exact founding year, current full-summer cost. |
| Testimonial                   | A real quote from an alum, scholarship recipient, or family member. Attribute appropriately. |
| Contact card                  | Confirm mailing address, phone, email currently on brantlake.com — replace `[bracketed]` placeholders. |
| ACA / heritage badge          | Swap the inline "ACA" text mark for a real logo image if available.   |

---

## Responsiveness & accessibility

- Mobile-first CSS; clean reflow at ~375px, 768px, 1024px, 1440px.
- WCAG AA contrast throughout: white on deep pine, dark ink on cream, white on leaf-deep for button text.
- Visible keyboard focus state on every interactive element (`outline: 3px solid var(--leaf)`).
- Real `alt` text on every image; semantic `<section>` / `<header>` / `<footer>` / `<figure>` / `<blockquote>` / `<dl>` markup.
- Sticky mobile donate button keeps the conversion path one tap away below 768px.

---

## Notes for the WordPress adaptation

- The visual system is intentionally a small token set — palette, type scale, radius, shadow. Easiest path is to recreate it as a custom block pattern or a one-off page template, rather than fighting the parent theme's defaults.
- Nothing here depends on JS. The "active" state on a chip is purely a visual default; if the donate form takes a URL parameter, swap to anchor links per amount.
- All section spacing is driven by `padding` on `section`, scaled at the 768px and 1024px breakpoints. Tighten there if the parent theme adds its own container padding.

---

## Companion files

- `index.html` — the prototype.
- This `README.md` — handoff notes.
- (Reference) `~/.claude/plans/can-you-leverage-this-memoized-fox.md` — the original written critique with rationale.
