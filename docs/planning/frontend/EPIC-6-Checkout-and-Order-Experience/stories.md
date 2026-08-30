# Stories for Epic: Checkout & Order Experience

## Frontend Engineer

### US-EP6-FE-001: Collect and Validate Checkout Information

**Story ID**: US-EP6-FE-001
**Epic Link**: EPIC-6
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Customer,
**I want to** enter shipping information and review my cart before payment,
**So that** I can submit a complete, accurate order.

**Acceptance Criteria**:

- [ ] Given checkout loads with a valid cart, when the page renders, then it displays the server-calculated order summary and shipping-address fields.
- [ ] Given a saved default address, when an authenticated customer begins checkout, then it can be selected or edited.
- [ ] Given invalid required address data, when I continue, then field-specific validation prevents payment submission.
- [ ] Given a guest shopper, when checkout begins, then email and shipping information can be entered without requiring account creation.

**Deliverables**:

- Checkout route, address form, order summary, and guest checkout support

**Success Metrics**:

- Payment cannot begin until checkout has valid required customer and address input.

---

### US-EP6-FE-002: Process Payment and Show Order Confirmation

**Story ID**: US-EP6-FE-002
**Epic Link**: EPIC-6
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Customer,
**I want to** complete payment and receive a clear order confirmation,
**So that** I know whether my purchase was successful.

**Acceptance Criteria**:

- [ ] Given valid checkout information, when I submit payment, then the interface prevents duplicate submissions until the payment flow resolves.
- [ ] Given a payment confirmation requirement or failure, when it occurs, then the UI communicates the next action without losing valid checkout information.
- [ ] Given a completed order, when the confirmation page opens, then it displays the returned order number, items, address, total, and next steps.
- [ ] Given successful checkout, when the cart cache refreshes, then purchased lines and the header count are cleared or reconciled to the backend response.

**Deliverables**:

- Payment-provider handoff and payment-state feedback
- Order-confirmation route and cart reconciliation

**Success Metrics**:

- A single checkout action cannot create duplicate visible orders.

---

### US-EP6-FE-003: Provide Customer Order History and Details

**Story ID**: US-EP6-FE-003
**Epic Link**: EPIC-6
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Customer,
**I want to** view my orders, their details, and current tracking status,
**So that** I can follow purchases after checkout.

**Acceptance Criteria**:

- [ ] Given an authenticated customer, when the order-history page loads, then it lists only API-returned orders with number, date, total, and status.
- [ ] Given an order detail route, when it loads, then it displays immutable item details, shipping information, payment summary, and status timeline supplied by the API.
- [ ] Given an eligible order, when cancellation or reorder is offered, then the UI requires confirmation and reconciles the result with the refreshed cart or order state.
- [ ] Given a guest order lookup flow is available from the API, when email and order number match, then the order can be viewed without exposing unrelated customer data.

**Deliverables**:

- Protected order-history and order-detail routes
- Cancellation, reorder, and guest-tracking experiences conditioned on API capabilities

**Success Metrics**:

- The order UI never derives ownership or status transitions locally; it renders the backend-authorized result.
