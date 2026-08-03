# Epic 2: User & Account Management

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** Customers need accounts to place and track orders, but the backend offers only basic user CRUD with no way to list accounts and no complete account lifecycle.

**Objective:** Provide stable user account management — create, view, update, delete, and list — with secure bcrypt password hashing, so accounts can support the authentication and order flows that depend on them.

Included scope:
- User registration with bcrypt password hashing (create user)
- User profile retrieval, update, and delete
- List users endpoint
- Role and active-status fields on the user record

Excluded scope:
- Login, token issuance, or session handling (Epic 3)
- Email verification (Epic 3)
- Admin user management (Epic 8)

Dependencies:
- [Epic 1: Backend Foundation & Infrastructure](#epic-1-backend-foundation--infrastructure)
- [Functional Requirements FR1](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given a valid email and password payload, when a user is created, then the password is stored as a bcrypt hash and the user is persisted with a role and active status.
- Given an existing user, when the profile is fetched, updated, or deleted, then the operation returns the expected result or a clear 404.
- Given a list request, when users are queried, then a paginated list of users is returned.

## User Stories

- [US-MVP-BE-007: User Registration with Password Hashing](./user_story007.md)
- [US-MVP-BE-008: User Profile Management](./user_story008.md)
- [US-MVP-BE-009: List Users Endpoint](./user_story009.md)
