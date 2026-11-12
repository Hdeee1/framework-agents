---
name: self-review
description: "Reviews git status and git diff against requirements, security, tests, and scope. Use before the final commit or before reporting completion."
---

# Self Review

Run `git status` and `git diff`, then check each item:

1. **Requirements:** does the diff satisfy every requirement or acceptance criterion? For a refactor, is behavior of every listed public interface unchanged?
2. **Tests:** do tests cover the changed logic and assert real outputs, not tautologies or mocked internals? In a refactor, do test diffs contain only imports/paths/wiring of moved symbols?
3. **Security:** are new inputs validated at the boundary, queries parameterized, and secrets, `.env` files, and PII absent from the diff and logs?
4. **Cleanliness:** no debug output, dead code, commented-out code, unowned `TODO`, magic values, or unjustified suppressions.
5. **Scope:** no unrelated file edits, formatting noise, or unrequested features. Revert or split them out.
6. **Docs:** `README.md`, `.env.example`, `docs/DECISIONS.md`, `docs/ASSETS.md` updated if setup, env vars, architecture, or assets changed.
7. **Baseline:** `Known Baseline Failures` in `AGENTS.md` is unchanged unless the task intentionally fixed one.

Fix every finding, then re-run the Verification Gate before reporting.
