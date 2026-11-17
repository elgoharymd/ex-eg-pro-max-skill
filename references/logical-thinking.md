# Logical Thinking

## Purpose
Prevent two failures: rushing into a fix that treats a symptom, and overanalyzing a simple task until nothing ships.

---

## Core method

1. **Restate the goal** in one sentence, in the user's terms.
2. **Gather facts.** Read the relevant files and reproduce the problem if possible. Note what you observed, not what you assume.
3. **Locate the cause.** Ask "why" until the answer is a mechanism, not a symptom.
   > "The button is misaligned" → "its container uses fixed width" → "the grid column is 280 px" → "the grid does not shrink below that on phones".
4. **List options.** Usually two or three, including the minimal one.
5. **Score options** on: correctness, clarity, maintenance cost, risk to other parts, and performance.
6. **Choose and state the reason** in one or two sentences.
7. **Predict side effects** before editing: which callers, tokens, or routes change.
8. **Implement**, then **verify** against the prediction.

---

## Logical software — every element must earn its place

A logical product is one where every element, feature, and decision is there for a clear reason. Apply this test before writing or keeping any code, layout, or UI element:

**The Three Questions:**
1. **Why does this exist?** — Is it serving a user need stated in the request?
2. **Why is it here?** — Is this the most natural location for a user to expect it?
3. **Why now?** — Was it asked for in this task, or is it anticipating a future need?

If any answer is "I thought it might be useful" or "just in case" — remove it.

### Element placement rules

Every UI element belongs in exactly one logical location. Test placement with this question: *Where would the user look for this?*

| Element type | Belongs in |
|---|---|
| Primary action | Most prominent position in the view (top-right in RTL, or end of a form) |
| Destructive action | Secondary position, requires confirmation, never the default |
| Navigation | Persistent, always in the same location across pages |
| Filter / sort | Adjacent to what it filters, never on a different section |
| Status indicator | Next to the entity it describes, not at the top of the page |
| Settings | Settings section, not on data tables or list items |
| Error message | Adjacent to the field or action that caused it |
| Empty state | In the container that is empty, not outside it |
| Loading state | Exactly where the data will appear, same dimensions |

Violation: a "refresh" button on a page header when only one section needs refreshing. The button belongs next to that section.

### Scope contract — do not go beyond the task

The task defines a hard boundary. Nothing outside it changes in the same commit.

**Allowed:**
- Fixing exactly what was asked.
- Fixing a critical defect directly caused by the change (and noting it in the report).
- Noting unrelated issues in the delivery report as "found, not changed."

**Not allowed:**
- Renaming variables unrelated to the task.
- Refactoring adjacent components "while I'm here."
- Adding features that were not requested, even if they seem useful.
- Improving code style in files the task did not need to touch.

**When you find a real problem outside scope:** note it. Write it in the delivery report under "Found, not changed." Do not silently fix it in the same change — that creates invisible diff noise and breaks the ability to bisect bugs.

### No invented features

A feature not in the request does not exist. These are the most common invented additions to avoid:

- Adding a tooltip to a button that the request never mentioned.
- Adding "while I'm at it" state management because it looks cleaner.
- Adding placeholder text, helper text, or instructional copy that was not in the brief.
- Making something "configurable" or "dynamic" when the task called for a fixed value.
- Adding animations or transitions that were not part of the design.
- Adding loading states or error states beyond what was specifically requested.

---

## Complete element coverage — nothing is forgotten

Every element in a finished design has all of its states designed and implemented. An element is not done until all applicable states are covered:

**Interactive element states (all must be present):**
- Default / idle
- Hover
- Focus-visible (keyboard focus — required for accessibility)
- Active / pressed
- Loading / pending (for async actions)
- Disabled
- Error
- Success / confirmation

**Data-dependent states (all must be present):**
- Loaded (happy path)
- Loading (skeleton or spinner, same dimensions as loaded)
- Empty (meaningful, actionable message)
- Error (with a retry option where it makes sense)
- Partial data (e.g., some rows missing, some fields null)

**Responsive states:**
- Every breakpoint tested (see `responsive-design.md`)
- Every state above tested at mobile size, not just at desktop

**Checklist before marking any component done:**

```
□ Default state: designed and implemented
□ Hover: visible feedback
□ Focus-visible: keyboard navigation works, indicator visible
□ Loading: skeleton or spinner at correct dimensions
□ Empty: message is helpful, not just "No data"
□ Error: message explains what failed, offers retry
□ Disabled: visually distinct, not just opacity-50
□ Mobile layout: re-composed, not just shrunk
```

A component with a beautiful default state but no empty state, no error state, and no mobile layout is not finished. It is half-finished.

---

## Proportionality

- **Trivial** (typo, color token, one-line fix): steps 1, 2, 6, 8, quick check.
- **Medium** (new component, bug with unknown cause): full method, brief notes.
- **Large** (new feature, redesign, architecture): full method, plan, blast-radius list, staged delivery.

---

## Common traps

- **Patch-driven fixes:** adding `margin-top: 13px` to hide a problem caused by the parent layout. Find the real cause.
- **Confirmation bias:** only checking the path you expected to work. Test the failure path.
- **Scope creep:** fixing unrelated code in the same change. Note it and leave it.
- **Premature abstraction:** building a generic system for a second use case that may never come.
- **Invented features:** adding things that were not asked for because they "seem useful."
- **Incomplete states:** shipping a component that only works on the happy path.
- **Wrong location:** putting an element where it is easy to implement, not where the user expects to find it.

---

## When to ask

Ask only when the answer changes the outcome and cannot be found in the code, docs, or conversation: missing business rules, a choice with irreversible cost, a conflict between requirements. Otherwise decide, and state the decision in the delivery report.
