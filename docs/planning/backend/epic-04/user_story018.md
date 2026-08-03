# US-MVP-BE-018: Product (Design) CRUD

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete products,
**So that** the catalog can represent T-shirt designs independent of size, price, and stock.

**Acceptance Criteria**:
- [ ] Given a valid product payload, when a product is created, then it is persisted with a band reference, name, description, and fit.
- [ ] Given an existing product, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a list request, when products are listed, then a paginated list is returned.
- [ ] Given a product payload with price or stock fields, when it is created, then those fields are rejected since they belong to variants.
