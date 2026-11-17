# ex-eg-pro-max-skill

A Claude Code skill that makes Claude work as a senior product team: art direction, product design, UI/UX, frontend engineering, software architecture, performance, and QA. It enforces original human-quality design, responsive layouts built for each screen size, clean code, accessibility, and a documented audit before any work is reported as finished.

> **Principle:** do not execute to finish the task; execute to make the product excellent.

## What it covers

- Landing pages, online stores, dashboards, and application screens
- Redesigns of existing interfaces
- Code cleanup and architecture review
- Responsive bug fixing
- Adding components to existing projects

It is not tied to one framework. It works with plain HTML, React, Vue, Next.js, native mobile, and backend-rendered apps.

## Structure

```
ex-eg-pro-max-skill/
├── SKILL.md              # Entry point: workflow, summaries, audit rules
├── references/           # Detailed rules, loaded per task
├── checklists/           # Review and audit checklists
├── examples/             # Good and bad patterns, engineering examples
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
└── .gitignore
```

Claude reads `SKILL.md` first and loads the reference, checklist, and example files only when the task needs them. This keeps context small.

## Installation

### Project-level (recommended for one codebase)

Copy the skill folder into the project:

```bash
mkdir -p .claude/skills
cp -r ex-eg-pro-max-skill .claude/skills/ex-eg-pro-max-skill
```

The skill is then available inside that project as `/ex-eg-pro-max-skill`.

### User-level (available in every project)

```bash
mkdir -p ~/.claude/skills
cp -r ex-eg-pro-max-skill ~/.claude/skills/ex-eg-pro-max-skill
```

On Windows PowerShell, use `$HOME\.claude\skills\` instead of `~/.claude/skills/`.

### Verify

Start Claude Code in the project and run:

```bash
claude
```

Then ask for a task, or invoke the skill directly with `/ex-eg-pro-max-skill`.

## Usage examples

- "Build a premium landing page for a photography studio. Use ex-eg-pro-max-skill."
- "Fix the responsive issues on the products page."
- "Clean up the booking module without changing behavior."

## Requirements

None beyond Claude Code. Verification steps use whatever the project already has (type checker, linter, tests, a browser). The skill tells Claude to record any check it could not run.

## License

MIT. See [LICENSE](LICENSE).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Changes are recorded in [CHANGELOG.md](CHANGELOG.md).
