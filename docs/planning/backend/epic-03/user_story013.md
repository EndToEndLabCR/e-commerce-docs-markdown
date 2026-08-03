# US-MVP-BE-013: Logout & Token Revocation

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** support logout with token revocation,
**So that** a signed-out token can no longer access protected resources.

**Acceptance Criteria**:
- [ ] Given an authenticated user, when logout is called, then the token is revoked or otherwise invalidated.
- [ ] Given a revoked token, when a protected endpoint is called, then a 401 response is returned.
- [ ] Given a repeated logout, when it is called again, then the response is safe and does not error.
