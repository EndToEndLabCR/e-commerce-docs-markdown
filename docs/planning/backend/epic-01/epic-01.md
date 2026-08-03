# Epic 1: Backend Foundation & Infrastructure

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** The API has no consistent, environment-aware foundation for configuration, database connectivity, observability, dependency wiring, schema migrations, or deployment, which makes it unreliable to run across local, test, stage, and production environments.

**Objective:** Provide a stable backend foundation that boots the FastAPI app from environment-driven configuration, connects to the correct database engine, emits structured logs with correlation IDs, wires dependencies through a composition root, versions the schema with Alembic, and ships in a container.

Included scope:
- Environment-driven configuration (per-environment YAML plus `.env` overrides)
- Async database connection and engine factory (PostgreSQL and SQLite)
- Structured JSON logging with request/user correlation IDs
- Dependency injection and composition root (repositories and use cases)
- Alembic schema versioning covering every model
- Containerized deployment (Docker, docker-compose, Gunicorn/Uvicorn)

Excluded scope:
- Authentication and authorization logic
- Business feature behavior (catalog, orders, carts, payments)
- Observability beyond logging (APM, distributed tracing)

Dependencies:
- [MVP Roadmap — Non-Functional Requirements](../../phased-roadmap.md)
- [Non-Functional Requirements](../../../requirements/non-functional-requirements.md)
- [MVP Database Design](../../../database/v1_mvp_database_design.md)

Acceptance criteria:
- Given a configured environment, when the API starts, then configuration is loaded from the correct environment source without hardcoded values.
- Given an incoming request, when it is handled, then structured logs include a request ID and timestamp.
- Given a persistence driver setting, when the engine is created, then the matching database (Postgres or SQLite) is used.
- Given any new model, when a migration is generated, then Alembic metadata includes the model and the chain upgrades cleanly.

## User Stories

- [US-MVP-BE-001: App Bootstrap & Environment Configuration](./user_story001.md)
- [US-MVP-BE-002: Async Database Connection & Engine Factory](./user_story002.md)
- [US-MVP-BE-003: Structured JSON Logging with Correlation IDs](./user_story003.md)
- [US-MVP-BE-004: Dependency Injection & Composition Wiring](./user_story004.md)
- [US-MVP-BE-005: Database Schema Versioning with Alembic](./user_story005.md)
- [US-MVP-BE-006: Containerized Deployment](./user_story006.md)
