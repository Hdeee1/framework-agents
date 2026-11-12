---
name: ship-check
description: "Full pre-release quality, security, and documentation check."
---

# Ship Check Workflow

1. **Clean install & static checks:** run `Install`, `Lint`, `Format Check`, `Typecheck`. Zero errors beyond `Known Baseline Failures`.
2. **Tests & coverage:** run `Test (All)`. All pass, and whole-project coverage is at least `Coverage Threshold` (skip if `N/A`).
3. **Production build:** run `Build`; also build the container image if a `Dockerfile`/`Containerfile` exists.
4. **Dependency audit:** run `Security Audit`. Resolve all high and critical findings.
5. **Secrets & Git hygiene:** `git status` is clean, `.gitignore` excludes `.env*` and build artifacts, and no secrets or private keys exist in tracked files.
6. **Docs & ledger:** every file under the assets directory has a valid row in `docs/ASSETS.md`; `README.md` and `.env.example` match current commands and environment variables.
7. **Report:** fix failures, re-run the failed gate, then output a pass/fail table for the 6 gates above with the exact command and exit code for each.
