---
name: project-bootstrap
description: "Initializes a brand-new empty repository with directory layout, tooling, test runner, documentation, and populated AGENTS.md. Use only when starting a new project from scratch in an empty workspace."
---

# Project Bootstrap

1. **Confirm Stack:** Check the user's request for the required language, framework, and project type (`Personal` or `Commercial`). If any of these are missing, ask the user before generating files; do not guess an entire tech stack unilaterally.
2. **Initialize Version Control & Editor Config:** Initialize Git (if not already initialized), create a stack-appropriate `.gitignore`, `.editorconfig`, and runtime version pin file (e.g., `.nvmrc`, `.python-version`, `go.mod`, `rust-toolchain.toml`).
3. **Scaffold Directories:** Create the idiomatic source and test directories for the chosen language plus `docs/` and `assets/`.
4. **Configure Toolchain:** Initialize the package manager with a committed lockfile, strict linter, formatter, typechecker (if applicable), and test runner.
5. **Create Documentation Baselines:** Create `README.md` (setup and run instructions), `.env.example`, `docs/DECISIONS.md` (recording the initial stack decision), and `docs/ASSETS.md` (with the standard ledger table header from `.agents/rules/02-assets-licensing.md`).
6. **Optional Delivery Configs:** Create CI workflow and container files only if requested by the user or standard for the deliverable type, following `.agents/rules/06-delivery.md`.
7. **Populate Agent Configs:** Replace all `<PLACEHOLDER>` fields in `AGENTS.md` and `.agents/rules/03-lang-stack.md` with the exact project values and commands.
8. **Smoke Test & Verify:** Write one deterministic smoke test and execute every command listed in `AGENTS.md` (`Lint`, `Format Check`, `Typecheck`, `Test (All)`, `Build`) until all exit with code `0`.
9. **Initial Commit:** Stage all files and create the initial commit: `chore: bootstrap project`.
