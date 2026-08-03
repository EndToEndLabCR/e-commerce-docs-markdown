# US-MVP-BE-034: Order Confirmation Email

> **Epic**: [Epic 6: Checkout & Payment](./epic-06.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 6
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** send an order confirmation email,
**So that** customers receive proof of their purchase.

**Acceptance Criteria**:
- [ ] Given a successful order, when it is placed, then a confirmation email with the order summary is sent to the customer.
- [ ] Given an email delivery failure, when the email cannot be sent, then the order remains valid and the failure is logged.
- [ ] Given the email template, when it is rendered, then it includes the order number, items, and total.
