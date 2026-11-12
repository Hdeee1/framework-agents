---
name: new-feature
description: "End-to-end workflow for implementing a new feature with tests, documentation, and verification gates."
---

# New Feature Workflow

1. **Check Context & Readiness:** Read `AGENTS.md` and `docs/DECISIONS.md`. If `AGENTS.md` contains unpopulated `<PLACEHOLDER>` fields, run `.agents/skills/project-onboard/SKILL.md` first.
2. **Inspect & Plan:** Read the existing modules affected by the feature. Write a concise implementation plan (goal, affected files, test strategy) and create a branch `feat/<short-kebab-name>`.
3. **Source External Assets (If Needed):** If the feature requires external media, icons, fonts, or datasets, execute `.agents/skills/asset-sourcing/SKILL.md`.
4. **Implement & Test Iteratively:** Write the feature implementation alongside unit and integration tests following `.agents/rules/01-engineering-standards.md` and `.agents/rules/03-lang-stack.md`. Run `Test (Single Target)` and `Typecheck` from `AGENTS.md` on the modified module during iteration.
5. **Run Full Verification Gate:** Execute `Lint`, `Format Check`, `Typecheck`, `Test (All)`, and `Build` from `AGENTS.md` until all pass with exit code `0`.
6. **Self-Review & Docs:** Run `.agents/skills/self-review/SKILL.md` on `git diff` and update `README.md`, `.env.example`, or `docs/DECISIONS.md` if configuration or architecture changed.
7. **Commit & Report:** Commit changes using `feat(<scope>): <summary>` and report the summary of changes and verification results.
