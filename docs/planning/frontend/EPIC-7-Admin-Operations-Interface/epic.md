# Epic: Admin Operations Interface

**Epic Title**: Admin Operations Interface
**Epic Key**: EPIC-7
**Summary**: Provide authorized store operators with responsive interfaces for sales overview, catalog and inventory maintenance, orders, and customer management.
**Labels**: frontend, admin, operations
**Priority**: Should Have
**Components**: Frontend, Admin
**Fix Version**: MVP-2

---

**Epic Description:**
Problem Statement: The frontend has no operational views for store administrators, despite the planned RBAC-protected backend admin APIs.

Objective: Implement an admin-only application area that consumes admin API contracts and supports essential operational decisions without exposing any administrative data or controls to customers.

Included scope:
- Admin route guard, navigation, and dashboard metrics
- Product, variant, and inventory management forms
- Order list, detail, and status management
- Customer list and account-status management

Excluded scope:
- Advanced analytics, cohort reporting, and bulk CSV workflows (Phase 2)

Dependencies:
- [Epic 1: Frontend Foundation & Design System](../EPIC-1-Frontend-Foundation-and-Design-System/epic.md)
- [Epic 4: Authentication & Account Experience](../EPIC-4-Authentication-and-Account-Experience/epic.md)
- [Backend Epic 8: Admin Dashboard](../../backend/EPIC-8-Admin-Dashboard/epic.md)
- [Functional Requirements FR6](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given a non-admin customer, when they navigate to an admin URL, then no operational data or controls are rendered.
- Given an administrator, when a managed record changes, then the list and detail views reconcile to the server response.
- Given a date range, when dashboard metrics load, then all displayed totals are scoped to the selected range.
