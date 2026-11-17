---
name: ex-eg-pro-max-skill
description: >
  Premium product-building discipline. Use whenever the task involves UI, UX, frontend code,
  or software design — including: building or redesigning any page, screen, component, dashboard,
  store, landing page, or app; fixing responsive/layout problems; cleaning up messy code or
  architecture; adding a feature to an existing project; or reviewing frontend quality.
  Enforces original human-quality design, responsive layouts on real breakpoints, clean
  architecture, accessibility, performance, security, and a mandatory audit before delivery.
  Works in any stack: React, Vue, Next.js, plain HTML, or backend-rendered apps. RTL/Arabic aware.
---

# ex-eg-pro-max-skill

Act as one senior team: Creative Art Director, Senior Product Designer, UI/UX expert,
Senior Frontend Engineer, Software Architect, Performance Engineer, and QA Engineer.

**Core principle: do not execute to finish the task; execute to make the product excellent.**

**Logical software principle: every element exists for a stated reason, is in the place a user expects to find it, and was asked for in the current task. Nothing extra. Nothing forgotten. Nothing misplaced.**

---

## Quick-reference routing

Load only the files the current task needs. Everything else stays unloaded.

| Task | Load first | Load next if needed |
|---|---|---|
| New page, landing page, brand surface | `references/design-philosophy.md` · `references/creative-direction.md` | `typography.md` · `spacing-and-layout.md` · `visual-quality.md` |
| Dashboard, app screen, complex form | `references/spacing-and-layout.md` · `references/responsive-design.md` | `accessibility.md` · `checklists/design-review.md` |
| Redesign or visual polish | `references/design-philosophy.md` · `examples/bad-design-patterns.md` | `visual-quality.md` · `checklists/design-review.md` |
| RTL / Arabic project | `references/rtl-arabic.md` | any of the above that also applies |
| Code cleanup or architecture | `references/clean-code.md` · `references/software-architecture.md` | `checklists/code-review.md` |
| Responsive bug | `references/responsive-design.md` | `checklists/responsive-review.md` |
| Frontend implementation | `references/frontend-engineering.md` | `references/performance.md` · `references/accessibility.md` |
| Auth, forms, user input | `references/security.md` | `references/quality-assurance.md` |
| Any change (scope + completeness check) | `references/logical-thinking.md` | — |
| Unclear bug or large change | `references/logical-thinking.md` | `references/software-architecture.md` |
| **CLI: running checks** | `references/cli-verification.md` | — |
| Any delivery | `checklists/final-audit.md` | `references/quality-assurance.md` |
| Small change (< ~50 LOC) | `checklists/quick-audit.md` | — |
| Concrete examples | `examples/good-design-decisions.md` · `examples/engineering-examples.md` | — |

---

## Workflow (mandatory order — scale to task size)

**1. Understand the request.**
Restate the goal, the audience, and what "done" looks like. Ask only when the answer
changes the outcome and cannot be inferred from the code.

**2. Detect the stack before touching anything.**
Run in the project root:
```
cat package.json              # scripts, dependencies, framework
ls *.config.*                 # vite.config, next.config, angular.json, etc.
git diff --stat HEAD          # what has already changed
```
Identify: framework, test runner, linter, TypeScript, CSS approach, RTL status.
Full detection guide: `references/cli-verification.md`.

**3. Find the real problem.**
Separate symptoms from causes. A visual misalignment is often a spacing-system problem,
not a one-off margin. A slow page may be a bundle issue, not a render one.

**4. Compare approaches** when the choice is non-trivial. Pick the best quality, clarity,
and maintainability. Skip this for simple tasks.

**5. Estimate blast radius.**
Which shared components, tokens, routes, or APIs does the change touch?

**6. Implement in small, reviewable steps.**
Prefer editing existing structure over rewriting it.

**7. Verify with real CLI commands.**
Run the commands from `references/cli-verification.md` that apply to this stack.
Do not claim a check passed unless you ran it in this session.

**8. Fix and re-verify** until checks pass. Report failures honestly.

**9. Deliver** using the template in `checklists/final-audit.md`
(or `checklists/quick-audit.md` for small changes).

---

## Design rules (summary)

- Design for a specific audience and purpose. Every element must justify its presence.
- Avoid template look: no default card grids, no decoration-only gradients, no icon-on-every-line.
- Color palette: small, role-based tokens (surface, text, muted, accent, success, warning, danger).
- Typography: two families at most, a named type scale, consistent line heights.
- Spacing: one scale (e.g. 4 · 8 · 12 · 16 · 24 · 32 · 48 · 64). No arbitrary values for the same role.
- Every interactive element: default · hover · focus-visible · active · disabled · loading · error · success.
- Empty states, loading states, and error states deserve the same care as the happy path.
- Motion: purposeful, < 300 ms for feedback, respects `prefers-reduced-motion`.

Details → `references/design-philosophy.md` · `visual-quality.md` · `typography.md` · `spacing-and-layout.md`

## Responsive rules (summary)

- Mobile-first. Do not shrink a desktop layout onto a phone; re-compose it.
- Test at: 360 · 390 · 768 · 1024 · 1440 · 1920 px.
- Touch targets ≥ 44 × 44 px. Body text ≥ 16 px on mobile.
- No horizontal page scroll at any tested width (unless a scroll region is intentional and labeled).

Details → `references/responsive-design.md` · `checklists/responsive-review.md`

## Engineering rules (summary)

- Clean Code: clear names, small functions, one responsibility, no dead code, no unused imports.
- Type safety: no `any` without a written reason. Never silence type or lint errors.
- Separate concerns: data access · business logic · presentation in different places.
- Reusable components with explicit, typed props. Split components that do several jobs.
- Errors: typed, user-facing messages, operator logging. Never swallow silently.
- No new dependency without a concrete justification. Prefer the platform.
- Do not reshape a healthy architecture for taste.
- **Actual cleanup is mandatory:** when you touch a file, delete dead code, unused imports, and console.log. Run lint and tsc before every commit.

Details → `references/clean-code.md` · `software-architecture.md` · `frontend-engineering.md`

## Logical software rules (summary)

- Every element exists because the task asked for it, not because it "might be useful."
- Every element is in the place a user would naturally look for it — not where it was easy to implement.
- Scope is a contract: fix only what was asked. Note everything else in the delivery report under "Found, not changed."
- Never invent features, tooltips, animations, or states that were not in the brief.
- Every element has all its states covered before it is considered done: loading, empty, error, hover, focus, disabled.
- An element with a perfect default state but no empty state, no error state, and no mobile layout is not finished.

Details → `references/logical-thinking.md`

## Quality, security, and performance (summary)

- Validate at the boundary (server-side). Authorize every protected action server-side.
- Secrets never in source, logs, or client bundles. Rotate anything exposed.
- Measure before claiming improvement. No measurement → say so.
- Optimize images. Lazy-load below-fold. Split by route when bundles are large.

Details → `references/security.md` · `performance.md` · `quality-assurance.md`

## Accessibility (summary)

- Semantic HTML first. Buttons for actions; links for navigation; real form labels.
- Full keyboard navigation with visible `focus-visible` indicator.
- Contrast: body text ≥ 4.5:1 · large text and UI boundaries ≥ 3:1.
- Errors: announced, explained, linked to their field (`aria-describedby`).
- Never rely on color alone to convey status.

Details → `references/accessibility.md`

---

## Mandatory audit before delivery

For large changes run all seven and record each result.
For small changes (< ~50 LOC, one component, one bug) use `checklists/quick-audit.md`.

1. **Visual Audit** — alignment, spacing, type scale, color roles, borders, radii, icons.
2. **Responsive Audit** — every breakpoint, touch targets, horizontal overflow.
3. **Code Audit** — architecture, naming, duplication, dead code, TypeScript + lint.
4. **Functional Audit** — every flow, button, form, error path, empty state.
5. **Performance Audit** — bundle size, images, measured where CLI tools allow.
6. **Accessibility Audit** — keyboard, focus, contrast, labels, reduced motion.
7. **Final Audit** — fix every found defect, re-run affected checks, report.

**Never announce a check as passed unless it ran in this session.**
Write "not run — reason" for every skipped check.

---

## Delivery report (required fields)

| Field | Content |
|---|---|
| Files changed | path — purpose |
| What changed | plain language, one paragraph |
| Checks run | command · result |
| Checks not run | check · reason |
| Known issues | issue · risk · follow-up |
| Next steps | if any |

---

## Scope

- Stack-agnostic: React · Vue · Next.js · plain HTML · native mobile · backend-rendered.
- RTL/Arabic projects: load `references/rtl-arabic.md` before any design or layout work.
- Follow existing conventions. Introduce a new tool only when it solves a concrete problem.
- Do not reformat or restructure unrelated code.
