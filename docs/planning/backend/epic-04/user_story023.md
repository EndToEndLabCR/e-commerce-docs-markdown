# US-MVP-BE-023: Filter Products by Multiple Criteria

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** filter products by size, color, price range, fit, and genre,
**So that** customers can narrow the catalog to what they want.

**Acceptance Criteria**:
- [ ] Given filter parameters, when products are queried, then results honor every supplied criterion.
- [ ] Given a price range, when filtering, then only variants within the range are returned.
- [ ] Given a size filter, when filtering, then only products with a matching variant are returned.
- [ ] Given conflicting filters with no matches, when queried, then an empty result set is returned.
