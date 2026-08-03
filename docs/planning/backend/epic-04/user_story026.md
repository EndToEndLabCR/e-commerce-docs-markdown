# US-MVP-BE-026: Foreign-Key Constraints & ORM Relationships

> **Epic**: [Epic 4: Product Catalog & Discovery](./epic-04.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 4
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** enforce foreign keys and ORM relationships between catalog tables,
**So that** referential integrity is guaranteed at the database level.

**Acceptance Criteria**:
- [ ] Given the schema, when it is inspected, then foreign keys exist between products-bands, variants-products, and variants-sizes.
- [ ] Given a delete on a parent record with children, when the delete is attempted, then it is blocked by the constraint or handled gracefully.
- [ ] Given ORM models, when relationships are defined, then related data can be loaded via the ORM.
- [ ] Given a migration, when it is applied, then the constraints are created and the chain upgrades cleanly.
