# Code Review Checklist

## Correctness
- [ ] The change does what the request asked, and nothing unrelated.
- [ ] Edge cases handled: empty input, null/undefined, large lists, concurrent updates.
- [ ] Errors are handled and surfaced appropriately; none are swallowed.

## Structure
- [ ] Each file and component has one clear responsibility.
- [ ] Business logic is not inside UI handlers or markup.
- [ ] No circular dependencies introduced.
- [ ] Module boundaries respected; no deep imports into other modules' internals.

## Clean code
- [ ] Names are clear and domain-specific.
- [ ] No duplicated logic that should be shared; no premature abstraction.
- [ ] No dead code, unused imports, unused variables, or commented-out blocks.
- [ ] No magic numbers without a named constant when meaning is not obvious.

## Types
- [ ] No `any` without a documented reason.
- [ ] States modeled explicitly; impossible combinations are unrepresentable.
- [ ] External data is validated, not just cast.

## Tooling
- [ ] Type checker passes with no new errors.
- [ ] Linter passes with no new warnings; no new suppression comments without justification.
- [ ] Formatter applied.

## Tests
- [ ] New behavior has tests; changed behavior has updated tests.
- [ ] Tests assert behavior, not implementation details.

## Security
- [ ] Input validated at the boundary; output encoded for its context.
- [ ] Authorization enforced server-side for every protected action.
- [ ] No secrets, tokens, or personal data in code, logs, or client bundles.

## Performance
- [ ] No unbounded queries or unpaginated lists introduced.
- [ ] No expensive work in render paths without measurement.
- [ ] New dependencies justified; bundle impact considered.

## Maintainability
- [ ] A new contributor could understand the change from its code and names.
- [ ] Documentation or README updated if behavior or setup changed.
