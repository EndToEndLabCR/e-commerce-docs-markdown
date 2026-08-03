# US-MVP-BE-016: Role-Based Access Control Guards

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** enforce role-based access control on endpoints,
**So that** admin-only operations are protected from customers and vice versa.

**Acceptance Criteria**:
- [ ] Given an admin token, when an admin-only endpoint is called, then access is granted.
- [ ] Given a customer token, when an admin-only endpoint is called, then a 403 response is returned.
- [ ] Given a missing token, when a role-guarded endpoint is called, then a 401 response is returned.
- [ ] Given the create-user endpoint, when a user is created, then the client cannot arbitrarily escalate its own role.
