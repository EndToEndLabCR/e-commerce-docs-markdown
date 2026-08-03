# US-MVP-BE-033: Server-Side Order Creation with Totals & Stock

> **Epic**: [Epic 6: Checkout & Payment](./epic-06.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 6
**Priority**: Must Have
**Effort Estimate**: 8

**As a** Backend Engineer,
**I want to** create orders server-side from cart line items with computed totals and stock decrement,
**So that** clients cannot tamper with prices or oversell inventory.

**Acceptance Criteria**:
- [ ] Given cart line items, when an order is created, then the total is computed server-side from unit prices and quantities, ignoring client-supplied totals.
- [ ] Given a valid order, when it is created, then an order number is generated and order items snapshot the purchased variants.
- [ ] Given an order creation, when stock is available, then variant stock quantities are decremented.
- [ ] Given insufficient stock, when an order is attempted, then the order fails and stock is not changed.
