# US-MVP-BE-031: Checkout with Shipping & Billing Addresses

> **Epic**: [Epic 6: Checkout & Payment](./epic-06.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 6
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
