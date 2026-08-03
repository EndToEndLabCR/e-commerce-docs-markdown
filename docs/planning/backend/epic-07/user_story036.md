# US-MVP-BE-036: Order CRUD

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete orders,
**So that** orders can be managed by the API.

**Acceptance Criteria**:
- [ ] Given a valid order payload, when an order is created, then it is persisted with a generated order number and status.
- [ ] Given an existing order, when it is fetched or updated, then the operation succeeds or returns a clear 404.
- [ ] Given an existing order, when it is deleted, then its order items are handled consistently.
- [ ] Given a list request, when orders are listed, then a paginated list is returned.
