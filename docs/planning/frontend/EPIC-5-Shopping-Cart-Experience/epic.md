# Epic: Shopping Cart Experience

**Epic Title**: Shopping Cart Experience
**Epic Key**: EPIC-5
**Summary**: Let customers add selected product variants, inspect current totals, adjust quantities, remove items, and continue to checkout.
**Labels**: frontend, cart, checkout-prep
**Priority**: Must Have
**Components**: Frontend, Cart
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: Customers cannot collect products or verify totals before checkout because the frontend lacks cart state, cart UI, and the backend cart integration.

Objective: Deliver a cart experience that keeps the global item count current and clearly communicates item availability, quantities, calculated totals, and checkout readiness.

Included scope:
- Add-to-cart feedback and current cart badge
- Cart page with line items, totals, and availability warnings
- Quantity update and remove interactions with optimistic feedback and rollback
- Empty-cart and authentication-aware persistence messaging

Excluded scope:
- Coupons, promotions, and wishlists (Phase 1)

Dependencies:
- [Epic 3: Catalog & Product Discovery](../EPIC-3-Catalog-and-Product-Discovery/epic.md)
- [Epic 4: Authentication & Account Experience](../EPIC-4-Authentication-and-Account-Experience/epic.md)
- [Backend Epic 5: Shopping Cart](../../backend/EPIC-5-Shopping-Cart/epic.md)
- [Functional Requirements FR3](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given an in-stock variant, when it is added to cart, then the header count and cart contents update.
- Given a quantity or removal mutation, when the backend accepts or rejects it, then the visible cart reconciles to the server response.
- Given an empty cart, when the cart page loads, then a clear continue-shopping path is provided.
