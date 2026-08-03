# US-MVP-BE-042: Reorder a Previous Purchase

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Should Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** create a new order from a previous order's line items,
**So that** customers can quickly repurchase the same items.

**Acceptance Criteria**:
- [ ] Given a prior order, when reorder is requested, then a new order is created with the same line items.
- [ ] Given an item that is no longer available or out of stock, when reorder runs, then a clear error identifies the unavailable item.
- [ ] Given a reorder, when it is created, then current variant prices and stock are used.
