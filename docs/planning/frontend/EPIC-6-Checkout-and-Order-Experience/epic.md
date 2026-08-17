# Epic: Checkout & Order Experience

**Epic Title**: Checkout & Order Experience
**Epic Key**: EPIC-6
**Summary**: Guide customers through address collection, payment, confirmation, and post-purchase order history and tracking.
**Labels**: frontend, checkout, orders
**Priority**: Must Have
**Components**: Frontend, Checkout, Orders
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: The frontend has no checkout or order surfaces, so customers cannot complete purchases or review orders after purchase.

Objective: Build a validated, accessible checkout experience integrated with the server-side order and payment flow, followed by confirmation and customer order-management views.

Included scope:
- Checkout review, shipping-address form, guest checkout, and payment handoff
- Payment processing states and duplicate-submission prevention
- Confirmation page and cart refresh after completed checkout
- Authenticated order history, details, tracking, cancellation, and reorder

Excluded scope:
- Refund, dispute, and return requests (V2)
- Shipment-carrier integrations beyond API-provided tracking information

Dependencies:
- [Epic 5: Shopping Cart Experience](../EPIC-5-Shopping-Cart-Experience/epic.md)
- [Epic 4: Authentication & Account Experience](../EPIC-4-Authentication-and-Account-Experience/epic.md)
- [Backend Epic 6: Checkout & Payment](../../backend/EPIC-6-Checkout-and-Payment/epic.md)
- [Backend Epic 7: Order Management](../../backend/EPIC-7-Order-Management/epic.md)
- [Functional Requirements FR4-FR5](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given a valid cart and address, when checkout is completed, then only one payment/order submission can be in flight.
- Given a successful order, when confirmation loads, then it shows the returned order summary and the cart no longer displays purchased items.
- Given an authenticated customer, when they view orders, then only their returned history and order details are displayed.
