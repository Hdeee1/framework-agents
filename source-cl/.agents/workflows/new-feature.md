---
name: new-feature
description: "End-to-end workflow for implementing a new feature with tests, docs, and verification."
---

# New Feature Workflow

1. **Readiness:** follow steps 2-3 of the execution loop in `.agents/rules/00-core-and-boundaries.md` (placeholder check, clean working tree). Read `AGENTS.md` and `docs/DECISIONS.md`.
2. **Acceptance criteria:** write the goal and at most 7 testable acceptance criteria. Ask the user only if an ambiguity would change a public API, stored data, or security behavior; otherwise state your assumptions in the plan.
3. **Inspect & plan:** read the affected modules. Write a plan (affected files, test per criterion). Create branch `feat/<short-kebab-name>` from the current HEAD.
4. **Assets (if needed):** run `.agents/skills/asset-sourcing/SKILL.md`.
5. **Implement with tests:** every acceptance criterion maps to at least one automated test. Follow `01` and `03`, plus `04`/`05`/`06` where the Task Router applies. Iterate with `Test (Single Target)` and `Typecheck`.
6. **Verification Gate:** run it as defined in `00`.
7. **Self-review & docs:** run `.agents/skills/self-review/SKILL.md`; update `README.md`, `.env.example`, `docs/DECISIONS.md` as needed.
8. **Commit & report:** commit `feat(<scope>): <summary>`. Do not push. Send the final report format from `00`.
