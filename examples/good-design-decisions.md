# Good Design Decisions (examples)

## 1. Landing page for a photography studio
- **Anchor:** "the light check" — the page opens like a studio schedule, with dated sessions as the organizing structure.
- **Hierarchy:** one large headline with a single booking action; supporting packages below in a two-column layout on desktop, one column on phones.
- **Type:** a condensed display face for headings, a neutral sans for body at 17 px with 1.6 line height.
- **Color:** warm off-white surface, near-black text, one accent used only for the primary action and focus ring.
- **Why it works:** the structure matches the business (booking sessions), not a generic hero-plus-three-cards template.

## 2. E-commerce product page
- **Priority:** price, size or variant, and add-to-cart are visible without scrolling on a 390 px phone.
- **Gallery:** fixed 4:5 aspect ratio, swipeable on touch, thumbnails hidden on phones.
- **States:** out-of-stock variants are disabled with a text explanation, not only greyed out.
- **Why it works:** decisions made on the page are supported by the most relevant information first.

## 3. Admin dashboard
- **Structure:** a summary row of four metrics, then a single primary chart, then the data table.
- **Table on phones:** each row becomes a card with the three most important fields; the rest expand on tap.
- **Empty state:** "No bookings this week" with a button to create one, not a blank chart.
- **Why it works:** each view answers one question in order of importance.

## 4. Settings form
- **Layout:** labels above inputs, one column, helper text in muted color below each field.
- **Errors:** appear beside the field on blur and on submit, with a sentence describing the fix.
- **Save feedback:** a polite live-region message "Changes saved", not a modal.
- **Why it works:** clear, predictable, and accessible with keyboard and screen readers.

## 5. Mobile navigation
- **Pattern:** bottom bar with four destinations on phones; the same destinations as a side rail on desktop.
- **Targets:** 48 px tall items with icon and label.
- **Why it works:** primary destinations stay in the thumb zone and the desktop layout uses the space it has.
