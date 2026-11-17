# Creative Direction

## Goal
Give the product a point of view before any component is drawn. A written direction prevents drift between pages and prevents generic output.

---

## Originality mandate

**The design must be unrecognizable as AI output.**

Before starting any design, ask: could this come from a template, a Dribbble trend, or a default component library? If yes, it is not ready. Keep pushing until the answer is no.

Signs you have found an original direction:
- The layout reflects the product's real workflow, not "hero + three cards."
- The color palette has a reason rooted in the brand or the material (a studio's warmth, a logistics dashboard's precision, a clinic's calm).
- Typography has character — a specific pairing made because it fits this brand, not because it was the default.
- The visual anchor (see below) is specific to this product, not generic.
- A stranger would describe it without using the words "modern," "clean," or "minimal."

---

## Direction brief (write this before the first component, 6 lines max)

- **Audience:** who, their context, their expectations.
- **Feeling:** three adjectives. Not "modern," "clean," or "professional" — those say nothing. Use: "deliberate, unhurried, precise" / "bold, editorial, candid" / "technical, spare, serious."
- **Visual anchor:** one idea that organizes the look. Must come from the product's real world.
  > Good: "a film call sheet" / "a pilot's instrument panel" / "a typographer's proof sheet" / "a production log book"
  > Bad: "modern dashboard" / "clean SaaS" / "dark mode app"
- **Color role:** what the accent does and how often it appears (aim for 5–10% of the surface).
- **Type voice:** display + text pairing with the reason (see typography.md for the font rules).
- **Avoid:** two or three things this brand must never look like.

---

## Finding the unexpected angle

The right design angle is usually not the most obvious one. Work through these:

1. **What is the physical or professional world of this product?** A studio booking tool lives in the world of photographers, sets, light. A logistics dashboard lives in the world of manifests, routes, timestamps. The design should feel like it belongs in that world.

2. **What is the user doing just before and after using this?** If they come from physical set preparation and go back to it, the UI should feel like a quick, trusted reference — not an experience to explore.

3. **What would a specialist in this field recognize?** A photographer would recognize a call sheet layout. A trader would recognize a ticker grid. Use the visual language of the domain.

4. **What would surprise without confusing?** Find one unexpected choice — in the grid, in the typographic scale, in a micro-interaction — that is memorable. One is enough.

---

## Asset direction

- All photography and illustration share one treatment (lighting, color grade, line weight).
- Icons are AI-generated images (Gemini or ChatGPT) — see `references/visual-assets.md`. Never drawn in SVG in code.
- Do not mix icon styles: all icons in a project use the same visual language and generation prompt prefix.

---

## Proactive improvement suggestions

After every delivery, generate 3–5 professional improvement suggestions for the user. See `references/pro-suggestions.md` for the format and rules.

---

## Review questions

1. Could a stranger identify the brand from one screen with the logo hidden? If not, the direction is too weak.
2. Does this look like it could come from a template or a Tailwind starter? If yes, push further.
3. Is there one element in this design that is genuinely unexpected?
4. Would a professional in this field recognize the visual language as belonging to their world?
