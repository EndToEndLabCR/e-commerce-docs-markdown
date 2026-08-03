# Epic 3: Authentication & Authorization

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** Users and admins cannot securely log in and no endpoint is protected, so accounts, orders, and admin functions have no access control.

**Objective:** Provide secure authentication and authorization: login that issues signed JWTs, token validation that resolves the current user, profile access, logout, email verification, password reset, and role-based access control.

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
- [Epic 1: Backend Foundation & Infrastructure](#epic-1-backend-foundation--infrastructure)
- [Epic 2: User & Account Management](#epic-2-user--account-management)
- [Functional Requirements FR1](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given valid credentials, when a user logs in, then a signed JWT is returned and later requests resolve the user from the token.
- Given an invalid or expired token, when a protected endpoint is called, then a 401 response is returned.
- Given a registered account, when the profile endpoint is called, then the caller receives only their own data.
- Given an admin token, when an admin-only endpoint is called, then access is granted; a customer token is rejected with 403.

## User Stories

- [US-MVP-BE-010: User Login with JWT Issuance](./user_story010.md)
- [US-MVP-BE-011: Token Validation & Current-User Dependency](./user_story011.md)
- [US-MVP-BE-012: Get Current User Profile](./user_story012.md)
- [US-MVP-BE-013: Logout & Token Revocation](./user_story013.md)
- [US-MVP-BE-014: Email Verification on Registration](./user_story014.md)
- [US-MVP-BE-015: Password Reset via Email](./user_story015.md)
- [US-MVP-BE-016: Role-Based Access Control Guards](./user_story016.md)
