---
trigger: always_on
description: "Universal standards for architecture, code quality, error handling, testing, dependencies, and documentation."
---

# Engineering Standards

## Architecture

- Keep business logic separate from transport (HTTP/CLI/UI) and external I/O (database, filesystem, third-party APIs).
- Do not create an abstraction until the same pattern appears at 3 or more call sites.
- Avoid mutable global state and side effects at module load. Pass dependencies explicitly.

## Code Quality

- Satisfy the strictest type-check and lint configuration already in the project.
- No unchecked escape hatches (e.g., `any`, untyped maps, `unsafe`) and no lint/type suppression directives without an inline comment stating why it is required and safe.
- Before finishing, remove unused imports, commented-out code, debug prints, and unnamed magic numbers/strings.
- Format deferred work as `TODO(<owner-or-issue>): <condition for removal>`.
- Document public APIs per the language's convention. Use inline comments only for non-obvious reasons, invariants, or workarounds.

## Errors & Resources

- Handle every error explicitly. No empty catch/ignore blocks. Add context (operation and identifier) before propagating.
- Close files, connections, transactions, and workers with the language's deterministic cleanup mechanism, and honor cancellation and timeouts.

## Testing Gates

- **New feature:** automated tests for the happy path and edge cases (empty/null input, invalid payload, boundary limits, upstream I/O failure).
- **Bug fix:** a regression test that fails before the fix and passes after.
- **Refactor:** never change behavior and structure in the same commit. If target code lacks tests, add characterization tests (tests that lock in current behavior) first.
- **Isolation:** tests are deterministic and order-independent. Mock only at external boundaries (network, filesystem, clock, randomness), never code you own.
- **Coverage:** follow `Coverage Threshold` in `AGENTS.md` (see Verification Gate in `00`).

## Dependencies

- Prefer the standard library. Use a third-party package only for security-critical domains (cryptography, auth), complex specification parsing, or substantial boilerplate removal.
- Commit lockfiles. Run `Security Audit` whenever dependencies change.

## Documentation

- Update `README.md` and `.env.example` in the same task when commands, environment variables, or setup prerequisites change.
- Record significant architecture or stack decisions in `docs/DECISIONS.md` using this entry format:

  `## <YYYY-MM-DD> <title>` followed by `Context:`, `Decision:`, `Consequences:` lines.
