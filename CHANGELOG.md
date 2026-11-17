# Changelog

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
