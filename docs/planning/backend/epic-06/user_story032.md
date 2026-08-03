# US-MVP-BE-032: Payment Processing with Stripe

> **Epic**: [Epic 6: Checkout & Payment](./epic-06.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 6
**Priority**: Must Have
**Effort Estimate**: 8

**As a** Backend Engineer,
**I want to** process payments through Stripe,
**So that** customers can pay for their orders with a credit card.

**Acceptance Criteria**:
- [ ] Given a checkout total, when the customer pays, then a Stripe payment intent is created for the correct amount and currency.
- [ ] Given a successful payment, when Stripe confirms it, then the order transitions to paid.
- [ ] Given a declined or failed payment, when it occurs, then a clear error is returned and the order is not marked paid.
- [ ] Given a webhook, when Stripe notifies the API, then the event is verified with the signing secret before handling.
