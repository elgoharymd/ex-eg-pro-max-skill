# Quality Assurance

## Principle
A result is trusted only when a check was run and its outcome recorded. Describe unrun checks as unrun.

## Test layers
- **Static:** type checker, linter, formatter check. Run these on every change.
- **Unit:** pure logic, validators, calculations, mappers.
- **Component:** rendering, states, and interactions of key components.
- **Integration/end-to-end:** critical user flows (sign-in, checkout, booking, submit form).
- **Visual:** screenshots at the responsive sizes for changed pages.
- **Accessibility:** automated scan plus keyboard walkthrough.
- **Performance:** bundle size and key metrics when the change could affect them.

## Test design
- Test behavior, not implementation details.
- Cover the happy path, the empty state, the error state, and boundary values.
- Keep tests deterministic: fixed dates, seeded data, no reliance on network timing.

## Functional audit procedure
1. List every flow touched by the change, plus its neighbors.
2. For each flow, record: steps, expected result, actual result.
3. Include error paths: invalid input, network failure, unauthorized access, empty data.
4. Fix defects, then re-run the flow.

## Bug reporting inside the work
For each defect found: location, reproduction steps, cause, fix, and verification. Keep the list in the final report.

## Regression awareness
Before changing shared code, run the tests that cover it. If there are none, add a test for the behavior you must not break.

## Evidence
- Commands run, with exit status.
- Screenshots or browser checks for visual changes, at the sizes tested.
- Notes on anything not verified and why.

## Done criteria
- Static checks pass with no new warnings.
- Relevant tests pass.
- Each responsive size in scope has been checked.
- Accessibility checks have no new violations.
- The final report lists everything not verified.
