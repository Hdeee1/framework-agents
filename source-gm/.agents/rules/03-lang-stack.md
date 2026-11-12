---
trigger: glob
globs: "**/*.ts, **/*.tsx, **/*.js, **/*.mjs, **/*.py, **/*.go, **/*.rs, **/*.java, **/*.kt, **/*.cs, **/*.rb, **/*.php"
description: "Project-specific language, runtime, compiler, and testing conventions populated per repository."
---

# Language & Stack Conventions

> **Note:** Populate the `<PLACEHOLDER>` fields below using `.agents/skills/project-bootstrap/SKILL.md` (new repo) or `.agents/skills/project-onboard/SKILL.md` (existing repo). Until populated, follow the universal defaults in each section.

## Runtime & Compiler Configuration

- **Pinned Runtime Version:** `<PLACEHOLDER: e.g., .nvmrc / .python-version / go.mod toolchain / rust-toolchain.toml>`
- **Compiler / Interpreter Strictness Flags:** `<PLACEHOLDER: e.g., tsconfig strict flags / mypy --strict / go vet + golangci-lint / cargo clippy -D warnings>`
- **Module System & Formatting:** `<PLACEHOLDER: e.g., ESM only / PEP 8 via ruff / gofumpt>`
- **Universal Default:** Pin the runtime version in version-controlled config files and enable strict compiler/typechecker modes so implicit untyped values, unused variables, and unreachable code fail the build.

## Idioms & Error Propagation

- **Error Handling Pattern:** `<PLACEHOLDER: e.g., explicit error return wrapping with %w / typed Result<T, E> / domain Error subclasses with cause>`
- **Schema & Boundary Validation Library:** `<PLACEHOLDER: e.g., Zod / Pydantic / go-playground/validator / serde>`
- **Structured Logging Library:** `<PLACEHOLDER: e.g., pino / structlog / log/slog / tracing>`
- **Universal Default:** Never throw or return raw strings as errors. Derive static types from validation schemas where supported. Use structured JSON/key-value logging in production code instead of raw stdout debug prints.

## Concurrency & Resource Lifecycle

- **Concurrency & Cancellation Model:** `<PLACEHOLDER: e.g., async/await with AbortSignal / context.Context propagation / structured concurrency>`
- **Universal Default:** Every concurrent task or background goroutine/thread/promise must have a deterministic termination path, explicit timeout/cancellation propagation, and race-condition protection on shared state.

## Testing Conventions

- **Test File Naming & Location:** `<PLACEHOLDER: e.g., src/**/*.test.ts / tests/test_*.py / *_test.go>`
- **Test Patterns & Fixtures:** `<PLACEHOLDER: e.g., table-driven tests, fixture directory path>`
- **Universal Default:** Name tests after the expected behavior (`should_<expected_behavior>_when_<condition>`). Keep test fixtures in dedicated fixture directories and run concurrency/race detectors where supported by the toolchain.
