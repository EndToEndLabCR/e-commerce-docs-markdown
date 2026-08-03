# US-MVP-BE-017: Band CRUD

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete bands,
**So that** the catalog can group products by artist.

**Acceptance Criteria**:
- [ ] Given a valid band payload, when a band is created, then it is persisted with a unique name.
- [ ] Given a duplicate band name, when a band is created, then a conflict response is returned.
- [ ] Given an existing band, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a list request, when bands are listed, then a paginated list is returned.
