# Epic: Checkout & Payment

**Epic Title**: Checkout & Payment
**Epic Key**: EPIC-6
**Summary**: Enable trusted checkout by validating totals server-side, processing Stripe payments, creating orders, and confirming completion.
**Labels**: backend, checkout, payments
**Priority**: Must Have
**Components**: Backend, Payments
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: Orders cannot be placed or paid for: the current order endpoint is a bare CRUD write that trusts client-supplied totals, with no payment processing, stock checks, or confirmation.

Objective: Provide a real checkout and payment flow: collect shipping and billing addresses, process payments via Stripe, create orders server-side with validated totals and stock decrement, send a confirmation email, and support guest checkout.

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
- [Epic 5: Shopping Cart](../EPIC-5-Shopping-Cart/epic.md)
- [Epic 4: Product Catalog & Discovery](../EPIC-4-Product-Catalog-and-Discovery/epic.md)
- [Epic 1: Backend Foundation & Infrastructure](../EPIC-1-Backend-Foundation-and-Infrastructure/epic.md)
- [Functional Requirements FR4](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given a checkout with addresses, when the order is submitted, then shipping and billing addresses are captured.
- Given a payment intent, when Stripe confirms the payment, then the order transitions to paid.
- Given order line items, when the order is created, then the total is computed server-side and stock is decremented.
- Given a successful order, when it is placed, then a confirmation email is sent.
