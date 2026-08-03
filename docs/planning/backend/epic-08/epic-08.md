# Epic 8: Admin Dashboard

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** Store operators have no administrative endpoints or role-based protection to manage users, products, inventory, and orders, and there are no business metrics available.

**Objective:** Provide an admin capability layer: admin authentication through RBAC plus guarded management endpoints for users, products/inventory, and orders, and a sales metrics endpoint.

Included scope:
- Admin authentication and authorization (role guard)
- Admin user management (view, disable)
- Admin product and inventory management
- Admin order management (view, update status)
- Sales dashboard metrics endpoints

Excluded scope:
- Admin frontend UI (frontend epic)
- Advanced analytics and cohort reporting (Phase 2)

Dependencies:
- [Epic 3: Authentication & Authorization](#epic-3-authentication--authorization)
- [Epic 4: Product Catalog & Discovery](#epic-4-product-catalog--discovery)
- [Epic 7: Order Management](#epic-7-order-management)
- [Functional Requirements FR6](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given an admin token, when an admin endpoint is called, then access is granted; a non-admin token is rejected with 403.
- Given admin privileges, when users, products, or orders are managed, then the admin can view and modify them.
- Given order data, when the sales endpoint is queried, then total orders and revenue are returned.

## User Stories

- [US-MVP-BE-043: Admin Authentication & Authorization](./user_story043.md)
- [US-MVP-BE-044: Admin User Management](./user_story044.md)
- [US-MVP-BE-045: Admin Product & Inventory Management](./user_story045.md)
- [US-MVP-BE-046: Admin Order Management](./user_story046.md)
- [US-MVP-BE-047: Sales Dashboard Metrics](./user_story047.md)
