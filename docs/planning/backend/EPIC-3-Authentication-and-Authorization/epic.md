# Epic: Authentication & Authorization

**Epic Title**: Authentication & Authorization
**Epic Key**: EPIC-3
**Summary**: Add secure login, token-based access control, account verification flows, and RBAC protection for customer and admin endpoints.
**Labels**: backend, auth, security
**Priority**: Must Have
**Components**: Backend, Security
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: Users and admins cannot securely log in and no endpoint is protected, so accounts, orders, and admin functions have no access control.

Objective: Provide secure authentication and authorization: login that issues signed JWTs, token validation that resolves the current user, profile access, logout, email verification, password reset, and role-based access control.

Included scope:
- Login with email/password issuing a signed JWT
- Token validation and current-user dependency
- "Get me" (own profile) endpoint
- Logout and token revocation
- Email verification on registration
- Password reset via email
- Role-based access control guards (customer vs admin)

Excluded scope:
- OAuth/social login (Phase 3)
- Refresh-token rotation (deferred)
- Multi-factor authentication

Dependencies:
- [Epic 1: Backend Foundation & Infrastructure](../EPIC-1-Backend-Foundation-and-Infrastructure/epic.md)
- [Epic 2: User & Account Management](../EPIC-2-User-and-Account-Management/epic.md)
- [Functional Requirements FR1](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given valid credentials, when a user logs in, then a signed JWT is returned and later requests resolve the user from the token.
- Given an invalid or expired token, when a protected endpoint is called, then a 401 response is returned.
- Given a registered account, when the profile endpoint is called, then the caller receives only their own data.
- Given an admin token, when an admin-only endpoint is called, then access is granted; a customer token is rejected with 403.
