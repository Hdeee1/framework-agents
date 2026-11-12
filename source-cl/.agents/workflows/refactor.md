---
name: refactor
description: "Workflow for changing internal structure of existing code without changing observable behavior."
---

# Refactor Workflow

1. **Readiness:** follow steps 2-3 of the execution loop in `.agents/rules/00-core-and-boundaries.md`. Read `AGENTS.md` and `docs/DECISIONS.md`.
2. **Define goal and invariants:** state the structural goal (e.g., extract module, remove duplication, separate I/O from domain logic). List the public interfaces that must stay identical (exported functions, endpoints, CLI flags, database schema, file formats). Create branch `refactor/<short-kebab-name>` from the current HEAD.
3. **Baseline:** run `Lint`, `Typecheck`, `Test (All)` on unmodified code. Results must match `Known Baseline Failures`. If the target lacks tests for its current inputs, outputs, and error cases, write characterization tests first, pass them on unmodified code, and commit them alone as `test(<scope>): add characterization tests`.
4. **Atomic steps:** change one structural concern per step. After each step run `Test (Single Target)` and `Typecheck`; commit when green (`refactor(<scope>): <step>`). Do not edit test assertions. Edit only imports, paths, or wiring of moved symbols, and list those edits in the report. If a step is still red after 2 attempts, revert that step and report.
5. **Exclusions:** no feature additions, bug fixes, dependency changes, schema changes, or version upgrades on this branch. Note any bug found in the report; do not fix it.
6. **Verification Gate:** run it as defined in `00`.
7. **Self-review:** run `.agents/skills/self-review/SKILL.md`; confirm every listed public interface is unchanged.
8. **Report:** do not push. Send the final report format from `00`.
