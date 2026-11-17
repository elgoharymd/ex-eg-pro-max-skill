# Typography

## Principles
- Two typefaces at most: one for display or headings, one for text. A single family in two or three weights is often better.
- Choose fonts that are licensed for the use, load fast, and support the project's languages (including Arabic and right-to-left text when needed).
- Set typography in tokens: `--font-display`, `--font-text`, and a named size scale.

## Scale
Use a modular or hand-tuned scale with roughly 5–7 steps, for example:
- Display: 48–72 px desktop, 32–40 px mobile
- H1: 36–48 px / H2: 28–32 px / H3: 20–24 px
- Body: 16–18 px (never below 16 px on mobile)
- Small/caption: 13–14 px, used sparingly

## Line height and measure
- Body line height: 1.5–1.7.
- Headings: 1.1–1.3, tighter as size grows.
- Line length for reading: 45–75 characters. Constrain paragraph width with `max-width` in `ch` or `rem`.
- Letter-spacing: slightly open for small uppercase labels (0.02–0.08em), slightly tight for large display text (−0.01 to −0.03em).

## Weight and contrast
- Use weight to create hierarchy before reaching for color.
- Muted text must still meet 4.5:1 contrast on its surface.

## Arabic and mixed-direction text
- Set `dir` and `lang` correctly on the root or block.
- Use fonts with proper Arabic shaping and adequate line height (often 1.7+).
- Do not italicize Arabic. Check that numbers, punctuation, and English brand names do not break alignment.
- Mirror layout direction, but not media or brand marks that must remain fixed.

## Rendering details
- Avoid text inside images for essential content.
- Use `text-wrap: balance` for short headings and `text-wrap: pretty` for paragraphs where supported.
- Prevent long words or URLs from overflowing with `overflow-wrap: anywhere` where needed.
