# US-MVP-BE-009: List Users Endpoint

> **Epic**: [Epic 2: User & Account Management](./epic-02.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 2
**Priority**: Must Have
**Effort Estimate**: 2

**As a** Backend Engineer,
**I want to** list users with pagination,
**So that** the account population can be browsed and paged consistently with other features.

**Acceptance Criteria**:
- [ ] Given a list request, when users are queried, then a paginated list of users is returned.
- [ ] Given `limit` and `offset` parameters, when users are listed, then the result honors them.
- [ ] Given an empty dataset, when users are listed, then an empty list is returned without error.
