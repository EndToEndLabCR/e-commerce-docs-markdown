# US-MVP-BE-024: Product Categories

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** assign products to categories,
**So that** customers can browse by music genre category.

**Acceptance Criteria**:
- [ ] Given a category model, when it is defined, then products can be assigned to one or more categories.
- [ ] Given a category filter, when products are queried, then only products in that category are returned.
- [ ] Given a product update, when categories change, then the assignment is persisted correctly.
- [ ] Given a deleted category, when products reference it, then the delete is handled gracefully.
