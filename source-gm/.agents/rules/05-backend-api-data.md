---
trigger: model_decision
description: "Standards for REST/RPC API design, database schemas, migrations, queries, caching, and backend service operations."
---

# Backend, API & Data Standards

## API Design & Contracts

- **Contract-Driven Boundaries:** Define request/response schemas explicitly (OpenAPI, JSON Schema, Protobuf, or typed validation schemas) and validate all incoming payloads and query parameters at the handler boundary.
- **Consistent Semantics:** Use accurate HTTP status codes (or RPC status codes), cursor-based or bounded offset pagination (`limit` capped with a safe maximum), and a uniform machine-readable error payload format (such as RFC 9457 Problem Details: `type`, `title`, `status`, `detail`).
- **Idempotency & Resilience:** Require idempotency keys or natural unique constraints for retriable state-mutating operations. Configure explicit timeouts on all outbound network calls; apply exponential backoff with jitter only to idempotent operations.

## Database & Persistence

- **Forward-Only Versioned Migrations:** Manage all schema changes through versioned migration files. Never edit or delete a migration that has already been committed and shared; write a new corrective migration instead.
- **Data Integrity at the Schema Layer:** Enforce `NOT NULL`, `UNIQUE`, `FOREIGN KEY`, and `CHECK` constraints directly in the database schema rather than relying solely on application code.
- **Query Safety & Efficiency:** Use parameterized queries exclusively. Wrap multi-step state mutations in atomic transactions, index columns used in `WHERE`/`JOIN`/`ORDER BY` clauses, and eliminate N+1 query loops via batching or joins.
- **Seed Separation:** Keep development/test seed scripts separate from schema migrations.

## Service Operations

- **Stateless & Configurable:** Read environment configuration at startup and fail fast if required variables are missing or invalid. Write structured logs to `stdout`/`stderr` without sensitive payload fields.
- **Health & Shutdown:** Expose liveness (`/healthz`) and readiness (`/readyz`) checks for long-running servers, enforce request body size limits and rate limiting on public endpoints, and implement graceful shutdown that drains in-flight requests and closes DB/cache pools cleanly on `SIGINT`/`SIGTERM`.
