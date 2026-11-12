---
name: self-review
description: "Reviews git status and git diff against requirements, security, test coverage, and scope discipline. Use before creating a final commit or reporting task completion."
---

# Self Review

Inspect `git status` and `git diff` critically before concluding any coding task:

1. **Requirement & Behavioral Check:** Does the diff completely satisfy the user request (or preserve 100% behavioral equivalence during a refactor)? Are boundary conditions (`null`/empty, invalid input, timeouts, concurrency) handled?
2. **Test Verification:** Do automated tests cover the changed logic, and do they assert actual behavioral outputs rather than tautologies or over-mocked internals?
3. **Security Check:** Are all new inputs validated at the boundary? Are queries parameterized? Are secrets, `.env` files, and PII completely absent from the diff and logs?
4. **Architecture & Cleanliness:** Are there any leftover debug logs, dead code, uncontextualized `TODO`s, magic numbers, or unjustified linter/type suppressions?
5. **Scope Check:** Does `git diff` contain any unrelated file edits, formatting noise, or unrequested features? Revert or split out any out-of-scope changes.
6. **Documentation Sync:** Are `README.md`, `.env.example`, `docs/DECISIONS.md`, and `docs/ASSETS.md` updated if setup, env vars, architecture, or assets changed?

Fix all identified issues and re-run the verification commands in `AGENTS.md` before reporting completion.
