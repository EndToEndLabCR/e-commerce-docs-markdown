# US-MVP-BE-028: View Cart with Computed Totals

> **Epic**: [Epic 5: Shopping Cart](./epic-05.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 5
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** return the cart with subtotal, tax, and total computed server-side,
**So that** the frontend always displays accurate amounts.

**Acceptance Criteria**:
- [ ] Given a cart with items, when it is fetched, then subtotal is computed from current unit prices and quantities.
- [ ] Given a tax rate configuration, when the cart is fetched, then tax is applied to the subtotal.
- [ ] Given the cart, when it is fetched, then the total is the sum of subtotal and tax.
- [ ] Given an empty cart, when it is fetched, then zeroed totals are returned without error.
