# Epic 7: Order Management

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** Orders and order items can be created and read back, but there is no enforceable status lifecycle, per-user history, tracking, cancellation, or reorder capability.

**Objective:** Provide full order management: order and order-item CRUD with immutable snapshots, an enforceable status state machine, per-user order history, status tracking, cancellation before shipment, and reorder.

Included scope:
- Order CRUD
- Order item immutable snapshots
- Order status state machine (pending, paid, cancelled; extend to shipped, delivered)
- Order history for registered users
- Order status tracking
- Cancel order before shipment
- Reorder a previous purchase

Excluded scope:
- Shipment provider integrations (V2)
- Returns and refunds workflow (V2)

Dependencies:
- [Epic 6: Checkout & Payment](#epic-6-checkout--payment)
- [Epic 3: Authentication & Authorization](#epic-3-authentication--authorization)
- [Functional Requirements FR5](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given an order, when its status changes, then only valid transitions are allowed.
- Given a registered user, when orders are queried, then only their own orders are returned.
- Given an unpaid, unshipped order, when the customer cancels, then the order is marked cancelled and stock is restored.
- Given a past order, when the customer reorders, then a new order is created from the previous line items.

## User Stories

- [US-MVP-BE-036: Order CRUD](./user_story036.md)
- [US-MVP-BE-037: Order Item Immutable Snapshots](./user_story037.md)
- [US-MVP-BE-038: Order Status State Machine](./user_story038.md)
- [US-MVP-BE-039: Order History for Registered Users](./user_story039.md)
- [US-MVP-BE-040: Order Status Tracking](./user_story040.md)
- [US-MVP-BE-041: Cancel Order Before Shipment](./user_story041.md)
- [US-MVP-BE-042: Reorder a Previous Purchase](./user_story042.md)
