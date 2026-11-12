---
trigger: model_decision
description: "Standards for API contracts, database schemas, migrations, queries, and long-running service operations."
---

# Backend, API & Data Standards

Applies only if the project has an HTTP/RPC API, a database, or a long-running service. Otherwise ignore this file.

## API

- Define request/response schemas explicitly (OpenAPI, JSON Schema, Protobuf, or typed validators). Validate all payloads and query parameters at the handler boundary.
- Use correct status codes, bounded pagination (`limit` has a fixed maximum), and one machine-readable error format (e.g., RFC 9457: `type`, `title`, `status`, `detail`).
- Retriable state-changing operations need an idempotency key or a natural unique constraint. Set explicit timeouts on all outbound calls. Retry with exponential backoff and jitter only idempotent operations.

## Database

- Change schemas only through versioned migration files. Never edit or delete a migration that was committed and shared; add a corrective one.
- Enforce `NOT NULL`, `UNIQUE`, `FOREIGN KEY`, and `CHECK` constraints in the schema, not only in application code.
- Use parameterized queries only. Wrap multi-step writes in a transaction. Index columns used in `WHERE`/`JOIN`/`ORDER BY`. Remove N+1 query loops with batching or joins.
- Keep seed scripts separate from migrations.

## Service Operations

- Read configuration at startup and fail fast if a required variable is missing or invalid. Log structured output to `stdout`/`stderr` without sensitive fields.
- For long-running servers: expose liveness and readiness endpoints (e.g., `/healthz`, `/readyz`), set request body size limits and rate limits on public endpoints, and shut down gracefully on `SIGINT`/`SIGTERM` (drain in-flight requests, close pools).
