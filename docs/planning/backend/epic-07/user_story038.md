# US-MVP-BE-038: Order Status State Machine

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** enforce a defined order status state machine,
**So that** orders only move through valid transitions.

**Acceptance Criteria**:
- [ ] Given a pending order, when payment succeeds, then the status transitions to paid.
- [ ] Given an invalid transition, when it is attempted, then a validation error is returned and the status is unchanged.
- [ ] Given a cancelled or delivered order, when further updates are attempted, then they are rejected.
- [ ] Given the status enum, when it is used, then only defined values (pending, paid, cancelled; shipped, delivered) are accepted.
