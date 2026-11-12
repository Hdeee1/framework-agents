---
trigger: always_on
description: "Per-project language idioms, error handling, validation, logging, concurrency, and test conventions."
---

# Language & Stack Conventions

Fill the fields below via `project-bootstrap` or `project-onboard`. Language, runtime version, test runner, and linter/formatter live in `AGENTS.md` only. Until a field is filled, follow its Universal Default.

## Toolchain Strictness

- **Runtime pin file:** `<PLACEHOLDER: e.g., .nvmrc / .python-version / go.mod toolchain / rust-toolchain.toml>`
- **Strictness flags:** `<PLACEHOLDER: e.g., tsconfig strict / mypy --strict / clippy -D warnings>`
- **Universal Default:** pin the runtime version in a committed file and enable the strictest compiler/type-checker mode available, so unused variables, implicit untyped values, and unreachable code fail the build.

## Idioms

- **Error handling pattern:** `<PLACEHOLDER: e.g., wrapped error returns / Result<T, E> / typed exception classes with cause>`
- **Boundary validation library:** `<PLACEHOLDER: e.g., Zod / Pydantic / go-playground/validator / serde>`
- **Logging library:** `<PLACEHOLDER: e.g., pino / structlog / log/slog / tracing>`
- **Universal Default:** never throw or return raw strings as errors. Derive static types from validation schemas where supported. Use structured key-value logging in non-test code, not raw prints.

## Concurrency

- **Concurrency & cancellation model:** `<PLACEHOLDER: e.g., async/await with AbortSignal / context.Context / structured concurrency / N/A>`
- **Universal Default:** every concurrent task has a termination path, timeout or cancellation propagation, and protection for shared state.

## Testing

- **Test file naming & location:** `<PLACEHOLDER: e.g., src/**/*.test.ts / tests/test_*.py / *_test.go>`
- **Fixture location & patterns:** `<PLACEHOLDER: e.g., tests/fixtures/, table-driven tests>`
- **Universal Default:** name tests `should_<expected_behavior>_when_<condition>` (adapted to the language's naming case), keep fixtures in a dedicated directory, and run race/concurrency detectors if the toolchain provides them.
