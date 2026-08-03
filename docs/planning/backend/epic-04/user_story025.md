# US-MVP-BE-025: Product Images

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Could Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** store product image references,
**So that** product detail pages can display design images.

**Acceptance Criteria**:
- [ ] Given an image URL, when a product is created or updated, then the image reference is persisted.
- [ ] Given a product response, when it is returned, then image references are included.
- [ ] Given a missing image, when a product is returned, then the response degrades gracefully without error.
