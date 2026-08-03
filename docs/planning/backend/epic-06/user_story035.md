# US-MVP-BE-035: Guest Checkout

> **Epic**: [Epic 6: Checkout & Payment](./epic-06.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 6
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** support checkout without an account,
**So that** customers can buy without registering.

**Acceptance Criteria**:
- [ ] Given a guest checkout, when an order is placed, then the order is created without a user reference.
- [ ] Given a guest order, when it is created, then the customer can still receive a confirmation email.
- [ ] Given a guest order, when an account is later created with the same email, then the order is not automatically linked unless specified.
- [ ] Given guest checkout, when payment succeeds, then the order flow completes the same as a registered user.
