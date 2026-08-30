# Stories for Epic: Admin Dashboard

## Backend Engineer

### US-EP8-BE-001: Admin Authentication and Authorization

**Story ID**: US-EP8-BE-001
**Epic Link**: EPIC-8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** protect admin endpoints with an admin role guard,
**So that** only authorized admins can manage the store.

**Acceptance Criteria**:

- [ ] Given an admin user, when they log in, then their token carries the admin role.
- [ ] Given an admin token, when an admin endpoint is called, then access is granted.
- [ ] Given a customer token, when an admin endpoint is called, then a 403 response is returned.
- [ ] Given a missing token, when an admin endpoint is called, then a 401 response is returned.

**Deliverables**:

- Admin role claim on issued tokens
- Reusable admin role guard for admin routes

**Success Metrics**:

- No non-admin token can reach an admin-protected endpoint.

---

### US-EP8-BE-002: Admin User Management

**Story ID**: US-EP8-BE-002
**Epic Link**: EPIC-8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** provide admin endpoints to view and disable user accounts,
**So that** admins can manage the customer base.

**Acceptance Criteria**:

- [ ] Given an admin token, when users are listed, then all accounts are returned with pagination.
- [ ] Given a user, when an admin disables the account, then the user can no longer log in or access protected resources.
- [ ] Given a user, when an admin changes their role, then the change is persisted.
- [ ] Given a non-admin token, when user management is attempted, then a 403 response is returned.

**Deliverables**:

- Admin user listing, disable, and role-management endpoints

**Success Metrics**:

- Disabled accounts are immediately blocked from authenticating.

---

### US-EP8-BE-003: Admin Product and Inventory Management

**Story ID**: US-EP8-BE-003
**Epic Link**: EPIC-8
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** provide admin endpoints to manage products and inventory,
**So that** admins can maintain the catalog and stock levels.

**Acceptance Criteria**:

- [ ] Given an admin token, when a product or variant is created, updated, or deactivated, then the change is persisted.
- [ ] Given a variant, when an admin updates stock, then the stock quantity is updated.
- [ ] Given a deactivated product, when it is viewed in the store catalog, then it is not returned.
- [ ] Given a non-admin token, when inventory management is attempted, then a 403 response is returned.

**Deliverables**:

- Admin product and variant management endpoints
- Deactivation flag excluding products from customer-facing catalog

**Success Metrics**:

- Deactivated products never appear in customer catalog responses.

---

### US-EP8-BE-004: Admin Order Management

**Story ID**: US-EP8-BE-004
**Epic Link**: EPIC-8
**Priority**: Should Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** provide admin endpoints to view all orders and update their status,
**So that** admins can process and track every order.

**Acceptance Criteria**:

- [ ] Given an admin token, when orders are listed, then all orders across all users are returned.
- [ ] Given an order, when an admin updates its status, then the change follows the allowed state machine.
- [ ] Given an order lookup, when an admin fetches it, then its items and history are included.
- [ ] Given a non-admin token, when order management is attempted, then a 403 response is returned.

**Deliverables**:

- Admin order listing and status-update endpoints
- Full order detail responses including items and status history

**Success Metrics**:

- All admin order status updates comply with the defined state machine.

---

### US-EP8-BE-005: Sales Dashboard Metrics

**Story ID**: US-EP8-BE-005
**Epic Link**: EPIC-8
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

**Deliverables**:

- Sales metrics endpoint with date-range filtering

**Success Metrics**:

- Metrics endpoints return accurate totals for any valid date range.
