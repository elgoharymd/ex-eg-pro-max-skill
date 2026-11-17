# Bad Design Patterns (examples)

## 1. Shrunk desktop layout
**Symptom:** a three-column desktop page becomes three tiny columns on a phone, with 12 px text and 28 px buttons.
**Fix:** re-compose into one column on phones, larger type, full-width buttons with 44 px height.

## 2. Gradient-and-glass template
**Symptom:** purple gradient background, frosted cards, and drop shadows on every element.
**Fix:** a restrained surface color, one accent, borders for separation, and shadows only on floating elements.

## 3. Pixel patching
**Symptom:** `margin-top: 13px` added to one element to fix a gap, which breaks at another width.
**Fix:** find the spacing token or layout rule that is responsible and correct it at the source.

## 4. Icon on everything
**Symptom:** every menu item, heading, and list item has an icon, so none of them stands out.
**Fix:** use icons only where they clarify meaning or speed scanning; keep the rest text-only.

## 5. Placeholder content left in place
**Symptom:** "Lorem ipsum", "John Doe", or "$0.00" metrics in a delivered page.
**Fix:** use realistic copy and data, or clearly mark sample data as sample.

## 6. Div-buttons
**Symptom:** `<div onClick>` styled as a button, with no keyboard support or role.
**Fix:** use a `button` element; it provides focus, keyboard activation, and role automatically.

## 7. Missing states
**Symptom:** a list that shows nothing when empty, or a form that gives no feedback while saving.
**Fix:** design empty, loading, and error states with a message and a next action.

## 8. Tiny touch targets
**Symptom:** a 20 px close button in a corner on a phone.
**Fix:** a 44 px target with an accessible name, placed where the thumb reaches.

## 9. Hover-only reveal
**Symptom:** actions appear only on hover, so touch users cannot reach them.
**Fix:** show actions by default on touch, or put them behind a visible menu button.

## 10. Architecture by reflex
**Symptom:** a "utils" folder with 40 unrelated functions, and components that import from each other in loops.
**Fix:** group code by feature, move business rules into a domain layer, and remove unused helpers.
