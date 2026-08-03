# US-MVP-BE-049: Repository & API Integration Tests

> **Epic**: [Epic 9: Backend Testing & Quality](./epic-09.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 9
**Priority**: Must Have
**Effort Estimate**: 8

**As a** Backend Engineer,
**I want to** integration-test repositories and API endpoints against SQLite,
**So that** persistence and request-handling behavior are verified end to end.

**Acceptance Criteria**:
- [ ] Given the SQLite test database, when repository tests run, then CRUD and query behavior are verified.
- [ ] Given the FastAPI app, when endpoint tests run against a test client, then success and error status codes are verified.
- [ ] Given migration setup, when tests run, then the schema is applied before the suite executes.
- [ ] Given the suite, when it runs, then it is deterministic and leaves no persistent data behind.
