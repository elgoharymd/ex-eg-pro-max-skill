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
- Duplicate code is acceptable for two occurrences if they may diverge. Extract on the third, or sooner when the logic is a business rule that must stay identical.
- Extract by meaning, not by similar shape.

## Dead code
- Delete unused functions, exports, props, CSS classes, feature flags, and commented-out blocks. Git keeps history.
- Remove unused imports and variables; the linter must enforce this.

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

---

## Actual cleanup — mandatory, not aspirational

Code review in this skill means actual deletions and fixes, not a list of suggestions. When you touch a file, you clean it. These are not optional:

**Always delete before committing:**
```
□ Unused imports (the linter flags these — fix them, do not suppress)
□ console.log, console.warn, debugger statements
□ Commented-out code blocks
□ Variables declared but never read
□ Functions defined but never called (unless exported for external use)
□ CSS classes defined but never referenced in the component
□ Props accepted by a component but never used in its render
□ Dead branches: `if (false)`, `if (process.env.NODE_ENV === 'never')`, etc.
□ TODOs older than the current task (note them in the delivery report, then delete)
```

**Before touching a file, run:**
```bash
npx tsc --noEmit       # find type errors
npx eslint <file>      # find unused imports, unreachable code
```

**After editing, re-run both** and confirm the error/warning count did not increase.

**What "clean" means for a file you just edited:**
- Zero new lint warnings in that file.
- No new `any` casts.
- No dead code you introduced or left behind.
- Every prop and variable has a name that describes its meaning.
- Functions do one thing; if a function grew too large during the edit, split it.

**What "clean" does NOT mean:**
- Reformatting every file in the project.
- Renaming things you did not need to touch.
- Extracting abstractions that were not needed for the current task.
- Fixing pre-existing issues in files outside the change — note those instead.

The scope of cleanup is: the files the task touched, and nothing beyond them.

---

## Quick self-review (run before every delivery)

```
□ Could a new team member explain this file in two sentences?
□ Is there any code I can delete without changing behavior?
□ Would the next change in this area be easy?
□ Are all error paths handled and typed?
□ Are there any console.log statements left?
□ Are there any unused imports, variables, or props?
□ Did I introduce any new `any` casts?
□ Does every component accept only the props it uses?
□ Is the state model explicit (typed union) or implicit (boolean soup)?
```

If any answer is "no" or "maybe," fix it before marking the task done.
