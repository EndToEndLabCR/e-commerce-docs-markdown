# US-MVP-BE-012: Get Current User Profile

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** expose a "get me" endpoint,
**So that** the frontend can load the authenticated user's own profile.

**Acceptance Criteria**:
- [ ] Given an authenticated user, when the profile endpoint is called, then their own data is returned.
- [ ] Given an unauthenticated request, when the profile endpoint is called, then a 401 response is returned.
- [ ] Given an authenticated user, when the response is returned, then it never includes the password hash.
