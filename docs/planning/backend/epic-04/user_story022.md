# US-MVP-BE-022: Search Products by Keyword

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** search products by keyword,
**So that** customers can find designs by band name or product name.

**Acceptance Criteria**:
- [ ] Given a search term, when the search endpoint is called, then products matching the band or product name are returned.
- [ ] Given an empty or whitespace term, when search is called, then a validation error is returned or all results are listed.
- [ ] Given no matches, when search is called, then an empty result set is returned.
- [ ] Given special characters in the term, when search is called, then it is handled safely without SQL errors.
