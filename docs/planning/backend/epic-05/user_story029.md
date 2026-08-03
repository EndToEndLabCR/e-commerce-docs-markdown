# US-MVP-BE-029: Update Quantity & Remove Cart Items

> **Epic**: [Epic 5: Shopping Cart](./epic-05.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 5
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** update line quantities and remove items from the cart,
**So that** customers can correct mistakes before checkout.

**Acceptance Criteria**:
- [ ] Given an existing cart line, when the quantity is updated, then the change is persisted and totals recompute.
- [ ] Given a quantity above available stock, when it is updated, then a clear error is returned.
- [ ] Given a quantity of zero, when it is updated, then the line is removed from the cart.
- [ ] Given an existing cart line, when it is removed, then it is deleted and totals update.
