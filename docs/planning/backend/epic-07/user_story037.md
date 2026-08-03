# US-MVP-BE-037: Order Item Immutable Snapshots

> **Epic**: [Epic 7: Order Management](./epic-07.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 7
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** store order items as immutable snapshots,
**So that** order history survives later catalog changes.

**Acceptance Criteria**:
- [ ] Given an order item, when it is created, then product name, band name, size, color, SKU, unit price, quantity, and line total are snapshotted.
- [ ] Given a catalog update, when a variant price or name changes, then existing order items are unaffected.
- [ ] Given an order item, when it is returned, then the line total equals unit price times quantity.
- [ ] Given an order item, when it is deleted with its order, then no orphaned rows remain.
