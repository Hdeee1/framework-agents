---
trigger: model_decision
description: "Standards for CI/CD pipelines, containerization, task runner synchronization, and release versioning."
---

# Delivery & CI/CD Standards

## Task Runner & Command Parity

- **Single Source of Truth:** Every command defined under `## Commands` in `AGENTS.md` must match the project's task runner (`Makefile`, `justfile`, `package.json` scripts, or language equivalent) and the CI pipeline step-for-step.
- **CI Pipeline Sequence:** Configure CI workflows to run in deterministic order using locked dependencies: `Install` → `Lint` → `Format Check` → `Typecheck` → `Test (All)` → `Build` → `Security Audit`.

## Containerization (When Applicable)

- **Hardened Multi-Stage Builds:** When a project uses containers (`Dockerfile` / `Containerfile`), use multi-stage builds with pinned base image versions/digests, a complete `.dockerignore` (excluding `.git`, `.env*`, local artifacts, and test fixtures), a non-root runtime user (`USER`), and a `HEALTHCHECK` instruction.
- **Local Services:** When local development requires backing services (databases, queues, caches), provide a `compose.yaml` / `docker-compose.yml` with pinned image versions and healthchecks so local setup remains reproducible.

## Versioning & Releases

- Follow Semantic Versioning (`MAJOR.MINOR.PATCH`) for libraries, CLIs, and versioned APIs, and document breaking changes or migration steps in `CHANGELOG.md` or release notes.
