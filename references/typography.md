# Typography

## Principles
- Two typefaces at most: one for display or headings, one for text. A single family in two or three weights is often better.
- Choose fonts that are licensed for the use, load fast, and support the project's languages (including Arabic and RTL text when needed).
- Set typography in tokens: `--font-display`, `--font-text`, and a named size scale.

---

## No AI-looking fonts

**This is a hard rule.** The following fonts make the product look generated, default, or AI-produced. Do not use them:

| Font | Why it is banned |
|---|---|
| **Inter** | The default font of AI-generated UIs, Figma templates, and every SaaS starter. Instantly recognizable as "not designed." |
| **DM Sans** | Second most common AI design font. Used in thousands of indistinguishable dashboards. |
| **Plus Jakarta Sans** | Overused in AI-generated product designs. |
| **Nunito / Nunito Sans** | Feels friendly-generic. The font of "we just picked something round." |
| **Outfit** | Overused in AI and no-code design outputs. |
| **Poppins** | Has been the default of every Bootstrap/Tailwind template for years. |
| **Lexend** | Technically readable but visually anonymous. |
| **Rubik** | Worn out in generic SaaS UIs. |
| **Montserrat** | Still being used as if it were distinctive. It is not. |
| **Raleway** | Signals "amateur modern design." |

**For Arabic — also avoid:**
| Font | Why |
|---|---|
| **Noto Sans Arabic** (default weight) | The system fallback feel. Signals "we did not design the Arabic." |
| **Tajawal** (default pairing) | Overused across Arabic SaaS products without customization. |
| **El Messiri** (without purpose) | Decorative but randomly applied. |

---

## Fonts with character — use these

Choose fonts that have a history, a context, or a point of view. Each pick needs a reason.

**Latin display (headings, hero text):**
| Font | Character | When to use |
|---|---|---|
| **Playfair Display** | Editorial, contrast, literary | Long-form, editorial, high-craft products |
| **Cormorant** | High-contrast, refined, cold | Luxury, architecture, premium brands |
| **Syne** | Geometric, contemporary, angular | Creative studios, tech with personality |
| **Clash Display** | Strong, editorial, modern | Brands that want to feel like a magazine |
| **Libre Baskerville** | Classic, readable, honest | Products with a craft or quality narrative |
| **DM Serif Display** | Journalistic, contrast-heavy | News, finance, serious data |
| **Spectral** | Sophisticated, structured | Legal, medical, formal dashboards |
| **Space Grotesk** | Technical, slightly unusual | Dev tools, infrastructure, technical products |

**Latin text (body, labels, data):**
| Font | Character | When to use |
|---|---|---|
| **Source Serif 4** | Readable, humanist, editorial | Long-form text, reports |
| **Libre Franklin** | Neutral but with structure | Dashboards, data-dense UIs |
| **IBM Plex Sans** | Technical, structured, neutral | Dev tools, data products |
| **Karla / Cabin** | Friendly but not generic | Consumer products with warmth |
| **Fira Sans** | Technical, clear | Developer or data-focused products |

**Arabic (use with intent):**
| Font | Character | When to use |
|---|---|---|
| **Readex Pro** | Designed for Arabic screens, balanced | Most Arabic digital products (acceptable default) |
| **IBM Plex Arabic** | Technical, structured | Dashboards, data-dense Arabic UIs |
| **Lateef** | Traditional, calligraphic | Cultural, heritage, editorial projects |
| **Reem Kufi** | Geometric, contemporary | Display text, brand names, headings |
| **Scheherazade New** | Classical, formal | Long-form Arabic reading |

---

## Scale

Use a modular or hand-tuned scale with roughly 5–7 steps:
- Display: 48–72 px desktop, 32–40 px mobile
- H1: 36–48 px / H2: 28–32 px / H3: 20–24 px
- Body: 16–18 px (never below 16 px on mobile)
- Small/caption: 13–14 px, used sparingly

## Line height and measure
- Body line height: 1.5–1.7.
- Headings: 1.1–1.3, tighter as size grows.
- Line length for reading: 45–75 characters. Constrain paragraph width with `max-width` in `ch` or `rem`.
- Letter-spacing: slightly open for small uppercase labels (0.02–0.08em), slightly tight for large display text (−0.01 to −0.03em).
- **Arabic:** never set `letter-spacing` on Arabic text. Use `line-height` ≥ 1.6 for body.

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
