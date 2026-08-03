# US-MVP-BE-041: Cancel Order Before Shipment

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** allow cancelling an order before shipment,
**So that** customers can back out of orders that have not shipped.

**Acceptance Criteria**:
- [ ] Given a pending or paid but unshipped order, when the customer cancels, then the order is marked cancelled.
- [ ] Given a cancelled order, when cancellation occurs, then stock for its items is restored.
- [ ] Given a shipped or delivered order, when cancellation is attempted, then it is rejected.
- [ ] Given a cancellation, when the order is fetched, then the cancelled status is reflected.
