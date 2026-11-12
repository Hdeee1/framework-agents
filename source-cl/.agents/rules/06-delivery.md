---
trigger: model_decision
description: "Standards for CI/CD, containers, task runner parity, and release versioning."
---

# Delivery & CI/CD Standards

## Command Parity

- Every command under `## Commands` in `AGENTS.md` must equal the corresponding task-runner entry (`Makefile`, `justfile`, `package.json` scripts, or equivalent) and the CI step.
- CI runs with locked dependencies in this order: `Install` → `Lint` → `Format Check` → `Typecheck` → `Test (All)` → `Build` → `Security Audit`.

## Containers (only if the project uses them)

- Use multi-stage builds, pinned base image versions or digests, a `.dockerignore` excluding `.git`, `.env*`, local artifacts and test fixtures, a non-root `USER`, and a `HEALTHCHECK`.
- If local development needs backing services, provide a `compose.yaml` with pinned image versions and healthchecks.

## Versioning

- Use Semantic Versioning (`MAJOR.MINOR.PATCH`) for libraries, CLIs, and versioned APIs. Document breaking changes and migration steps in `CHANGELOG.md` or release notes.
