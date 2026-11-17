# Logical Thinking

## Purpose
Prevent two failures: rushing into a fix that treats a symptom, and overanalyzing a simple task until nothing ships.

## Method
1. **Restate the goal** in one sentence, in the user's terms.
2. **Gather facts.** Read the relevant files and reproduce the problem if possible. Note what you observed, not what you assume.
3. **Locate the cause.** Ask "why" until the answer is a mechanism, not a symptom. Example: "The button is misaligned" → "its container uses fixed width" → "the grid column is 280 px" → "the grid does not shrink below that on phones".
4. **List options.** Usually two or three, including the minimal one.
5. **Score options** on: correctness, clarity, maintenance cost, risk to other parts, and performance.
6. **Choose and state the reason** in one or two sentences.
7. **Predict side effects** before editing: which callers, tokens, or routes change.
8. **Implement**, then **verify** against the prediction.

## Proportionality
- Trivial task (typo, color token, one-line fix): steps 1, 2, 6, 8, and a quick check.
- Medium task (new component, bug with unknown cause): full method, brief written notes.
- Large task (new feature, redesign, architecture change): full method, plan and blast-radius list, staged delivery.

## Common traps
- **Patch-driven fixes:** adding a `margin-top: 13px` to hide a spacing problem caused by the parent layout.
- **Confirmation bias:** only checking the path you expected to work.
- **Scope creep:** fixing unrelated code in the same change. Note it and leave it, unless it blocks the task.
- **Premature abstraction:** building a generic system for a second use case.

## When to ask
Ask only when the answer changes the outcome and cannot be found in the code, docs, or conversation: missing credentials, conflicting business rules, a choice with irreversible cost. Otherwise decide, and state the decision in the report.
