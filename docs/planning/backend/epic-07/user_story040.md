# US-MVP-BE-040: Order Status Tracking

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** expose order status and status history,
**So that** customers can track where their order is.

**Acceptance Criteria**:
- [ ] Given an order, when it is fetched, then its current status is returned.
- [ ] Given status changes, when the order is fetched, then the history of status changes is available.
- [ ] Given a status timestamp, when history is returned, then each change includes a timestamp.
