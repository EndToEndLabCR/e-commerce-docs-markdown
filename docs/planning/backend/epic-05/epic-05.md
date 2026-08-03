# Epic 5: Shopping Cart

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** Customers have no way to collect items before purchase, so the store cannot support a typical purchase flow or cart-based totals.

**Objective:** Provide a shopping cart that lets customers add variants, view the cart with subtotal, tax, and total, update quantities, remove items, and persist the cart across sessions for logged-in users.

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
- [Epic 4: Product Catalog & Discovery](#epic-4-product-catalog--discovery)
- [Epic 3: Authentication & Authorization](#epic-3-authentication--authorization)
- [Functional Requirements FR3](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given a valid variant, when a customer adds it to the cart, then quantity is tracked and stock availability is validated.
- Given a cart, when the customer views it, then subtotal, tax, and total are computed server-side.
- Given a cart line, when quantity is updated or the item removed, then totals reflect the change.
- Given a logged-in user, when a new session starts, then the cart is restored from persistence.

## User Stories

- [US-MVP-BE-027: Cart Model & Add Item to Cart](./user_story027.md)
- [US-MVP-BE-028: View Cart with Computed Totals](./user_story028.md)
- [US-MVP-BE-029: Update Quantity & Remove Cart Items](./user_story029.md)
- [US-MVP-BE-030: Cart Persistence for Logged-In Users](./user_story030.md)
