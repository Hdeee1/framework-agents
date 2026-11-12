---
name: project-onboard
description: "Inspects an existing codebase to populate AGENTS.md, .agents/rules/03-lang-stack.md, and docs. Use when adopting this framework in a repository that already has code, before adding features or refactoring."
---

# Project Onboard (Existing Repository)

1. **Create branch** `chore/agent-onboard` from the current HEAD.
2. **Discover stack and tooling:** read dependency manifests, lockfiles, compiler/linter configs, task runners (`Makefile`, `justfile`, `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, or equivalent), and CI workflow files.
3. **Read existing guidance** such as `CONTRIBUTING.md`, `.cursor/rules/`, `.github/copilot-instructions.md`. Copy only project facts (commands, restricted paths) into `AGENTS.md`. Do not delete those files.
4. **Map layout:** entrypoints, core domain, tests, sensitive paths. Do not modify application source.
5. **Populate `AGENTS.md`:** replace every placeholder using the exact commands the repository and its CI already use. Keep all sections and headings. If `Project Type` is unknown, ask the user; if no answer, use `Commercial`.
6. **Populate `.agents/rules/03-lang-stack.md`** with conventions observed in the code (error handling, validation library, logging library, test naming).
7. **Create missing docs:** `docs/DECISIONS.md` (summarize the existing architecture, format from `01`) and `docs/ASSETS.md` (ledger header from `02`).
8. **Measure baseline:** run `Lint`, `Format Check`, `Typecheck`, `Test (All)`, and `Security Audit`. Do not fix failures. Write each failing command and file/test into `Known Baseline Failures`. Set `Coverage Threshold` to the lower of `80` and the current whole-project coverage.
9. **Verify:** run `grep -n "<PLACEHOLDER:" AGENTS.md .agents/rules/03-lang-stack.md` and confirm no output.
10. **Commit** `chore: add agent framework config` and report the baseline failures to the user.
