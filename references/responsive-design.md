# Responsive Design

## Principle
Design for the context of each screen size, not for a scaled copy. A phone user is often one-handed, on the move, and scrolling quickly. A desktop user compares, scans, and types more.

## Breakpoints
Use these as starting points and adjust to content:
- `xs` 0–359 px (small phones; must still work)
- `sm` 360–599 px (phones)
- `md` 600–899 px (large phones, small tablets)
- `lg` 900–1199 px (tablets landscape, small laptops)
- `xl` 1200–1599 px (laptops, desktops)
- `2xl` 1600 px+ (wide screens)

Base styles target the smallest size; enhance upward with `min-width` queries.

## Re-composition by size
- **Navigation:** on phones, a compact bar with a clear menu or a bottom bar for 3–5 primary destinations. On desktop, a full horizontal or side nav.
- **Tables:** on phones, switch to stacked key/value rows or cards with the most important columns first. Provide horizontal scroll only with a visible container and sticky first column when needed.
- **Forms:** one column on phones; two columns only where field pairs are logically linked (e.g., first and last name). Use the right `inputmode` and `autocomplete`.
- **Media:** constrain width, set aspect ratios, and avoid loading desktop-size images on phones (`srcset`/`sizes`).
- **Modals:** full-screen sheets on phones, centered dialogs on larger screens.
- **Dense data (dashboards):** prioritize one summary per row on phones; allow the user to expand details.

## Touch and reach
- Targets ≥ 44 × 44 px, with ≥ 8 px between adjacent targets.
- Primary actions in the thumb zone on phones (lower part of the screen).
- Hover-only interactions need a touch equivalent.

## Overflow
- No horizontal scroll on the page at any tested width. Check long words, URLs, code, and wide images.
- Use `max-width: 100%` on media and `min-width: 0` on flex and grid children.
- Intentional scroll regions are labeled and keyboard-scrollable.

## Typography and spacing on small screens
- Body ≥ 16 px. Headings scale with `clamp()`.
- Reduce section spacing, not the gutter below 16 px.

## Testing method
Test at 360, 390, 768, 1024, 1440, and 1920 px wide, in portrait and landscape where relevant. Check the layout, the tap targets, and overflow at each. When browser tools are available, take screenshots and inspect `document.documentElement.scrollWidth > clientWidth` to detect overflow.

## Common failures
- Fixed widths in pixels on containers.
- Desktop navigation hidden with `display:none` but no mobile replacement.
- Images with intrinsic size wider than the viewport.
- Sticky elements covering content on small viewports.
- `100vh` on mobile browsers causing hidden bottom content; prefer `100dvh` or flow layouts.
