---
name: project-onboard
description: "Inspects an existing codebase to populate placeholders in AGENTS.md, .agents/rules/03-lang-stack.md, and docs/DECISIONS.md. Use when adopting this framework in an existing repository before adding features or refactoring."
---

# Project Onboard (Existing Repository)

1. **Discover Stack & Tooling:** Inspect dependency manifests, lockfiles, compiler/linter configs, task runners (`Makefile`, `justfile`, `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`), and CI workflow files at the repository root.
2. **Map Directory Layout:** Identify entrypoints, core domain modules, test directories, and sensitive paths without modifying any application source code.
3. **Populate `AGENTS.md`:** Replace all `<PLACEHOLDER>` fields in `AGENTS.md` (`Stack`, `Layout`, `Commands`, and `Forbidden Paths`) using the exact commands already used by the repository and its CI pipeline. If `Project Type` (`Personal` vs. `Commercial`) is unknown, ask the user or default to `Commercial`.
4. **Populate `.agents/rules/03-lang-stack.md`:** Fill in the `<PLACEHOLDER>` fields with the existing conventions observed in the codebase (error handling style, validation library, logging library, test naming pattern).
5. **Initialize Missing Docs:** If `docs/DECISIONS.md` or `docs/ASSETS.md` do not exist, create them and summarize the existing architecture in `docs/DECISIONS.md`.
6. **Verify Baseline Commands:** Run the populated `Lint`, `Format Check`, `Typecheck`, and `Test (All)` commands from `AGENTS.md` to establish a known baseline before making any code changes. Report any pre-existing failures to the user.
