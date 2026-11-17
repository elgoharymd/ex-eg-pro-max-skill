# Contributing

Thank you for improving ex-eg-pro-max-skill.

## Ground rules
- Keep `SKILL.md` short. It is the entry point and must stay readable at a glance. Put detail in `references/`.
- Each rule should be specific and checkable. Replace general advice ("make it look good") with a concrete rule ("body text ≥ 16 px on mobile").
- Do not duplicate content across files. Link instead.
- Do not add framework-specific rules to the core files. Put framework notes in `references/frontend-engineering.md` under a clearly labeled section, or in a new reference file.
- Every example must be realistic and correct.

## Process
1. Open an issue describing the problem or addition.
2. Fork and create a branch.
3. Make the change and update `CHANGELOG.md` under "Unreleased".
4. Validate:
   - Every `references/`, `checklists/`, and `examples/` link in `SKILL.md` and `README.md` resolves to a file.
   - The frontmatter of `SKILL.md` has `name` and `description`, and `name` matches the folder name.
   - Code samples are syntactically valid for their language.
5. Open a pull request with a short description of what changed and why.

## Style
- Plain language. Short sentences. Tables only where they compare values.
- Arabic and English may both be used in examples, but rule names stay in English so they remain searchable.

## Versioning
- Patch: typo fixes and clarifications.
- Minor: new reference, checklist, or example.
- Major: changes to the workflow or to required outputs.
