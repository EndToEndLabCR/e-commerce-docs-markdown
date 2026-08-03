# US-MVP-BE-021: Paginated Product Listing Envelope

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** return product listings in a shared paginated envelope,
**So that** the frontend can render paging consistently across the catalog.

**Acceptance Criteria**:
- [ ] Given a list request, when products are returned, then the response uses the shared pagination envelope with items, total, limit, and offset.
- [ ] Given `limit` and `offset` parameters, when products are listed, then the result honors them.
- [ ] Given an empty catalog, when products are listed, then an empty items list is returned without error.
