# Stories for Epic: Order Management

## Backend Engineer

### US-EP7-BE-001: Order CRUD

**Story ID**: US-EP7-BE-001
**Epic Link**: EPIC-7
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete orders,
**So that** orders can be managed by the API.

**Acceptance Criteria**:

- [ ] Given a valid order payload, when an order is created, then it is persisted with a generated order number and status.
- [ ] Given an existing order, when it is fetched or updated, then the operation succeeds or returns a clear 404.
- [ ] Given an existing order, when it is deleted, then its order items are handled consistently.
- [ ] Given a list request, when orders are listed, then a paginated list is returned.

**Deliverables**:

- Full CRUD endpoints for orders
- Consistent cascade handling for order items on delete

**Success Metrics**:

- Every created order has a unique, generated order number.

---

### US-EP7-BE-002: Order Item Immutable Snapshots

**Story ID**: US-EP7-BE-002
**Epic Link**: EPIC-7
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** store order items as immutable snapshots,
**So that** order history survives later catalog changes.

**Acceptance Criteria**:

- [ ] Given an order item, when it is created, then product name, band name, size, color, SKU, unit price, quantity, and line total are snapshotted.
- [ ] Given a catalog update, when a variant price or name changes, then existing order items are unaffected.
- [ ] Given an order item, when it is returned, then the line total equals unit price times quantity.
- [ ] Given an order item, when it is deleted with its order, then no orphaned rows remain.

**Deliverables**:

- Immutable order item snapshot fields
- Line total calculation consistent across order history

**Success Metrics**:

- Historical order items never change when the catalog changes.

---

### US-EP7-BE-003: Order Status State Machine

**Story ID**: US-EP7-BE-003
**Epic Link**: EPIC-7
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** enforce a defined order status state machine,
**So that** orders only move through valid transitions.

**Acceptance Criteria**:

- [ ] Given a pending order, when payment succeeds, then the status transitions to paid.
- [ ] Given an invalid transition, when it is attempted, then a validation error is returned and the status is unchanged.
- [ ] Given a cancelled or delivered order, when further updates are attempted, then they are rejected.
- [ ] Given the status enum, when it is used, then only defined values (pending, paid, cancelled; shipped, delivered) are accepted.

**Deliverables**:

- Order status enum and transition validation
- Guard preventing updates to terminal-state orders

**Success Metrics**:

- No order transitions to an invalid or undefined status.

---

### US-EP7-BE-004: Order History for Registered Users

**Story ID**: US-EP7-BE-004
**Epic Link**: EPIC-7
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** return a user's own order history,
**So that** registered customers can review their past orders.

**Acceptance Criteria**:

- [ ] Given a registered user, when their orders are queried, then only orders belonging to them are returned.
- [ ] Given another user's order ID, when it is requested, then access is denied.
- [ ] Given a pagination request, when history is returned, then the list is paginated.

**Deliverables**:

- Scoped order history endpoint for the authenticated user
- Access control preventing cross-user order access

**Success Metrics**:

- No user can retrieve another user's order data.

---

### US-EP7-BE-005: Order Status Tracking

**Story ID**: US-EP7-BE-005
**Epic Link**: EPIC-7
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** expose order status and status history,
**So that** customers can track where their order is.

**Acceptance Criteria**:

- [ ] Given an order, when it is fetched, then its current status is returned.
- [ ] Given status changes, when the order is fetched, then the history of status changes is available.
- [ ] Given a status timestamp, when history is returned, then each change includes a timestamp.

**Deliverables**:

- Status history tracking on orders
- Timestamped status change records

**Success Metrics**:

- Every status change is recorded with an accurate timestamp.

---

### US-EP7-BE-006: Cancel Order Before Shipment

**Story ID**: US-EP7-BE-006
**Epic Link**: EPIC-7
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

**Deliverables**:

- Cancel-order endpoint with shipment-status guard
- Stock restoration on cancellation

**Success Metrics**:

- Cancelling an order always restores the associated stock.

---

### US-EP7-BE-007: Reorder a Previous Purchase

**Story ID**: US-EP7-BE-007
**Epic Link**: EPIC-7
**Priority**: Should Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** create a new order from a previous order's line items,
**So that** customers can quickly repurchase the same items.

**Acceptance Criteria**:

- [ ] Given a prior order, when reorder is requested, then a new order is created with the same line items.
- [ ] Given an item that is no longer available or out of stock, when reorder runs, then a clear error identifies the unavailable item.
- [ ] Given a reorder, when it is created, then current variant prices and stock are used.

**Deliverables**:

- Reorder endpoint building a new order from a prior one
- Current-price and stock revalidation on reorder

**Success Metrics**:

- Reordered items always reflect current catalog pricing and availability.
