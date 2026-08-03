# US-MVP-BE-020: Product Variant CRUD

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete product variants,
**So that** sellable SKUs with size, price, and stock are managed correctly.

**Acceptance Criteria**:
- [ ] Given a valid variant payload, when a variant is created, then it is persisted with a unique SKU, product reference, size reference, price, and stock.
- [ ] Given a duplicate SKU, when a variant is created, then a conflict response is returned.
- [ ] Given an existing variant, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a variant, when it is validated, then the size reference points to an existing size.
