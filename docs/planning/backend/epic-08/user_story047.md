# US-MVP-BE-047: Sales Dashboard Metrics

> **Epic**: [Epic 8: Admin Dashboard](./epic-08.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** expose sales metrics endpoints,
**So that** admins can see total orders, revenue, and order volume.

**Acceptance Criteria**:
- [ ] Given order data, when the metrics endpoint is queried, then total orders and total revenue are returned.
- [ ] Given a date range, when metrics are queried, then results are scoped to the range.
- [ ] Given an empty dataset, when metrics are queried, then zeroed metrics are returned without error.
- [ ] Given a non-admin token, when metrics are queried, then a 403 response is returned.
