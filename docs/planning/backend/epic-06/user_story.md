# Story: Checkout with Shipping & Billing Addresses

**Story Title**: Checkout with Shipping & Billing Addresses
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to collect shipping and billing addresses at checkout
**So that** orders carry the addresses needed for fulfillment and payment.
**Labels**: backend, checkout, payments
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a checkout request, when it is submitted, then shipping and billing addresses are validated and captured.
- Given a billing address marked as the same as shipping, when checkout runs, then the billing address is copied from shipping.
- Given an incomplete or invalid address, when checkout is attempted, then a validation error is returned.
- Given an order, when it is created, then the addresses are stored as immutable snapshots.

---

# Story: Payment Processing with Stripe

**Story Title**: Payment Processing with Stripe
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to process payments through Stripe
**So that** customers can pay for their orders with a credit card.
**Labels**: backend, checkout, payments
**Priority**: Must Have
**Story Points**: 8

---

**Acceptance Criteria:**

- Given a checkout total, when the customer pays, then a Stripe payment intent is created for the correct amount and currency.
- Given a successful payment, when Stripe confirms it, then the order transitions to paid.
- Given a declined or failed payment, when it occurs, then a clear error is returned and the order is not marked paid.
- Given a webhook, when Stripe notifies the API, then the event is verified with the signing secret before handling.

---

# Story: Server-Side Order Creation with Totals & Stock

**Story Title**: Server-Side Order Creation with Totals & Stock
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to create orders server-side from cart line items with computed totals and stock decrement
**So that** clients cannot tamper with prices or oversell inventory.
**Labels**: backend, checkout, payments
**Priority**: Must Have
**Story Points**: 8

---

**Acceptance Criteria:**

- Given cart line items, when an order is created, then the total is computed server-side from unit prices and quantities, ignoring client-supplied totals.
- Given a valid order, when it is created, then an order number is generated and order items snapshot the purchased variants.
- Given an order creation, when stock is available, then variant stock quantities are decremented.
- Given insufficient stock, when an order is attempted, then the order fails and stock is not changed.

---

# Story: Order Confirmation Email

**Story Title**: Order Confirmation Email
**Story Key**: STORY-4
**As a** Backend Engineer
**I want** to send an order confirmation email
**So that** customers receive proof of their purchase.
**Labels**: backend, checkout, payments
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given a successful order, when it is placed, then a confirmation email with the order summary is sent to the customer.
- Given an email delivery failure, when the email cannot be sent, then the order remains valid and the failure is logged.
- Given the email template, when it is rendered, then it includes the order number, items, and total.

---

# Story: Guest Checkout

**Story Title**: Guest Checkout
**Story Key**: STORY-5
**As a** Backend Engineer
**I want** to support checkout without an account
**So that** customers can buy without registering.
**Labels**: backend, checkout, payments
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a guest checkout, when an order is placed, then the order is created without a user reference.
- Given a guest order, when it is created, then the customer can still receive a confirmation email.
- Given a guest order, when an account is later created with the same email, then the order is not automatically linked unless specified.
- Given guest checkout, when payment succeeds, then the order flow completes the same as a registered user.
