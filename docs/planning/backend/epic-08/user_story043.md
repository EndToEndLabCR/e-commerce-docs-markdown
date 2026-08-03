# US-MVP-BE-043: Admin Authentication & Authorization

> **Epic**: [Epic 8: Admin Dashboard](./epic-08.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** protect admin endpoints with an admin role guard,
**So that** only authorized admins can manage the store.

**Acceptance Criteria**:
- [ ] Given an admin user, when they log in, then their token carries the admin role.
- [ ] Given an admin token, when an admin endpoint is called, then access is granted.
- [ ] Given a customer token, when an admin endpoint is called, then a 403 response is returned.
- [ ] Given a missing token, when an admin endpoint is called, then a 401 response is returned.
