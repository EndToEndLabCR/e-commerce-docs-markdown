# US-MVP-BE-045: Admin Product & Inventory Management

> **Epic**: [Epic 8: Admin Dashboard](./epic-08.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** provide admin endpoints to manage products and inventory,
**So that** admins can maintain the catalog and stock levels.

**Acceptance Criteria**:
- [ ] Given an admin token, when a product or variant is created, updated, or deactivated, then the change is persisted.
- [ ] Given a variant, when an admin updates stock, then the stock quantity is updated.
- [ ] Given a deactivated product, when it is viewed in the store catalog, then it is not returned.
- [ ] Given a non-admin token, when inventory management is attempted, then a 403 response is returned.
