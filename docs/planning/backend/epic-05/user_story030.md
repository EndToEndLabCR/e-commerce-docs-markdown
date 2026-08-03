# US-MVP-BE-030: Cart Persistence for Logged-In Users

> **Epic**: [Epic 5: Shopping Cart](./epic-05.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 5
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** persist the cart for logged-in users,
**So that** the cart survives session changes and device switches.

**Acceptance Criteria**:
- [ ] Given a logged-in user, when they add items, then the cart is stored against the user account.
- [ ] Given a new session, when the user logs in, then their saved cart is loaded.
- [ ] Given a merge scenario with an anonymous cart, when the user logs in, then the carts are merged predictably.
- [ ] Given an item that is no longer available, when the cart is loaded, then it is handled gracefully with a notice.
