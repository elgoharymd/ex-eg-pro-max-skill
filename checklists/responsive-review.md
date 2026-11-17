# Responsive Review Checklist

Test widths: 360, 390, 768, 1024, 1440, 1920 px. Add landscape phone if relevant.

## Layout per width
- [ ] 360 px: content readable, no clipped controls.
- [ ] 390 px: primary action reachable in the lower screen area.
- [ ] 768 px: layout uses the tablet arrangement, not a stretched phone layout.
- [ ] 1024 px: navigation and content density suit a laptop-sized screen.
- [ ] 1440 px and 1920 px: max content width prevents excessively long lines; gutters look intentional.

## Overflow
- [ ] No horizontal page scroll at any width.
- [ ] Long words, URLs, and code wrap or truncate.
- [ ] Images and embeds fit their containers.
- [ ] Tables have a responsive treatment (stacked, cards, or a labeled scroll region).

## Touch
- [ ] Interactive targets ≥ 44 × 44 px with spacing between them.
- [ ] No hover-only interactions without a touch equivalent.
- [ ] Sticky headers and bottom bars do not cover focused content.

## Navigation
- [ ] Mobile navigation is operable with one hand and clearly labeled.
- [ ] Desktop navigation does not collapse into an unlabeled icon row.

## Forms and dialogs
- [ ] Forms are single-column on phones.
- [ ] Correct input types and keyboards are used.
- [ ] Dialogs become full-screen or bottom sheets on phones and remain scrollable.

## Typography and spacing
- [ ] Body text ≥ 16 px on mobile.
- [ ] Headings scale fluidly without breaking words awkwardly.
- [ ] Section spacing reduces on small screens without cramping.

## Viewport units
- [ ] Full-height sections do not hide content behind mobile browser toolbars (use `dvh` or flow layout).

## Evidence
- [ ] Screenshots or measurements recorded for each tested width, or "not run" with reason.
