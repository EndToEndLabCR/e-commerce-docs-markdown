# Story: Unit Tests for Domain & Application Layers

**Story Title**: Unit Tests for Domain & Application Layers
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to unit-test domain value objects and application use cases
**So that** business rules are verified without a database.
**Labels**: backend, quality, testing
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a value object, when its tests run, then valid construction, validation rules, and equality are verified.
- Given a use case, when its tests run, then happy path, edge, and failure cases are verified with mocked repositories.
- Given a use case that raises a domain exception, when it is tested, then the correct exception is asserted.
- Given the test suite, when it runs, then it passes with no skipped failures.

---

# Story: Repository & API Integration Tests

**Story Title**: Repository & API Integration Tests
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to integration-test repositories and API endpoints against SQLite
**So that** persistence and request-handling behavior are verified end to end.
**Labels**: backend, quality, testing
**Priority**: Must Have
**Story Points**: 8

---

**Acceptance Criteria:**

- Given the SQLite test database, when repository tests run, then CRUD and query behavior are verified.
- Given the FastAPI app, when endpoint tests run against a test client, then success and error status codes are verified.
- Given migration setup, when tests run, then the schema is applied before the suite executes.
- Given the suite, when it runs, then it is deterministic and leaves no persistent data behind.

---

# Story: Lint & Type-Check Baseline

**Story Title**: Lint & Type-Check Baseline
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to enforce ruff and mypy checks
**So that** code quality and typing stay consistent across the codebase.
**Labels**: backend, quality, testing
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given the codebase, when ruff runs, then the configured rules pass with no errors.
- Given the codebase, when mypy runs, then it passes with no errors under the configured settings.
- Given new code, when it is added, then it introduces no new lint or type violations.
- Given a pull request, when checks run, then lint and type-check are part of the validation.
