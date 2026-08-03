# US-MVP-BE-048: Unit Tests for Domain & Application Layers

> **Epic**: [Epic 9: Backend Testing & Quality](./epic-09.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 9
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
