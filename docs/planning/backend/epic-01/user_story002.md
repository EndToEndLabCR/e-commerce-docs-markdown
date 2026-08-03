# US-MVP-BE-002: Async Database Connection & Engine Factory

> **Epic**: [Epic 1: Backend Foundation & Infrastructure](./epic-01.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 1
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create an async database engine through a factory that supports Postgres and SQLite,
**So that** the API uses the right database per environment and can run tests against SQLite.

**Acceptance Criteria**:
- [ ] Given a persistence driver of `postgres`, when the engine is created, then an async `asyncpg` engine is produced.
- [ ] Given a persistence driver of `sqlite`, when the engine is created, then an async `aiosqlite` engine is produced.
- [ ] Given a database session request, when a request handler runs, then an async session is provided and closed after use.
