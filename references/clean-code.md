# Clean Code

## Naming
- Names describe the domain meaning: `sessionStartsAt`, not `d1` or `dataTemp`.
- Booleans read as questions: `isOpen`, `hasPermission`, `canEdit`.
- Functions are verbs; types and components are nouns.
- Avoid abbreviations unless they are universal in the project (`id`, `url`).

## Functions
- Do one thing at one level of abstraction.
- Prefer early returns over deep nesting.
- Limit parameters; group related ones into an object when more than three.
- No hidden side effects in functions named like pure reads.

## Duplication
- Duplicate code is acceptable for two occurrences if they may diverge. Extract on the third occurrence, or sooner when the logic is a business rule that must stay identical.
- Extract by meaning, not by similar shape.

## Dead code
- Delete unused functions, exports, props, CSS classes, feature flags, and commented-out blocks. Git keeps history.
- Remove unused imports and variables; the linter should enforce this.

## Comments
- Explain *why*, not *what*. The code should say what it does.
- Keep TODOs with an owner or ticket, or remove them.
- Do not leave comments that contradict the code.

## Types and errors
- Avoid `any`. Use `unknown` and narrow it.
- Model states explicitly (`status: 'idle' | 'loading' | 'error' | 'success'`) instead of several booleans that can disagree.
- Throw or return typed errors with a code and a message; never swallow errors silently.

## Formatting and tooling
- Follow the project's formatter and linter config. Do not argue style in a PR that the tool already decides.
- Fix warnings. Do not add disable comments unless they are narrow, justified, and explained.

## Quick self-review
- Could a new team member explain this file in two sentences?
- Is there any code I can delete without changing behavior?
- Would the next change in this area be easy?
