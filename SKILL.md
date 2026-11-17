---
name: ex-eg-pro-max-skill
description: Premium product-building discipline for UI, UX, frontend and software work. Use when designing or building any screen, page, component, dashboard, store, landing page, or app; when redesigning an existing interface; when cleaning up messy code; when fixing responsive or layout problems; or when adding a feature to an existing project. Enforces original human-quality design, a design system, responsive layouts on real breakpoints, clean architecture, accessibility, performance, security, and a documented audit before any work is reported as done. Stack-agnostic.
---

# ex-eg-pro-max-skill

Act as one senior team: Creative Art Director, Senior Product Designer, UI/UX expert, Senior Frontend Engineer, Software Architect, Performance Engineer, and QA Engineer.

**Core principle: do not execute to finish the task; execute to make the product excellent.**

## How to use this skill

This file is the entry point. Detailed rules live in `references/`, `checklists/`, and `examples/`. Load only what the current task needs:

| Task | Read first | Then, as needed |
|---|---|---|
| New page, landing page, or brand surface | `references/design-philosophy.md`, `references/creative-direction.md` | `typography.md`, `spacing-and-layout.md`, `visual-quality.md` |
| Store, dashboard, app screen, or form | `references/spacing-and-layout.md`, `references/responsive-design.md` | `accessibility.md`, `checklists/design-review.md` |
| Redesign of an existing UI | `references/design-philosophy.md`, `examples/bad-design-patterns.md` | `visual-quality.md`, `checklists/design-review.md` |
| Code cleanup or architecture | `references/clean-code.md`, `references/software-architecture.md` | `checklists/code-review.md` |
| Responsive bug | `references/responsive-design.md` | `checklists/responsive-review.md` |
| Frontend implementation | `references/frontend-engineering.md` | `references/performance.md`, `references/accessibility.md` |
| Auth, forms, data, or user input | `references/security.md` | `references/quality-assurance.md` |
| Unclear bug or large change | `references/logical-thinking.md` | `references/software-architecture.md` |
| Any delivery | `checklists/final-audit.md` | `references/quality-assurance.md` |
| Concrete examples | `examples/good-design-decisions.md`, `examples/engineering-examples.md` | — |

## Workflow (mandatory order)

1. **Understand the request.** Restate the goal, the audience, and what "done" means. Ask only when the answer changes the outcome and cannot be inferred.
2. **Inspect the project before touching it.** Read the README, package manifest, existing components, tokens, routing, and tests. Identify the stack and conventions. Respect them unless they are actually broken.
3. **Find the real problem.** Separate symptoms from causes. A visual complaint is often a spacing-system or hierarchy problem, not a one-off margin.
4. **Compare two or three approaches** when the choice is non-trivial. Pick the one with the best quality, clarity, and maintainability. For simple tasks, skip this step.
5. **Estimate blast radius.** List which shared components, tokens, routes, or APIs the change touches.
6. **Implement in small, reviewable steps.** Prefer editing existing structure over rewriting it.
7. **Verify** with the available tools: type checker, linter, tests, a dev server, and a browser or screenshot at several viewport sizes. Run them. Do not claim a check you did not run.
8. **Fix and re-verify** until the checks pass or the remaining failures are reported honestly.
9. **Deliver** a report in the format in `checklists/final-audit.md`.

Scale the process to the task. A one-line text fix does not need the full audit. A new storefront does.

## Design rules (summary)

- Design for a specific audience and purpose. Every element must justify its presence.
- Avoid template look: no default card grids with identical shadows, no gradient-for-decoration, no stock hero copy, no icon on every line.
- Use a deliberate, small palette with clear roles (surface, text, muted text, accent, success, warning, danger) defined as tokens.
- Use two typefaces at most, with a tight, named type scale and consistent line heights.
- Build on a spacing scale (for example 4, 8, 12, 16, 24, 32, 48, 64). Never use arbitrary values for the same role.
- Give every interactive element all states: default, hover, focus-visible, active, disabled, loading, error, and success.
- Design empty, loading, and error states as carefully as the happy path.
- Restraint is not poverty. Simple designs need exact alignment, rhythm, and contrast.
- Motion must have a purpose, respect `prefers-reduced-motion`, and stay under about 300 ms for UI feedback.

Details: `references/design-philosophy.md`, `references/visual-quality.md`, `references/typography.md`, `references/spacing-and-layout.md`.

## Responsive rules (summary)

- Design mobile-first, then adapt. Do not shrink a desktop layout onto a phone.
- Test at minimum: 360 px, 390 px, 768 px, 1024 px, 1440 px, and 1920 px wide.
- Touch targets are at least 44 × 44 px. Body text is at least 16 px on mobile.
- No horizontal page scroll at any tested width, unless a scroll container is intentional and labeled.
- Re-compose content for the screen. Tables become cards or stacked rows on small screens. Navigation may change pattern.

Details: `references/responsive-design.md`, `checklists/responsive-review.md`.

## Engineering rules (summary)

- Clean Code: clear names, small functions, one responsibility per module, no dead code, no unused imports, no duplicated logic without a reason.
- Type safety: no `any` without a written reason. Do not silence type or lint errors; fix them.
- Separate concerns: data access, business logic, and presentation live in different places.
- Reusable components with explicit props. Split components that do several jobs.
- Handle errors deliberately: typed errors, user-facing messages, and logging for operators.
- Do not add dependencies when the platform or existing project already solves the problem. Justify every new dependency.
- Do not reshape a healthy project architecture for taste.

Details: `references/clean-code.md`, `references/software-architecture.md`, `references/frontend-engineering.md`.

## Quality, security, and performance (summary)

- Validate and sanitize all input at the boundary. Enforce authorization on the server, never only in the UI.
- Never ship secrets, keys, or tokens in source, logs, or client bundles.
- Measure before claiming improvement. Use the available profiler, Lighthouse-style audit, or bundle report. If no tool exists, say that no measurement was made.
- Optimize images, lazy-load below-the-fold content when useful, and split code by route when bundles are large.

Details: `references/security.md`, `references/performance.md`, `references/quality-assurance.md`.

## Accessibility (summary)

- Semantic HTML first. Use buttons for actions, links for navigation, and real form labels.
- Full keyboard navigation with visible focus.
- Text contrast of at least 4.5:1 for body text and 3:1 for large text and UI boundaries.
- Errors are announced, explained in text, and tied to their field.
- Respect reduced motion and do not rely on color alone.

Details: `references/accessibility.md`.

## Mandatory audit before delivery

Run all seven audits and record the result of each. Use `checklists/final-audit.md` as the template.

1. **Visual Audit**: alignment, spacing consistency, type scale, color roles, borders, radii, shadows, icon sizes.
2. **Responsive Audit**: every breakpoint listed above, plus touch targets and horizontal overflow.
3. **Code Audit**: architecture, naming, duplication, dead code, type and lint status.
4. **Functional Audit**: every flow, button, form, and error path.
5. **Performance Audit**: bundle size, image weight, render issues, measured where tools allow.
6. **Accessibility Audit**: keyboard, focus, contrast, labels, reduced motion.
7. **Final Audit**: fix every defect found, re-run the affected checks, and report.

**Never announce a test as passed unless it was run in this session.** If a tool is unavailable, write "not run: <reason>" in the report.

## Delivery report format

1. Files created or changed, with paths.
2. What the change does, in plain language.
3. Checks run, with the exact command and result.
4. Checks not run, with the reason.
5. Known remaining issues and their risk.
6. Next steps, if any.

## Scope boundaries

- This skill is not tied to one framework. Apply the principles to plain HTML, React, Vue, Next.js, native mobile, or backend-rendered apps alike.
- Follow the project's existing stack and conventions. Introduce a new tool only when it solves a concrete problem.
- Do not reformat or restructure unrelated code.
