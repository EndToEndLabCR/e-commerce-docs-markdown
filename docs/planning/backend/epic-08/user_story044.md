# US-MVP-BE-044: Admin User Management

> **Epic**: [Epic 8: Admin Dashboard](./epic-08.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** provide admin endpoints to view and disable user accounts,
**So that** admins can manage the customer base.

**Acceptance Criteria**:
- [ ] Given an admin token, when users are listed, then all accounts are returned with pagination.
- [ ] Given a user, when an admin disables the account, then the user can no longer log in or access protected resources.
- [ ] Given a user, when an admin changes their role, then the change is persisted.
- [ ] Given a non-admin token, when user management is attempted, then a 403 response is returned.
