# Story: Cart Model & Add Item to Cart

**Story Title**: Cart Model & Add Item to Cart
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to model a cart and add product variants to it
**So that** customers can collect items before checkout.
**Labels**: backend, cart, checkout-prep
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a valid variant ID and quantity, when an item is added, then it is stored in the cart and stock availability is validated.
- Given an item already in the cart, when it is added again, then the quantity is incremented rather than duplicated.
- Given an out-of-stock variant, when it is added, then a clear error is returned.
- Given a cart, when an item is added, then the cart is associated with the current user or session.

---

# Story: View Cart with Computed Totals

**Story Title**: View Cart with Computed Totals
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to return the cart with subtotal, tax, and total computed server-side
**So that** the frontend always displays accurate amounts.
**Labels**: backend, cart, checkout-prep
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a cart with items, when it is fetched, then subtotal is computed from current unit prices and quantities.
- Given a tax rate configuration, when the cart is fetched, then tax is applied to the subtotal.
- Given the cart, when it is fetched, then the total is the sum of subtotal and tax.
- Given an empty cart, when it is fetched, then zeroed totals are returned without error.

---

# Story: Update Quantity & Remove Cart Items

**Story Title**: Update Quantity & Remove Cart Items
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to update line quantities and remove items from the cart
**So that** customers can correct mistakes before checkout.
**Labels**: backend, cart, checkout-prep
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given an existing cart line, when the quantity is updated, then the change is persisted and totals recompute.
- Given a quantity above available stock, when it is updated, then a clear error is returned.
- Given a quantity of zero, when it is updated, then the line is removed from the cart.
- Given an existing cart line, when it is removed, then it is deleted and totals update.

---

# Story: Cart Persistence for Logged-In Users

**Story Title**: Cart Persistence for Logged-In Users
**Story Key**: STORY-4
**As a** Backend Engineer
**I want** to persist the cart for logged-in users
**So that** the cart survives session changes and device switches.
**Labels**: backend, cart, checkout-prep
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a logged-in user, when they add items, then the cart is stored against the user account.
- Given a new session, when the user logs in, then their saved cart is loaded.
- Given a merge scenario with an anonymous cart, when the user logs in, then the carts are merged predictably.
- Given an item that is no longer available, when the cart is loaded, then it is handled gracefully with a notice.
