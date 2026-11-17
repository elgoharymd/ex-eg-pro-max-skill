# Accessibility Review Checklist

## Structure
- [ ] One `h1` per page; heading levels are logical.
- [ ] Landmarks present: header, nav, main, footer.
- [ ] Lists and tables use correct semantics.

## Keyboard
- [ ] All interactive elements reachable with Tab and operable with Enter/Space.
- [ ] Focus order matches visual order.
- [ ] Dialogs trap focus, close with Escape, and restore focus.
- [ ] No keyboard traps.

## Focus
- [ ] Visible focus indicator on every focusable element with ≥ 3:1 contrast.
- [ ] Focus is not hidden behind sticky headers.

## Color and contrast
- [ ] Body text ≥ 4.5:1; large text ≥ 3:1.
- [ ] Non-text UI boundaries and focus rings ≥ 3:1.
- [ ] Status is not conveyed by color alone.

## Forms
- [ ] Every control has a programmatic label.
- [ ] Required fields are stated in text.
- [ ] Errors identify the field, explain the problem, and suggest a fix.
- [ ] Error text is associated with its field (`aria-describedby`).
- [ ] Autocomplete and input types are set where relevant.

## Images and media
- [ ] Meaningful images have descriptive alt text; decorative images have empty alt.
- [ ] Video has captions; autoplay is controlled.

## Motion and zoom
- [ ] `prefers-reduced-motion` respected.
- [ ] Content reflows at 400% zoom without horizontal scroll (for reflowing content).
- [ ] No content flashes more than three times per second.

## Targets
- [ ] Touch targets ≥ 44 × 44 px where practical; never below 24 × 24 px.

## Testing record
- [ ] Automated scan run (tool name and result recorded), or "not run: reason".
- [ ] Keyboard-only walkthrough of primary flows recorded.
- [ ] Screen reader check recorded, or "not run: reason".
