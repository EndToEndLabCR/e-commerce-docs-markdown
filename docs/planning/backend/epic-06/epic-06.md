# Epic 6: Checkout & Payment

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** Orders cannot be placed or paid for: the current order endpoint is a bare CRUD write that trusts client-supplied totals, with no payment processing, stock checks, or confirmation.

**Objective:** Provide a real checkout and payment flow: collect shipping and billing addresses, process payments via Stripe, create orders server-side with validated totals and stock decrement, send a confirmation email, and support guest checkout.

Included scope:
- Checkout with shipping and billing address collection
- Payment processing with Stripe
- Server-side order creation with totals from line items and stock decrement
- Order confirmation email
- Guest checkout (orders without an account)

Excluded scope:
- Promo codes (Phase 1)
- Refund and dispute handling
- Multi-currency payments (Phase 3)

Dependencies:
- [Epic 5: Shopping Cart](#epic-5-shopping-cart)
- [Epic 4: Product Catalog & Discovery](#epic-4-product-catalog--discovery)
- [Epic 1: Backend Foundation & Infrastructure](#epic-1-backend-foundation--infrastructure)
- [Functional Requirements FR4](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given a checkout with addresses, when the order is submitted, then shipping and billing addresses are captured.
- Given a payment intent, when Stripe confirms the payment, then the order transitions to paid.
- Given order line items, when the order is created, then the total is computed server-side and stock is decremented.
- Given a successful order, when it is placed, then a confirmation email is sent.

## User Stories

- [US-MVP-BE-031: Checkout with Shipping & Billing Addresses](./user_story031.md)
- [US-MVP-BE-032: Payment Processing with Stripe](./user_story032.md)
- [US-MVP-BE-033: Server-Side Order Creation with Totals & Stock](./user_story033.md)
- [US-MVP-BE-034: Order Confirmation Email](./user_story034.md)
- [US-MVP-BE-035: Guest Checkout](./user_story035.md)
