# US-MVP-BE-046: Admin Order Management

> **Epic**: [Epic 8: Admin Dashboard](./epic-08.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 8
**Priority**: Should Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** provide admin endpoints to view all orders and update their status,
**So that** admins can process and track every order.

**Acceptance Criteria**:
- [ ] Given an admin token, when orders are listed, then all orders across all users are returned.
- [ ] Given an order, when an admin updates its status, then the change follows the allowed state machine.
- [ ] Given an order lookup, when an admin fetches it, then its items and history are included.
- [ ] Given a non-admin token, when order management is attempted, then a 403 response is returned.
