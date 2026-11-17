# Final Audit

Run every section before delivery. For each item, record Pass, Fail (fixed), Fail (open, with reason), or Not run (with reason). A Fail that is not fixed must appear in the report.

## 1. Visual Audit
- [ ] Spacing uses the scale; alignment verified on each screen.
- [ ] Type scale and weights consistent across pages.
- [ ] Color roles and contrast verified.
- [ ] Radii, borders, shadows, and icon sizes consistent.

## 2. Responsive Audit
- [ ] Checked at 360, 390, 768, 1024, 1440, 1920 px (see `responsive-review.md`).
- [ ] No horizontal page overflow.
- [ ] Touch targets ≥ 44 px.

## 3. Code Audit
- [ ] Type checker: command and result recorded.
- [ ] Linter: command and result recorded.
- [ ] No dead code, unused imports, or unjustified `any`.
- [ ] Architecture boundaries respected; blast radius reviewed.

## 4. Functional Audit
- [ ] Every changed flow tested: happy path, empty state, error state, unauthorized access.
- [ ] All buttons, links, forms, and dialogs behave as expected.
- [ ] Tests run: command and result recorded.

## 5. Performance Audit
- [ ] Bundle or asset size checked against budget, or "not measured".
- [ ] Images sized and lazy-loaded where appropriate.
- [ ] No layout shift from late-loading media.

## 6. Accessibility Audit
- [ ] See `accessibility-review.md`.
- [ ] Automated scan result recorded, or "not run".

## 7. Security and Hygiene
- [ ] No secrets or keys in code, config committed to git, or client bundles.
- [ ] `.gitignore` covers env files and build output.
- [ ] Dependencies reviewed for new additions.

## 8. Fixes and re-tests
- [ ] Every Fail re-tested after the fix.
- [ ] Re-test results recorded.

---

## Report template

**Files created or changed**
- `path` — purpose

**What changed**
- Short description in plain language.

**Checks run**
| Check | Command or method | Result |
|---|---|---|
| Type check | `...` | pass / fail (details) |
| Lint | `...` | ... |
| Tests | `...` | ... |
| Responsive | widths tested | ... |
| Accessibility | tool or manual | ... |

**Checks not run**
- Check — reason.

**Known issues and risk**
- Issue — impact — suggested follow-up.

**Next steps**
- ...
