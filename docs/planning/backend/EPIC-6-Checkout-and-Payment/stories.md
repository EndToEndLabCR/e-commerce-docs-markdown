# Stories for Epic: Checkout & Payment

## Backend Engineer

### US-EP6-BE-001: Checkout with Shipping and Billing Addresses

**Story ID**: US-EP6-BE-001
**Epic Link**: EPIC-6
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** collect shipping and billing addresses at checkout,
**So that** orders carry the addresses needed for fulfillment and payment.

**Acceptance Criteria**:

- [ ] Given a checkout request, when it is submitted, then shipping and billing addresses are validated and captured.
- [ ] Given a billing address marked as the same as shipping, when checkout runs, then the billing address is copied from shipping.
- [ ] Given an incomplete or invalid address, when checkout is attempted, then a validation error is returned.
- [ ] Given an order, when it is created, then the addresses are stored as immutable snapshots.

**Deliverables**:

- Address collection and validation for checkout
- Immutable address snapshot on the order record

**Success Metrics**:

- Order addresses remain unchanged even if the customer later edits their saved address.

---

### US-EP6-BE-002: Payment Processing with Stripe

**Story ID**: US-EP6-BE-002
**Epic Link**: EPIC-6
**Priority**: Must Have
**Effort Estimate**: 8

**As a** Backend Engineer,
**I want to** process payments through Stripe,
**So that** customers can pay for their orders with a credit card.

**Acceptance Criteria**:

- [ ] Given a checkout total, when the customer pays, then a Stripe payment intent is created for the correct amount and currency.
- [ ] Given a successful payment, when Stripe confirms it, then the order transitions to paid.
- [ ] Given a declined or failed payment, when it occurs, then a clear error is returned and the order is not marked paid.
- [ ] Given a webhook, when Stripe notifies the API, then the event is verified with the signing secret before handling.

**Deliverables**:

- Stripe payment intent creation and confirmation flow
- Verified webhook handler for payment events

**Success Metrics**:

- Unverified or forged webhook events are always rejected.

---

### US-EP6-BE-003: Server-Side Order Creation with Totals and Stock

**Story ID**: US-EP6-BE-003
**Epic Link**: EPIC-6
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

**Deliverables**:

- Server-side order total calculation
- Atomic stock decrement tied to order creation

**Success Metrics**:

- Client-supplied totals are never used to price an order.

---

### US-EP6-BE-004: Order Confirmation Email

**Story ID**: US-EP6-BE-004
**Epic Link**: EPIC-6
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** send an order confirmation email,
**So that** customers receive proof of their purchase.

**Acceptance Criteria**:

- [ ] Given a successful order, when it is placed, then a confirmation email with the order summary is sent to the customer.
- [ ] Given an email delivery failure, when the email cannot be sent, then the order remains valid and the failure is logged.
- [ ] Given the email template, when it is rendered, then it includes the order number, items, and total.

**Deliverables**:

- Order confirmation email template and delivery
- Logged failure handling that does not block order completion

**Success Metrics**:

- Email delivery failures never invalidate a completed order.

---

### US-EP6-BE-005: Guest Checkout

**Story ID**: US-EP6-BE-005
**Epic Link**: EPIC-6
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** support checkout without an account,
**So that** customers can buy without registering.

**Acceptance Criteria**:

- [ ] Given a guest checkout, when an order is placed, then the order is created without a user reference.
- [ ] Given a guest order, when it is created, then the customer can still receive a confirmation email.
- [ ] Given a guest order, when an account is later created with the same email, then the order is not automatically linked unless specified.
- [ ] Given guest checkout, when payment succeeds, then the order flow completes the same as a registered user.

**Deliverables**:

- Guest checkout path with no user association
- Confirmation email support for guest orders

**Success Metrics**:

- Guest orders complete through the same payment flow as registered users.
