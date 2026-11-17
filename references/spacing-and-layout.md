# Spacing and Layout

## Spacing scale
Use one scale for margins, padding, and gaps: 4, 8, 12, 16, 24, 32, 48, 64, 96 px. Name the steps (`--space-1` … `--space-9`). Do not introduce 10, 14, 18, or 22 px unless the scale is changed deliberately.

## Role mapping
- Inside a control (button, input): 8–16 px horizontal, 8–12 px vertical.
- Between related items (label to input, list items): 8–12 px.
- Between groups inside a card: 16–24 px.
- Between sections on a page: 48–96 px desktop, 32–48 px mobile.
- Page side gutters: 16 px mobile, 24–32 px tablet, 40–80 px desktop with a max content width.

## Grid
- Use a 12-column grid on desktop, 8 on tablet, 4 on mobile, or a CSS grid with `auto-fit`/`minmax` for fluid layouts.
- Align edges: text, images, and cards share left edges within a column.
- Gutters are consistent across the page.

## Container widths
- Reading content: 60–75 ch.
- App content: 1120–1280 px.
- Full-bleed sections are intentional, not accidental overflow.

## Proximity rule
Items that belong together are closer than items that do not. If a heading sits closer to the previous section than to its own content, fix it.

## Alignment checks
- Left edges of headings, body, and form fields align.
- Baselines of buttons and inputs in a row match.
- Equal-height cards have equal internal structure (title, body, footer aligned).

## Layout tools
- Prefer flexbox and grid. Avoid absolute positioning for normal flow.
- Use `gap` rather than margins on siblings.
- Use `min-width: 0` on flex children that hold text to allow truncation.
- Keep z-index in a named scale (e.g., dropdown, sticky, modal, toast).
