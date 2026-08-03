# US-MVP-BE-039: Order History for Registered Users

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** return a user's own order history,
**So that** registered customers can review their past orders.

**Acceptance Criteria**:
- [ ] Given a registered user, when their orders are queried, then only orders belonging to them are returned.
- [ ] Given another user's order ID, when it is requested, then access is denied.
- [ ] Given a pagination request, when history is returned, then the list is paginated.
