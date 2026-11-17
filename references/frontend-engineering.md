# Frontend Engineering

## Structure
- Keep feature folders self-contained: components, hooks, data access, and tests together.
- Separate presentational components (props in, markup out) from containers that fetch data or manage state.
- Put shared primitives (button, input, card, dialog) in one design-system layer, not copied per page.

## Components
- One clear responsibility per component. If a component has three unrelated jobs, split it.
- Props are typed, minimal, and named for purpose (`onSelect`, not `handleClick2`).
- Avoid boolean prop explosions; prefer variants (`variant="primary" | "ghost"`).
- Keep component files under about 200 lines as a guideline; split when a file grows past that for good reason.

## State
- Keep state as local as possible. Lift only when two siblings need it.
- Derive values instead of storing them when they can be computed.
- Server data is cached and revalidated with a dedicated mechanism, not copied into local state.

## Styling
- Use the project's existing approach (CSS modules, utility classes, styled system). Do not mix systems within one component.
- Reference tokens, not literal values.
- Avoid deeply nested selectors that couple components to page structure.

## Accessibility in components
- Use native elements first. A `div` with `onClick` is a defect unless it is given full keyboard and role semantics.
- Every form control has a visible label.
- Manage focus when opening and closing dialogs and when routes change.

## States every component must handle
Default, hover, focus-visible, active, disabled, loading, empty, error, success. Check each one visually.

## Data and async
- Show a loading state that matches the layout (skeleton with the same dimensions) rather than a spinner in an empty box.
- Handle empty results with a message and a next action.
- Handle errors with a human message, a retry action when safe, and details only for developers.

## Quality tooling
- Run the type checker with strict settings where the project supports it.
- Run the linter and fix warnings rather than suppressing them.
- Keep unit tests for logic, component tests for behavior, and visual or end-to-end checks for key flows.

## Dependencies
- Prefer platform features (native dialog, `fetch`, CSS `:has`, container queries) when they meet the requirement and the browser support target.
- Before adding a library, check bundle cost, maintenance status, and whether a few lines of code would do.
