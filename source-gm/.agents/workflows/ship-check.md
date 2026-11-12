---
name: ship-check
description: "Full pre-release quality, security, and documentation verification gate."
---

# Ship Check Workflow

1. **Clean Install & Static Checks:** Run `Install`, `Lint`, `Format Check`, and `Typecheck` from `AGENTS.md` and verify zero warnings or errors.
2. **Test Suite & Coverage Gate:** Run `Test (All)` from `AGENTS.md` and verify that all tests pass and core module coverage meets the `>= 80%` threshold defined in `.agents/rules/01-engineering-standards.md`.
3. **Production Build:** Run `Build` from `AGENTS.md` (including container image build if a `Dockerfile`/`Containerfile` exists in the repository).
4. **Dependency Security Audit:** Run `Security Audit` from `AGENTS.md` and resolve any high or critical vulnerabilities.
5. **Secret & Git Hygiene Scan:** Verify `git status` is clean, `.gitignore` excludes `.env*` and build artifacts, and no secrets, private keys, or credentials exist in tracked files.
6. **Documentation & Asset Ledger Audit:** Confirm every file under `assets/` has a matching valid row in `docs/ASSETS.md` and that `README.md` and `.env.example` match current commands and environment variables.
7. **Report Quality Gate Matrix:** Fix any failures found, then output a pass/fail summary table covering all 6 gates above with exact command exit results.
