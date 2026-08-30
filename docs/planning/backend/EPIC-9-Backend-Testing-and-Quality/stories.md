# Stories for Epic: Backend Testing & Quality

## Backend Engineer

### US-EP9-BE-001: Unit Tests for Domain and Application Layers

**Story ID**: US-EP9-BE-001
**Epic Link**: EPIC-9
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** unit-test domain value objects and application use cases,
**So that** business rules are verified without a database.

**Acceptance Criteria**:

- [ ] Given a value object, when its tests run, then valid construction, validation rules, and equality are verified.
- [ ] Given a use case, when its tests run, then happy path, edge, and failure cases are verified with mocked repositories.
- [ ] Given a use case that raises a domain exception, when it is tested, then the correct exception is asserted.
- [ ] Given the test suite, when it runs, then it passes with no skipped failures.

**Deliverables**:

- Unit test suite for domain value objects
- Unit test suite for application use cases with mocked repositories

**Success Metrics**:

- Domain and use case logic is covered without requiring a live database.

---

### US-EP9-BE-002: Repository and API Integration Tests

**Story ID**: US-EP9-BE-002
**Epic Link**: EPIC-9
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

**Deliverables**:

- Repository integration test suite against SQLite
- API integration test suite using a FastAPI test client

**Success Metrics**:

- Integration test runs are deterministic and produce no leftover test data.

---

### US-EP9-BE-003: Lint and Type-Check Baseline

**Story ID**: US-EP9-BE-003
**Epic Link**: EPIC-9
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** enforce ruff and mypy checks,
**So that** code quality and typing stay consistent across the codebase.

**Acceptance Criteria**:

- [ ] Given the codebase, when ruff runs, then the configured rules pass with no errors.
- [ ] Given the codebase, when mypy runs, then it passes with no errors under the configured settings.
- [ ] Given new code, when it is added, then it introduces no new lint or type violations.
- [ ] Given a pull request, when checks run, then lint and type-check are part of the validation.

**Deliverables**:

- Ruff and mypy configuration for the project
- Lint and type-check steps wired into pull request validation

**Success Metrics**:

- Pull requests cannot merge with new lint or type-check violations.
