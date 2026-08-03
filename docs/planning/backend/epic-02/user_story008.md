# US-MVP-BE-008: User Profile Management

> **Epic**: [Epic 2: User & Account Management](./epic-02.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 2
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** retrieve, update, and delete user profiles,
**So that** customers can manage their account data.

**Acceptance Criteria**:
- [ ] Given an existing user ID, when the profile is fetched, then the user data is returned.
- [ ] Given a valid update payload, when the profile is updated, then the changed fields are persisted.
- [ ] Given an existing user ID, when the profile is deleted, then the user is removed and a confirmation is returned.
- [ ] Given a non-existent user ID, when any profile operation runs, then a 404 response is returned.
