# Changelog

## v1.3.0 — 2026-11-17

### Added
- `references/visual-assets.md` — icons as AI-generated images (Gemini/ChatGPT). No SVG libraries. No inline SVG icons. Includes style prefix system, prompt templates, file naming, code usage, and consistency rules.
- `references/pro-suggestions.md` — mandatory 3–5 proactive improvement suggestions after every delivery. Defines strong vs weak suggestions, format, categories, and tone.

### Changed
- `references/creative-direction.md` — added originality mandate ("design must be unrecognizable as AI output"), "unexpected angle" method, and reference to `visual-assets.md` and `pro-suggestions.md`.
- `references/typography.md` — added "No AI-looking fonts" section with explicit blacklist (Inter, DM Sans, Plus Jakarta Sans, Nunito, Outfit, Poppins, Lexend, Rubik, Montserrat, Raleway and Arabic equivalents) and curated whitelist of fonts with character and history for Latin and Arabic.
- `references/design-philosophy.md` — added "AI-unrecognizable" test, banned fonts and SVG icon libraries in the "Human, not generated" section.
- `SKILL.md` — added originality and icon rules to Design rules summary, added `visual-assets.md` routing row, made suggestions mandatory in delivery report format.

---

## v1.2.0 — 2026-11-17

### Added
- `references/logical-thinking.md` expanded with Three Questions test, element placement rules, scope contract, and complete element state coverage checklist.
- `references/clean-code.md` expanded with mandatory "Actual cleanup" section.
- `checklists/quick-audit.md` expanded with point 6: logical placement + complete states check.
- `SKILL.md` — added "Logical software principle" and "Logical software rules" summary section.

---

## v1.1.0 — 2026-11-17

### Added
- `references/cli-verification.md` — actual shell commands for every check (tsc, eslint, vitest, jest, playwright, build, bundle size, git hygiene). Includes stack-detection fingerprints and a project-specific sequence for Vite + React + TypeScript + Vitest.
- `references/rtl-arabic.md` — comprehensive RTL and Arabic UI reference: logical CSS properties, Arabic typography (Readex Pro, line-height, no letter-spacing), icon mirroring, bidirectional text, form alignment, number/date formatting, and a table of common RTL bugs.
- `checklists/quick-audit.md` — 5-point fast audit for changes under ~50 LOC. Delivers in under 5 minutes; replaces the full 7-part audit for small fixes.

### Changed
- **`SKILL.md`** — rewritten for CLI efficiency:
  - `description` frontmatter is tighter and more trigger-precise.
  - Workflow step 2 now includes actual `cat`/`ls`/`git diff` commands for stack detection.
  - Routing table adds rows for RTL/Arabic projects, CLI checks, and quick-audit.
  - Mandatory audit section now explicitly routes small changes to `quick-audit.md`.
  - All summary sections kept; references unchanged.

---

## v1.0.0 — 2026-11-12

Initial release. 23 files covering design philosophy, creative direction, visual quality,
typography, spacing, responsive design, frontend engineering, software architecture, clean code,
logical thinking, accessibility, performance, security, and quality assurance, plus five
checklists and three example files.
