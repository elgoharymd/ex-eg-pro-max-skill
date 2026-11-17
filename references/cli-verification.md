# CLI Verification

Run these commands in the project root before claiming any check passed.
Write every result — including the exact command and its output status — in the delivery report.

---

## Stack detection

Run these first on any project you have not seen before:

```bash
# Framework and scripts
cat package.json | grep -E '"name"|"scripts"|"dependencies"|"devDependencies"' -A 30

# Config files fingerprint
ls *.config.* tsconfig*.json .eslintrc* vitest.config* jest.config* tailwind.config* 2>/dev/null

# Git: what already changed
git diff --stat HEAD
git status --short

# TypeScript: check if strict mode is on
cat tsconfig.json | grep '"strict"'
```

**Framework fingerprints:**

| File found | Framework |
|---|---|
| `vite.config.*` | Vite (React, Vue, Svelte, Vanilla) |
| `next.config.*` | Next.js |
| `angular.json` | Angular |
| `nuxt.config.*` | Nuxt |
| `svelte.config.*` | SvelteKit |
| `astro.config.*` | Astro |
| `remix.config.*` or `vite.config.ts` + `@remix-run/` | Remix |
| none of the above, `index.html` at root | Plain HTML / Vanilla |

**Test runner fingerprints:**

| devDependency | Runner |
|---|---|
| `vitest` | `npx vitest run` |
| `jest` | `npx jest --passWithNoTests` |
| `@testing-library/react` + vitest | `npx vitest run` |
| `playwright` or `@playwright/test` | `npx playwright test` |
| `cypress` | `npx cypress run --headless` |

---

## TypeScript

```bash
# Type check without emitting (fastest)
npx tsc --noEmit

# Type check a specific file and its imports
npx tsc --noEmit --file src/pages/SomePage.tsx

# Check strict mode adherence
npx tsc --noEmit --strict
```

**What to look for:** any error. Zero errors = pass. Report the error count if it fails.

---

## ESLint

```bash
# Check the whole src directory, fail on warnings too
npx eslint "src/**/*.{ts,tsx,js,jsx}" --max-warnings 0

# Check a single file
npx eslint src/pages/SomePage.tsx --max-warnings 0

# If using flat config (eslint.config.*)
npx eslint src/ --max-warnings 0
```

**What to look for:** zero errors, zero warnings. If the project has pre-existing warnings, run with `--max-warnings` set to the current count and note it.

---

## Tests

```bash
# Vitest
npx vitest run

# Vitest with coverage
npx vitest run --coverage

# Jest
npx jest --passWithNoTests

# Playwright (integration)
npx playwright test

# Run only tests related to changed files (Vitest)
npx vitest related src/pages/SomePage.tsx --run
```

---

## Build

```bash
# Vite
npm run build

# Next.js
npm run build

# Check the build output for unexpected size changes
# (run after npm run build)
ls -lh dist/assets/          # Vite
ls -lh .next/static/chunks/  # Next.js
```

**Bundle size quick check (Vite):**
```bash
npm run build 2>&1 | grep -E "kB|KB|MB|gzip"
```
Flag any JS chunk over 300 KB (gzip) as a potential issue.

---

## Package scripts (project-specific)

```bash
# List all defined scripts
cat package.json | grep -A 20 '"scripts"'

# Common patterns:
npm run lint        # may be configured differently from raw eslint
npm run typecheck   # may alias tsc --noEmit
npm run test        # may run vitest or jest
npm run check       # Svelte/Astro combined type+lint
```

Always prefer the project's own `npm run lint` / `npm run test` over direct `npx` calls when both exist — the project's script may set env vars or flags that matter.

---

## CSS / Styling checks

```bash
# Stylelint (if configured)
npx stylelint "src/**/*.css" --max-warnings 0

# Check for horizontal overflow (manual — open the app and run in browser console)
# document.querySelectorAll('*').forEach(el => {
#   if (el.scrollWidth > el.clientWidth) console.log(el);
# });
```

---

## Accessibility (CLI)

```bash
# axe-core via CLI (if installed)
npx axe http://localhost:5173 --exit

# pa11y
npx pa11y http://localhost:5173
```

These require the dev server running. Note if they cannot be run.

---

## Performance

```bash
# Bundle analysis — Vite
npm run build -- --mode production
# Then open: dist/stats.html (if rollup-plugin-visualizer is configured)

# Lighthouse CLI (requires Chrome)
npx lighthouse http://localhost:5173 --output=json --quiet | grep '"score"' | head -6

# Check image sizes in the build
find dist -name "*.png" -o -name "*.jpg" -o -name "*.jpeg" -o -name "*.webp" | xargs ls -lh
```

---

## Git hygiene before committing

```bash
# See exactly what will be staged
git diff HEAD

# Stage only the files you changed (never git add .)
git add src/pages/SomePage.tsx src/styles.css

# Review what is staged
git diff --cached --stat

# Confirm no secrets or large files are included
git diff --cached | grep -E "API_KEY|SECRET|PASSWORD|token" -i
```

---

## This project (Vite + React + TypeScript + Vitest)

The recommended verification sequence for the اداره اسبوت لايت project:

```bash
# From the dashboard directory:
npx tsc --noEmit
npx eslint "src/**/*.{ts,tsx}" --max-warnings 0
npm run build

# From the worker directory (Cloudflare Worker):
cd ../worker
npx tsc --noEmit
npx vitest run
```

**Minimum required before any delivery in this project:**
1. `npx tsc --noEmit` → zero errors
2. `npm run build` → clean build, no new large chunks
3. Visual check at 390 px and 1440 px (RTL Arabic layout)
