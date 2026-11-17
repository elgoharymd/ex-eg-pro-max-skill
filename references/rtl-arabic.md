# RTL and Arabic Projects

Load this file first on any project where the UI is in Arabic, Hebrew, Persian, or any other RTL language,
**before** any design, layout, or CSS work.

---

## Document setup (HTML / React)

```html
<!-- Always set at the document root -->
<html lang="ar" dir="rtl">
```

In React:
```tsx
// In index.html or the root template
<html lang="ar" dir="rtl">

// For dynamic locale switching, set on <body> or the top container
document.documentElement.lang = 'ar';
document.documentElement.dir  = 'rtl';
```

---

## CSS: use logical properties, not physical ones

RTL layout flips left ↔ right. Use logical properties so the same CSS works in both directions.

| Avoid (physical) | Use instead (logical) |
|---|---|
| `margin-left` | `margin-inline-start` |
| `margin-right` | `margin-inline-end` |
| `padding-left` | `padding-inline-start` |
| `padding-right` | `padding-inline-end` |
| `border-left` | `border-inline-start` |
| `border-right` | `border-inline-end` |
| `left: 0` | `inset-inline-start: 0` |
| `right: 0` | `inset-inline-end: 0` |
| `text-align: left` | `text-align: start` |
| `text-align: right` | `text-align: end` |
| `float: left` | `float: inline-start` |
| `border-radius: 4px 0 0 4px` | `border-start-start-radius: 4px; border-end-start-radius: 4px` |

**Exceptions:** explicit LTR content (phone numbers, URLs, code, prices in Latin numerals).
Wrap those in `<span dir="ltr" class="ltr">` or `<bdi>`.

---

## Arabic typography

**Recommended fonts:**
- **Readex Pro** — covers Arabic + Latin in one weight-axis font; designed for screen readability.
- **Cairo** — slightly rounder, good for display headings.
- **IBM Plex Arabic** — neutral, good for dense data interfaces.

**Font loading:**
```css
@import url('https://fonts.googleapis.com/css2?family=Readex+Pro:wght@300;400;500;600;700&display=swap');

body {
  font-family: 'Readex Pro', system-ui, sans-serif;
}
```

**Size:** Arabic script reads better at slightly larger sizes. If Latin UI uses 14 px, Arabic benefits from 15–16 px for the same read comfort.

**Line height:** Arabic descenders and ascenders need more room. Use `line-height: 1.6` or higher for body text; never below `1.4`.

**Letter spacing:** Do NOT set `letter-spacing` on Arabic text. The Arabic script is cursive — adding letter spacing breaks the glyph connections and makes the text unreadable.

**Number rendering:** Arabic-Indic (٠١٢٣) vs Western (0123). Be deliberate — mixing in one sentence is usually fine, but be consistent within the same context (all table cells the same style).

---

## Layout: RTL-first, not LTR + flip

Design RTL from the start. Do not build LTR and then apply `transform: scaleX(-1)` or `direction: rtl` as an afterthought — that approach breaks icon orientation, shadow direction, and animation direction.

**Reading direction:**
- Text flows right to left.
- UI reading order: right to left (primary action on the right, breadcrumbs start from the right).
- Lists and navigation: items are still top-to-bottom (block direction is unchanged).

**Alignment:**
- Primary content anchors to `inline-start` (which is "right" in RTL).
- Secondary / metadata anchors to `inline-end` (which is "left" in RTL).

---

## Icons and directional elements

Some icons carry inherent directionality (arrows, chevrons, back/forward, play/rewind, speech bubbles with tails). These must be **mirrored** in RTL.

```css
/* Mirror directional icons in RTL */
[dir="rtl"] .icon-arrow-forward,
[dir="rtl"] .icon-chevron-right,
[dir="rtl"] .icon-back {
  transform: scaleX(-1);
}
```

Icons that are **not** mirrored: settings gear, search magnifier, clock, calendar, check, warning, info, most logos, photo/video camera. When in doubt, check the Material Design RTL guidelines.

---

## Mixed-direction content (bidirectional text)

**Explicit LTR spans** for:
- Phone numbers: `<span dir="ltr" class="ltr" style="unicode-bidi: isolate">+966 50 123 4567</span>`
- Prices with Latin numerals and currency symbols
- URLs and email addresses
- Code snippets
- English words inside Arabic sentences

**`<bdi>` for unknown-direction content** (user-generated text, names from an API):
```html
<bdi>{{ userName }}</bdi>
```

**CSS class `ltr`:**
```css
.ltr {
  direction: ltr;
  unicode-bidi: isolate;
  display: inline-block; /* or inline — isolates bidi context */
}
```

---

## Flexbox and Grid in RTL

Flexbox `row` direction already flips correctly with `dir="rtl"`. Grid does too with logical properties.

```css
/* This works correctly in both LTR and RTL */
.row {
  display: flex;
  flex-direction: row;         /* flips automatically */
  gap: 12px;
}

.grid {
  display: grid;
  grid-template-columns: 200px 1fr;  /* columns flip with the dir */
}
```

Watch for: explicit `order` values, `justify-content: flex-start/flex-end` (use `start/end`), and absolute positioning with `left/right` (use `inset-inline-start/end`).

---

## CSS transitions and animations

RTL does not automatically reverse animations. If an element slides in from the right on LTR, it should slide in from the left on RTL.

```css
/* Direction-aware slide in */
@keyframes slide-in-start {
  from { transform: translateX(calc(var(--dir, 1) * -20px)); opacity: 0; }
  to   { transform: translateX(0); opacity: 1; }
}

:root { --dir: 1; }
[dir="rtl"] { --dir: -1; }
```

Or use a simpler approach: define animations with `inset-inline-start` changes, which the browser resolves per direction.

---

## Shadows and gradients

Shadows visually suggest depth and light source. In RTL layouts, a drop-shadow that was bottom-right in LTR should often be bottom-left in RTL (since the visual "depth" follows the reading anchor). In practice, bottom-center shadows are safer for RTL projects:

```css
/* Neutral shadow (works in both directions) */
box-shadow: 0 2px 8px 0 rgba(0, 0, 0, 0.12);

/* Avoid directionally biased shadows like: */
/* box-shadow: 4px 4px 12px rgba(0,0,0,.2); */
```

---

## Forms

- Labels are on the right of inputs in RTL.
- Validation icons (success checkmark, error x) appear at `inline-end` of the input field.
- Input `type="tel"` and `type="email"` should be `dir="ltr"` or `direction: ltr` since users type them LTR even on Arabic UIs.
- Checkboxes and radio buttons are to the right of their labels.

```css
/* Input field with inline-end icon */
.input-wrap {
  position: relative;
}
.input-icon {
  position: absolute;
  inset-block-start: 50%;
  inset-inline-end: 12px;
  transform: translateY(-50%);
}
```

---

## Numbers and dates

**Dates:** Arabic uses both Hijri and Gregorian calendars. Confirm with the project which to use.
Common Arabic date format: `الثلاثاء، ١٧ نوفمبر ٢٠٢٦` (using `Intl.DateTimeFormat` with `locale: 'ar-SA'` or `'ar-EG'`).

**Numbers in Arabic:** Arabic-Indic numerals (٠–٩) are traditional; Western Arabic numerals (0–9) are common in modern digital products especially for data-dense interfaces. Pick one style and be consistent.

```js
// Western numerals with Arabic locale
new Intl.NumberFormat('ar', { numberingSystem: 'latn' }).format(1234)
// → '1,234'

// Arabic-Indic numerals
new Intl.NumberFormat('ar', { numberingSystem: 'arab' }).format(1234)
// → '١٬٢٣٤'
```

---

## Testing RTL

1. **Browser DevTools:** Elements → Computed → check `direction: rtl` on `<html>` and key containers.
2. **Overflow check:** Inspect every row and column for LTR overflow. Run at 360 px width.
3. **Icon audit:** Every arrow, chevron, and directional icon must be mirrored correctly.
4. **Mixed text:** Insert test text with English words, prices, and phone numbers inside Arabic sentences.
5. **Keyboard navigation:** Tab order should follow visual RTL order (not LTR DOM order).
6. **Screen reader:** VoiceOver / NVDA reads RTL text if `lang` and `dir` are set correctly.

---

## Common RTL bugs to watch for

| Bug | Cause | Fix |
|---|---|---|
| Text overflows to the wrong side | Using `margin-right` instead of `margin-inline-end` | Switch to logical properties |
| Icon points the wrong way | No mirror rule for directional icons | Add `[dir="rtl"] .icon { transform: scaleX(-1) }` |
| Absolute element in wrong corner | Using `right: 0` instead of `inset-inline-end: 0` | Switch to logical property |
| Input placeholder mis-aligned | Missing `dir="rtl"` on input | Add `dir="rtl"` or `direction: rtl` |
| Animation slides wrong way | LTR translateX in keyframe | Use direction-aware variable (see above) |
| Number runs LTR inside Arabic sentence | Missing `dir="ltr"` wrapper | Wrap number in `<span dir="ltr">` |
| Table columns reversed | Explicit `text-align: left` | Switch to `text-align: start` |
| Scroll indicator on wrong side | Default scrollbar | Use `scrollbar-gutter: stable both-edges` or accept it |
