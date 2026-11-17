# Accessibility

## Target
Meet WCAG 2.2 AA as the baseline.

## Semantics
- Use landmarks: `header`, `nav`, `main`, `footer`, and `section` with headings.
- One `h1` per page. Heading levels do not skip without reason.
- Lists are real lists. Tables have headers (`th`, `scope`).
- Buttons trigger actions; links navigate. Do not swap them.

## Keyboard
- Every interactive element is reachable and operable with the keyboard.
- Tab order follows the visual order.
- Dialogs trap focus while open, close on Escape, and return focus to the trigger.
- No keyboard traps outside dialogs.

## Focus
- Visible focus indicator on every focusable element, at least 2 px with 3:1 contrast against adjacent colors.
- Do not remove outlines without a replacement.

## Color and contrast
- Body text 4.5:1 minimum; large text (≥ 24 px, or ≥ 18.66 px bold) 3:1.
- UI component boundaries and focus rings 3:1.
- Never convey status by color alone; add text or an icon.

## Forms
- Every input has a programmatic label (`label for`, or `aria-labelledby`).
- Required fields are marked in text, not only with an asterisk.
- Errors appear next to the field, are written in plain language, say how to fix the problem, and are linked with `aria-describedby`.
- Use `aria-live` (polite) for status messages such as "saved".
- Use correct `type`, `autocomplete`, and `inputmode`.

## Images and media
- Meaningful images have descriptive `alt`; decorative images have `alt=""`.
- Videos have captions; autoplaying media is paused by default or can be stopped.

## Motion
- Respect `prefers-reduced-motion`: replace large movement with fades or no motion.
- Avoid flashing content above three flashes per second.

## Touch and zoom
- Targets ≥ 44 × 44 px where practical; at least 24 × 24 px as the WCAG minimum.
- Content works at 200% text zoom and at 400% zoom without horizontal scrolling for reflowing text.

## Testing
- Keyboard-only walkthrough of key flows.
- Automated checks (axe or Lighthouse accessibility) when available; record the result.
- Screen reader spot check on the main flow when available; if not, say so.
