---
name: refactor
description: "Step-by-step workflow for refactoring existing code (improving internal structure without changing observable behavior)."
---

# Refactor Workflow

1. **Check Context & Readiness:** Read `AGENTS.md` and `docs/DECISIONS.md`. If `AGENTS.md` contains unpopulated `<PLACEHOLDER>` fields, run `.agents/skills/project-onboard/SKILL.md` first.
2. **Establish Baseline & Characterization Tests:** Run `Test (All)` and `Typecheck` from `AGENTS.md` on the unmodified code. If the target module lacks test coverage for its current public inputs, outputs, and error cases, write and pass characterization tests **before** modifying production code.
3. **Scope & Branch:** Define the exact structural goal (e.g., extract module, remove duplication, decouple I/O from domain logic) and create a branch `refactor/<short-kebab-name>`. Never mix feature additions or behavioral bug fixes into a refactor branch.
4. **Apply Atomic Structural Steps:** Perform the refactoring in small, incremental steps. After each step, run `Test (Single Target)` and `Typecheck` from `AGENTS.md` without modifying existing test assertions (update test imports/wiring only if signatures intentionally moved).
5. **Run Full Verification Gate:** Execute `Lint`, `Format Check`, `Typecheck`, `Test (All)`, and `Build` from `AGENTS.md` and verify zero regressions.
6. **Self-Review:** Run `.agents/skills/self-review/SKILL.md` on `git diff` to confirm no unintended behavioral changes, public API breaks, or scope creep occurred.
7. **Commit & Report:** Commit changes using `refactor(<scope>): <summary>` and report the structural improvements and test verification results.
