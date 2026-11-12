# Project Agent Guide

- **Project Type:** `<PLACEHOLDER: Personal | Commercial>`
- **Response Language:** `<PLACEHOLDER: Match user prompt language (default) | English | Indonesian>`
- **Architecture & Decisions Log:** `docs/DECISIONS.md`
- **External Assets Ledger:** `docs/ASSETS.md`

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
- **Static & External Assets:** `assets/`

## Commands (Mandatory — never guess commands outside this list)

- **Install:** `<PLACEHOLDER: exact install command from lockfile>`
- **Dev:** `<PLACEHOLDER: exact local dev command>`
- **Build:** `<PLACEHOLDER: exact build command>`
- **Test (All):** `<PLACEHOLDER: exact full test suite command with coverage>`
- **Test (Single Target):** `<PLACEHOLDER: exact command pattern to test a single file/module>`
- **Lint:** `<PLACEHOLDER: exact lint check command>`
- **Format Check:** `<PLACEHOLDER: exact formatter check command>`
- **Typecheck:** `<PLACEHOLDER: exact typecheck command, or N/A if compiled>`
- **Security Audit:** `<PLACEHOLDER: exact dependency vulnerability check command>`

## Forbidden Paths (Never read, write, or list without explicit user approval)

- Any path outside this repository root workspace.
- `.env` and `.env.*` files (except `.env.example`), private keys (`*.pem`, `*.key`), and credentials files.
- `<PLACEHOLDER: Add project-specific restricted directories or N/A>`

## Agent Framework Routing Index

Always load and obey the core rules below, and read task-specific rules, skills, or workflows from `.agents/` before executing matching tasks:

- **Always-On Core Rules:**
  - `.agents/rules/00-core-and-boundaries.md` — Execution loop, autonomy boundaries, and baseline security.
  - `.agents/rules/01-engineering-standards.md` — Architecture, typing, error handling, and testing gates.
- **Contextual Rules (Load when task matches):**
  - `.agents/rules/02-assets-licensing.md` — Adding third-party assets, fonts, media, datasets, or libraries.
  - `.agents/rules/03-lang-stack.md` — Project-specific language, runtime, and testing conventions.
  - `.agents/rules/04-web-frontend.md` — Modifying UI components, stylesheets, templates, or frontend state.
  - `.agents/rules/05-backend-api-data.md` — Modifying APIs, database schemas, migrations, queries, or server ops.
  - `.agents/rules/06-delivery.md` — Modifying CI/CD pipelines, containers, task runners, or release configs.
- **Skills (Reusable Procedures):**
  - `.agents/skills/project-bootstrap/SKILL.md` — Initializing a brand-new empty repository from scratch.
  - `.agents/skills/project-onboard/SKILL.md` — Populating `AGENTS.md` and `.agents/rules/03-lang-stack.md` in an existing repository.
  - `.agents/skills/asset-sourcing/SKILL.md` — Finding, verifying licenses, downloading, and logging external assets.
  - `.agents/skills/self-review/SKILL.md` — Auditing `git diff` prior to completion or commit.
- **Workflows (End-to-End Task Pipelines):**
  - `.agents/workflows/new-feature.md` — Implementing a new feature end-to-end with tests and documentation.
  - `.agents/workflows/refactor.md` — Restructuring existing code while strictly preserving observable behavior.
  - `.agents/workflows/ship-check.md` — Running full release quality and security gates before shipping.
