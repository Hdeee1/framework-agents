---
trigger: always_on
description: "Universal software engineering standards for architecture, code quality, error handling, testing, and documentation."
---

# Engineering Standards

## Architecture & Modularity

- **Separation of Concerns:** Keep domain/business logic decoupled from transport layers (HTTP/CLI/UI) and external I/O (databases, filesystems, third-party APIs).
- **No Premature Abstraction:** Prefer explicit, straightforward code until a pattern is duplicated across at least 3 distinct call sites.
- **State Management:** Avoid mutable global state and side-effect-heavy module initialization; pass dependencies explicitly via constructors or function parameters.

## Code Quality & Typing

- **Strict Static Analysis:** Enable and satisfy the strictest type-checking and linter rules configured in the project.
- **No Unjustified Suppressions:** Never use unchecked dynamic escape hatches (such as `any` or untyped dicts) or linter suppression directives (`nolint`, `eslint-disable`, `type: ignore`) without an inline comment explaining why it is required and safe.
- **No Dead Artifacts:** Remove unused imports, commented-out code, debug print statements, and magic numbers/strings before finishing a task.
- **Actionable TODOs:** Format deferred work as `TODO(<owner-or-issue>): <specific condition for removal>`.
- **Meaningful Comments:** Document public APIs/exports per language convention; use inline comments only to explain non-obvious _why_ decisions, invariants, or workarounds.

## Error & Resource Handling

- **Explicit Error Handling:** Handle all errors explicitly. Never use empty catch/ignore blocks. Wrap or enrich errors with operational context (what operation failed and on which identifier) before propagating.
- **Deterministic Cleanup:** Always close files, network connections, database transactions, and background workers using the language's deterministic cleanup mechanism (`defer`, `try/finally`, `with`, `using`, or `Drop`) and respect cancellation/timeout signals.

## Verification & Testing Gates

- **New Features:** Every new feature must include automated unit and/or integration tests covering happy paths and boundary edge cases (`null`/empty inputs, invalid payloads, boundary limits, and upstream I/O failures).
- **Bug Fixes:** Every bug fix must include a deterministic regression test that fails before the fix and passes after the fix.
- **Refactoring:** Never modify observable behavior and internal structure in the same commit. Verify that existing tests pass before starting a refactor; if target code lacks tests, write characterization tests locking in current behavior first.
- **Test Isolation:** Tests must be deterministic and order-independent. Do not mock internal domain logic you own; use fakes, stubs, or mocks strictly at external I/O boundaries (network, filesystem, clock, randomness).
- **Coverage Gate:** Maintain line/branch coverage at or above `80%` on modified packages/modules (or avoid decreasing existing coverage on legacy modules).

## Dependency Hygiene

- **Standard Library First:** Prefer built-in language standard libraries over third-party packages unless the problem involves security-critical domains (cryptography, auth), complex protocol/specification parsing, or significant boilerplate reduction.
- **Reproducible Builds:** Commit lockfiles to version control and run `Security Audit` from `AGENTS.md` whenever dependencies change.

## Documentation Maintenance

- **Setup & Usage:** Update `README.md` and `.env.example` in the same task whenever commands, environment variables, or setup prerequisites change.
- **Architectural Decisions:** Log significant architectural choices, stack selections, or trade-offs in `docs/DECISIONS.md` (Context, Decision, Consequences).
