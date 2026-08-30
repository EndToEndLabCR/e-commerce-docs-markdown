# Epic: Shopping Cart

**Epic Title**: Shopping Cart
**Epic Key**: EPIC-5
**Summary**: Implement cart capabilities for item collection, quantity management, computed totals, and user cart persistence.
**Labels**: backend, cart, checkout-prep
**Priority**: Must Have
**Components**: Backend, Database
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: Customers have no way to collect items before purchase, so the store cannot support a typical purchase flow or cart-based totals.

Objective: Provide a shopping cart that lets customers add variants, view the cart with subtotal, tax, and total, update quantities, remove items, and persist the cart across sessions for logged-in users.

Included scope:
- Cart model and add-item-to-cart
- View cart with computed totals (subtotal, tax, total)
- Update quantity and remove items
- Cart persistence for logged-in users

Excluded scope:
- Coupons and promotions (Phase 1)
- Wishlist (Phase 1)
- Persisted guest carts (deferred)

Dependencies:
- [Epic 4: Product Catalog & Discovery](../EPIC-4-Product-Catalog-and-Discovery/epic.md)
- [Epic 3: Authentication & Authorization](../EPIC-3-Authentication-and-Authorization/epic.md)
- [Functional Requirements FR3](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given a valid variant, when a customer adds it to the cart, then quantity is tracked and stock availability is validated.
- Given a cart, when the customer views it, then subtotal, tax, and total are computed server-side.
- Given a cart line, when quantity is updated or the item removed, then totals reflect the change.
- Given a logged-in user, when a new session starts, then the cart is restored from persistence.
