# Professional Improvement Suggestions

## Purpose

After every delivery, generate 3–5 proactive professional improvement suggestions for the user.
These are not corrections of what was built — they are forward-looking opportunities to make the product significantly better.

**This is mandatory.** It is not optional and is not skipped for small tasks.

---

## The standard

Suggestions must meet all of these:

1. **Specific** — grounded in what was actually seen in this project (the code, the data model, the user flow). Not generic advice that could apply to any product.
2. **Prioritized by impact** — lead with the highest-value suggestion.
3. **Actionable** — the user can decide yes/no and delegate implementation immediately.
4. **Professional level** — the kind of suggestion a senior product designer or lead engineer would make, not a junior checklist item.
5. **Brief** — each suggestion is 2–4 sentences. Not a paragraph. Not a list of sub-points.

---

## Categories to draw from

Pull suggestions from whichever are most relevant to this product:

**UX improvements**
- Flow shortcuts the user may not have considered
- Confusion points (steps that require extra cognitive load)
- Feedback missing at key moments (success confirmation, progress indicators)
- Navigation patterns that could be simplified
- Empty states that could be made actionable instead of passive

**Visual design**
- A design system inconsistency observed across pages
- A component that could be consolidated (two similar components doing the same job)
- A spacing or hierarchy problem that makes the page harder to scan
- A typographic choice that could better reflect the brand character
- A color usage that dilutes the accent's meaning

**Engineering quality**
- A pattern that will cause scaling problems (N+1 queries, loading whole lists into memory, etc.)
- A missing state (loading/error/empty) that will show broken UI in production
- A component that is doing too many jobs and should be split
- A type safety gap that is likely to cause a bug
- A missing test for a critical path

**Performance**
- An unoptimized image or asset loading path
- A bundle chunk that could be lazy-loaded
- A render cycle that could be reduced with memoization or key management

**Accessibility**
- A keyboard navigation gap
- A missing focus indicator
- A label that is implied but not programmatic

**Features grounded in the product**
- A next natural feature based on the product's actual workflow (not a generic "add analytics")
- An automation that would save the user's team real time
- An integration that is implied by the data model (e.g., "you're storing X — you could export to Y")

---

## Format

```
## Suggested Improvements

**1. [Suggestion title] — [category]**
[2–3 sentences: what it is, why it matters for this specific product, how hard it is to implement]

**2. [Suggestion title] — [category]**
[...]

**3. [Suggestion title] — [category]**
[...]
```

---

## Examples of strong vs weak suggestions

**Weak (generic, could apply to any product):**
> "Consider adding dark mode."
> "You could improve performance by lazy-loading images."
> "Think about adding a search feature."

**Strong (specific, grounded in what was seen):**
> "The booking list currently loads all bookings for the day in one query. When a studio has 30+ bookings, this will cause visible latency. Paginating by room (the natural unit users already filter by) would cut the initial load to 5–8 rows and avoid the problem before it appears."

> "The 'needs follow-up' status has no path to resolution from the booking list — users see the alert but must navigate to the full booking to change the status. Adding an inline action button directly on the row would eliminate that round-trip and likely increase the follow-up resolution rate."

> "The TodayStrip timeline shows no visual distinction between bookings that are currently in progress versus upcoming. A subtle highlight or the now-marker's color reflected onto the active booking bar would give the manager an immediate read of what's happening right now."

---

## Tone

- Direct, confident, specific.
- Do not hedge with "you might want to consider" or "perhaps." Say: "This will cause X. The fix is Y."
- Do not apologize or frame as criticism. These are opportunities, presented by a senior colleague.
- In Arabic products, write the suggestions in Arabic if the conversation is in Arabic.
