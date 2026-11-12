# Project Agent Guide

Read this file at the start of every task. Details live in `.agents/`; follow the Task Router below.

## Project

- **Project Type:** `<PLACEHOLDER: Personal | Commercial>`
- **Response Language:** `<PLACEHOLDER: a language name, or "match user">`
- **Decisions Log:** `docs/DECISIONS.md`
- **Assets Ledger:** `docs/ASSETS.md`

## Stack

- **Language & Runtime Version:** `<PLACEHOLDER: e.g., Python 3.12 / Go 1.23 / Node.js 22 LTS>`
- **Framework:** `<PLACEHOLDER: e.g., FastAPI / Next.js / Gin / None>`
- **Package Manager:** `<PLACEHOLDER: e.g., uv / pnpm / go mod / cargo>`
- **Test Runner:** `<PLACEHOLDER: e.g., pytest / vitest / go test>`
- **Linter & Formatter:** `<PLACEHOLDER: e.g., ruff / eslint + prettier / golangci-lint>`

## Layout

- **Entrypoints / App:** `<PLACEHOLDER: e.g., src/ or cmd/>`
- **Core Domain / Internal Logic:** `<PLACEHOLDER: e.g., src/core/ or internal/>`
- **Tests:** `<PLACEHOLDER: e.g., tests/ or co-located *_test.*>`
- **Assets Directory:** `<PLACEHOLDER: e.g., assets/ or public/>`

## Commands

Use only these commands for verification. Never guess others. `N/A` means skip that command.

- **Install:** `<PLACEHOLDER: exact install command from lockfile>`
- **Dev:** `<PLACEHOLDER: exact local dev command>`
- **Build:** `<PLACEHOLDER: exact build command>`
- **Test (All):** `<PLACEHOLDER: exact full test suite command, with coverage output if supported>`
- **Test (Single Target):** `<PLACEHOLDER: exact command pattern to test one file/module>`
- **Lint:** `<PLACEHOLDER: exact lint check command>`
- **Format Check:** `<PLACEHOLDER: exact formatter check command, no writes>`
- **Typecheck:** `<PLACEHOLDER: exact typecheck command, or N/A>`
- **Security Audit:** `<PLACEHOLDER: exact dependency vulnerability check command>`
- **Coverage Threshold:** `<PLACEHOLDER: percent number (default 80), or N/A>`

## Known Baseline Failures

Failures that existed before any agent change. The Verification Gate tolerates exactly these and nothing new.

- `<PLACEHOLDER: None | list of "command — failing file/test">`

## Forbidden Paths (never read, write, or list without explicit user approval)

- Any path outside this repository root.
- `.env` and `.env.*` (except `.env.example`), private keys (`*.pem`, `*.key`), credential files.
- `<PLACEHOLDER: project-specific restricted paths, or N/A>`

## Task Router

Always load: `.agents/rules/00-core-and-boundaries.md`, `.agents/rules/01-engineering-standards.md`, `.agents/rules/03-lang-stack.md`.

- Config fields unfilled, repo empty → `.agents/skills/project-bootstrap/SKILL.md`
- Config fields unfilled, repo has code → `.agents/skills/project-onboard/SKILL.md`
- New feature → `.agents/workflows/new-feature.md`
- Refactor → `.agents/workflows/refactor.md`
- Bug fix or any other change → no workflow; follow `00` execution loop and `01` testing gates
- Release / pre-ship check → `.agents/workflows/ship-check.md`
- Adding a third-party asset, font, media, dataset, or library → `.agents/rules/02-assets-licensing.md`; for non-library assets also `.agents/skills/asset-sourcing/SKILL.md`
- Touching web UI (HTML, CSS, components, templates) → `.agents/rules/04-web-frontend.md`
- Touching API, database, migrations, or long-running server code → `.agents/rules/05-backend-api-data.md`
- Touching CI, containers, task runner, or release config → `.agents/rules/06-delivery.md`
- Before reporting completion of any coding task → `.agents/skills/self-review/SKILL.md`
