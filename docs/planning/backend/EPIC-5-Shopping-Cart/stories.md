# Stories for Epic: Shopping Cart

## Backend Engineer

### US-EP5-BE-001: Cart Model and Add Item to Cart

**Story ID**: US-EP5-BE-001
**Epic Link**: EPIC-5
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

**Deliverables**:

- Cart data model and add-item endpoint
- Stock validation on add-to-cart

**Success Metrics**:

- Adding an existing item never creates a duplicate cart line.

---

### US-EP5-BE-002: View Cart with Computed Totals

**Story ID**: US-EP5-BE-002
**Epic Link**: EPIC-5
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

**Deliverables**:

- Cart retrieval endpoint with server-computed totals
- Configurable tax rate application

**Success Metrics**:

- Cart totals are always computed server-side, never trusted from the client.

---

### US-EP5-BE-003: Update Quantity and Remove Cart Items

**Story ID**: US-EP5-BE-003
**Epic Link**: EPIC-5
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

**Deliverables**:

- Update-quantity and remove-item endpoints
- Stock validation on quantity updates

**Success Metrics**:

- Cart totals stay in sync after every quantity change or removal.

---

### US-EP5-BE-004: Cart Persistence for Logged-In Users

**Story ID**: US-EP5-BE-004
**Epic Link**: EPIC-5
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** persist the cart for logged-in users,
**So that** the cart survives session changes and device switches.

**Acceptance Criteria**:

- [ ] Given a logged-in user, when they add items, then the cart is stored against the user account.
- [ ] Given a new session, when the user logs in, then their saved cart is loaded.
- [ ] Given a merge scenario with an anonymous cart, when the user logs in, then the carts are merged predictably.
- [ ] Given an item that is no longer available, when the cart is loaded, then it is handled gracefully with a notice.

**Deliverables**:

- User-scoped cart persistence
- Anonymous-to-user cart merge logic

**Success Metrics**:

- Logged-in users retain their cart across devices and sessions.
