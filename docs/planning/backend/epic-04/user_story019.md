# US-MVP-BE-019: T-Shirt Size Lookup CRUD

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** manage the standardized t-shirt size lookup table,
**So that** variants can reference a shared, non-duplicated size set.

**Acceptance Criteria**:
- [ ] Given a valid size payload, when a size is created, then it is persisted with a unique size value.
- [ ] Given a duplicate size, when a size is created, then a conflict response is returned.
- [ ] Given an existing size, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a list request, when sizes are listed, then all supported sizes are returned.
