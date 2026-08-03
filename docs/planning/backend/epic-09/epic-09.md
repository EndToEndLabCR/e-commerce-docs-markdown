# Epic 9: Backend Testing & Quality

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** The API has zero automated tests and no enforced lint or type-check baseline, so regressions go undetected and code quality is unverified.

**Objective:** Establish a quality baseline: unit tests for domain value objects and use cases, repository and API integration tests, and enforced ruff and mypy checks so the backend is verifiable and maintainable.

Included scope:
- Unit tests for the domain and application layers
- Repository and API integration tests (SQLite)
- Lint and type-check baseline (ruff and mypy)

Excluded scope:
- End-to-end browser tests (frontend)
- Load and performance testing (DevOps)
- Hard coverage-enforcement gates (post-baseline)

Dependencies:
- [Epic 1: Backend Foundation & Infrastructure](#epic-1-backend-foundation--infrastructure)
- [Epic 2: User & Account Management](#epic-2-user--account-management)
- [Epic 4: Product Catalog & Discovery](#epic-4-product-catalog--discovery)
- [Non-Functional Requirements](../../../requirements/non-functional-requirements.md)

Acceptance criteria:
- Given a value object or use case, when tests run, then behavior is verified including edge and failure cases.
- Given the repositories and API, when integration tests run against SQLite, then CRUD and error paths are verified.
- Given the codebase, when ruff and mypy run, then the configured rules pass with no new violations.

## User Stories

- [US-MVP-BE-048: Unit Tests for Domain & Application Layers](./user_story048.md)
- [US-MVP-BE-049: Repository & API Integration Tests](./user_story049.md)
- [US-MVP-BE-050: Lint & Type-Check Baseline](./user_story050.md)
