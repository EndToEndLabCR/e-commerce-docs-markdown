# Story: Admin Authentication & Authorization

**Story Title**: Admin Authentication & Authorization
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to protect admin endpoints with an admin role guard
**So that** only authorized admins can manage the store.
**Labels**: backend, admin, operations
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given an admin user, when they log in, then their token carries the admin role.
- Given an admin token, when an admin endpoint is called, then access is granted.
- Given a customer token, when an admin endpoint is called, then a 403 response is returned.
- Given a missing token, when an admin endpoint is called, then a 401 response is returned.

---

# Story: Admin User Management

**Story Title**: Admin User Management
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to provide admin endpoints to view and disable user accounts
**So that** admins can manage the customer base.
**Labels**: backend, admin, operations
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given an admin token, when users are listed, then all accounts are returned with pagination.
- Given a user, when an admin disables the account, then the user can no longer log in or access protected resources.
- Given a user, when an admin changes their role, then the change is persisted.
- Given a non-admin token, when user management is attempted, then a 403 response is returned.

---

# Story: Admin Product & Inventory Management

**Story Title**: Admin Product & Inventory Management
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to provide admin endpoints to manage products and inventory
**So that** admins can maintain the catalog and stock levels.
**Labels**: backend, admin, operations
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given an admin token, when a product or variant is created, updated, or deactivated, then the change is persisted.
- Given a variant, when an admin updates stock, then the stock quantity is updated.
- Given a deactivated product, when it is viewed in the store catalog, then it is not returned.
- Given a non-admin token, when inventory management is attempted, then a 403 response is returned.

---

# Story: Admin Order Management

**Story Title**: Admin Order Management
**Story Key**: STORY-4
**As a** Backend Engineer
**I want** to provide admin endpoints to view all orders and update their status
**So that** admins can process and track every order.
**Labels**: backend, admin, operations
**Priority**: Should Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given an admin token, when orders are listed, then all orders across all users are returned.
- Given an order, when an admin updates its status, then the change follows the allowed state machine.
- Given an order lookup, when an admin fetches it, then its items and history are included.
- Given a non-admin token, when order management is attempted, then a 403 response is returned.

---

# Story: Sales Dashboard Metrics

**Story Title**: Sales Dashboard Metrics
**Story Key**: STORY-5
**As a** Backend Engineer
**I want** to expose sales metrics endpoints
**So that** admins can see total orders, revenue, and order volume.
**Labels**: backend, admin, operations
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given order data, when the metrics endpoint is queried, then total orders and total revenue are returned.
- Given a date range, when metrics are queried, then results are scoped to the range.
- Given an empty dataset, when metrics are queried, then zeroed metrics are returned without error.
- Given a non-admin token, when metrics are queried, then a 403 response is returned.
