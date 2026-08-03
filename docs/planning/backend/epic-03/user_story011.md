# US-MVP-BE-011: Token Validation & Current-User Dependency

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** validate JWTs and resolve the current user in a reusable dependency,
**So that** protected endpoints can rely on a consistent auth check.

**Acceptance Criteria**:
- [ ] Given a valid token, when a protected endpoint is called, then the current user is resolved from the token claims.
- [ ] Given an expired or malformed token, when a protected endpoint is called, then a 401 response is returned.
- [ ] Given a missing `Authorization` header, when a protected endpoint is called, then a 401 response is returned.
- [ ] Given a token for a deleted user, when it is validated, then the request is rejected.
