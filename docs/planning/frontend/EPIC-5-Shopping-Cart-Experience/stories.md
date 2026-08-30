# Stories for Epic: Shopping Cart Experience

## Frontend Engineer

### US-EP5-FE-001: Add Products to the Cart

**Story ID**: US-EP5-FE-001
**Epic Link**: EPIC-5
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Customer,
**I want to** add an in-stock selected variant to my cart,
**So that** I can purchase it later in the checkout flow.

**Acceptance Criteria**:

- [ ] Given a selected in-stock variant and valid quantity, when I add it, then the cart API is called with that exact variant and quantity.
- [ ] Given a successful response, when the cart updates, then a non-blocking confirmation and updated header count are displayed.
- [ ] Given an unavailable variant or failed request, when the add action is attempted, then the UI preserves the current cart and explains the problem.

**Deliverables**:

- Typed cart mutation and cache invalidation
- Add-to-cart feedback and live global cart count

**Success Metrics**:

- The header item count matches the latest server cart response after every successful add.

---

### US-EP5-FE-002: Display the Cart and Server-Calculated Totals

**Story ID**: US-EP5-FE-002
**Epic Link**: EPIC-5
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Customer,
**I want to** review cart items and server-calculated totals,
**So that** I understand what I will pay before checkout.

**Acceptance Criteria**:

- [ ] Given a non-empty cart, when the page loads, then every line shows image, product, chosen variant, unit price, quantity, subtotal, and availability warning when needed.
- [ ] Given cart totals, when they are returned, then subtotal, tax, and total are displayed from the server response without client-side price calculation.
- [ ] Given an empty cart, when the page loads, then it shows a continue-shopping action instead of a checkout action.

**Deliverables**:

- Cart route, line-item display, total summary, and empty-cart state

**Success Metrics**:

- The frontend displays totals exactly as returned by the cart API.

---

### US-EP5-FE-003: Update and Remove Cart Items

**Story ID**: US-EP5-FE-003
**Epic Link**: EPIC-5
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Customer,
**I want to** change quantities or remove items from my cart,
**So that** my order reflects what I intend to purchase.

**Acceptance Criteria**:

- [ ] Given a valid quantity change, when it is submitted, then the line item and totals update with pending feedback.
- [ ] Given a rejected quantity update, when the server reports stock or validation failure, then the UI restores the server-confirmed cart state and explains the issue.
- [ ] Given a remove action, when it succeeds, then the line item, totals, and header count refresh.

**Deliverables**:

- Quantity controls and remove-item action with mutation feedback

**Success Metrics**:

- Failed cart mutations do not leave stale optimistic quantities or totals on screen.
