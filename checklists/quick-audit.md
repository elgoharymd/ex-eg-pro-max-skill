# Quick Audit

**Use this for:** small changes — a single bug fix, a one-component update, a copy edit, or anything under ~50 lines of changed code.

For large changes (new page, redesign, new feature, significant architecture change) use `checklists/final-audit.md` instead.

---

## 5-point quick audit

Work through each point. Write the result (✓ pass / ✗ fail / — not applicable) in your delivery report.

---

**1. Does the change do what it was asked to do?**

- Re-read the original request.
- Test the specific scenario it was meant to fix.
- Check that the fix does not regress any adjacent behavior you can see without running the full test suite.

---

**2. Does the code pass type check and lint?**

```bash
npx tsc --noEmit
npx eslint "src/**/*.{ts,tsx}" --max-warnings 0
```

Both must pass. If they were already failing before your change, say so and report the pre-existing count separately.

---

**3. Does it look right on mobile and desktop?**

Open the dev server and check at two widths:
- **390 px** (iPhone-class mobile, RTL layout)
- **1280 px** (laptop)

Specifically:
- No broken layout or overflow.
- Text is readable (≥ 16 px on mobile).
- Interactive target is reachable by touch (≥ 44 px).
- RTL direction is correct — no LTR leakage.

---

**4. Are loading, empty, and error states handled?**

If the change involves data fetching, a form, or a user action:
- Loading: does it show a skeleton or spinner?
- Empty: does it show a meaningful empty state?
- Error: does it show a user-facing message with a retry option?

If the change does not touch data or user actions, mark this — (not applicable).

---

**5. No new lint, type, or accessibility regressions?**

- No new `any` casts introduced.
- No `console.log` left in.
- Interactive elements added? They must have an accessible name, keyboard reachability, and a visible focus indicator.
- Images added? They need `alt` text.

---

## Delivery note for quick changes

```
Change: <one line>
Files: <paths>
Type check: ✓ / ✗ (errors: N)
Lint: ✓ / ✗ (warnings: N)
Build: ✓ / not run (reason)
Visual check: ✓ 390 px + 1280 px / ✗ issue: <describe>
Known issues: none / <describe>
```

Write "not run — reason" for each check you skipped. Do not write ✓ for a check you did not run.
