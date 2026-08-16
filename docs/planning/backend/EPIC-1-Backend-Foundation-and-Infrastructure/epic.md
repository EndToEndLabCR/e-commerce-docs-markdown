# Epic: Backend Foundation & Infrastructure

**Epic Title**: Backend Foundation & Infrastructure
**Epic Key**: EPIC-1
**Summary**: Establish the foundational backend architecture needed for reliable local development, environment-aware configuration, observability, schema lifecycle, and containerized deployment.
**Labels**: backend, foundational, infrastructure
**Priority**: Must Have
**Components**: Backend, Infrastructure, Database
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: The backend does not yet have a consistent foundation for configuration, database connectivity, observability, dependency wiring, schema versioning, or deployment. As a result, the API is difficult to run reliably across local, test, staging, and production environments.

Objective: Create a stable backend foundation that loads environment-specific settings, connects to the appropriate database engine, emits structured logs with correlation IDs, resolves dependencies through a composition root, versions schema changes with Alembic, and runs in a containerized deployment model.

Included scope:
- Environment-driven configuration with per-environment settings and `.env` overrides
- Async database connection and engine factory supporting PostgreSQL and SQLite
- Structured JSON logging with request and user correlation IDs
- Dependency injection and composition root for repositories and use cases
- Alembic-based schema versioning for all models
- Containerized deployment with Docker and Gunicorn/Uvicorn

Excluded scope:
- Authentication and authorization logic
- Feature-specific business workflows for catalog, orders, carts, or payments
- Full observability tooling beyond logging and correlation tracking

Dependencies:
- [MVP Roadmap](../../phased-roadmap.md)
- [Non-Functional Requirements](../../../requirements/non-functional-requirements.md)
- [MVP Database Design](../../../database/v1_mvp_database_design.md)

Measurable success criteria:
- Given a configured environment, when the API starts, then configuration is loaded from the correct source without hardcoded values.
- Given an incoming request, when it is handled, then logs include a request ID and timestamp in a structured JSON format.
- Given a persistence driver setting, when the engine is created, then the correct database backend is used for Postgres or SQLite.
- Given any new model, when a migration is generated, then Alembic metadata includes the model and upgrades complete cleanly.
