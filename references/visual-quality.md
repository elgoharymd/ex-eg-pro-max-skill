# Visual Quality

## Color system
- Define tokens on the root, for example `--color-surface`, `--color-surface-raised`, `--color-text`, `--color-text-muted`, `--color-accent`, `--color-accent-contrast`, `--color-border`, `--color-success`, `--color-warning`, `--color-danger`, `--color-focus`.
- Components reference roles, never raw hex values.
- Provide light and dark values, or document why only one theme exists.
- Check contrast: body text ≥ 4.5:1; large text and UI boundaries ≥ 3:1.
- Use neutrals with a slight tint of the brand hue for a cohesive feel; avoid pure black on pure white for long text.

## Borders, radii, shadows
- Use one radius scale (for example 4, 8, 12, 16). Nested elements use a smaller radius than their container.
- Shadows come from a small scale (sm, md, lg). Use a border before a shadow when separation is enough.
- Do not stack multiple shadows or use heavy blur for decoration.

## Iconography
- One icon set, one stroke width, one optical size per context (e.g., 16, 20, 24 px).
- Icons align to the text's cap height or line box; check optically, not just numerically.
- Icon-only buttons have an accessible name and a tooltip.

## Imagery
- Set explicit aspect ratios to prevent layout shift.
- Use `object-fit: cover` for thumbnails and check focal point on mobile crops.
- Provide `alt` text that describes purpose, or empty `alt` for decorative images.
- Serve modern formats where the build supports them, with sensible dimensions.

## Detail checklist
- Baselines and vertical rhythm line up across columns.
- Dividers and borders are the same weight throughout.
- Corners of adjacent elements meet cleanly.
- Numbers use tabular figures where columns of values align.
- No orphaned single word at the end of a headline on desktop, where it is easy to avoid.
