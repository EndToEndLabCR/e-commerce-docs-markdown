# US-MVP-BE-027: Cart Model & Add Item to Cart

> **Epic**: [Epic 5: Shopping Cart](./epic-05.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 5
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** model a cart and add product variants to it,
**So that** customers can collect items before checkout.

**Acceptance Criteria**:
- [ ] Given a valid variant ID and quantity, when an item is added, then it is stored in the cart and stock availability is validated.
- [ ] Given an item already in the cart, when it is added again, then the quantity is incremented rather than duplicated.
- [ ] Given an out-of-stock variant, when it is added, then a clear error is returned.
- [ ] Given a cart, when an item is added, then the cart is associated with the current user or session.
