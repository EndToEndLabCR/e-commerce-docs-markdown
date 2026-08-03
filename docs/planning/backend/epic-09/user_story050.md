# US-MVP-BE-050: Lint & Type-Check Baseline

> **Epic**: [Epic 9: Backend Testing & Quality](./epic-09.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 9
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
