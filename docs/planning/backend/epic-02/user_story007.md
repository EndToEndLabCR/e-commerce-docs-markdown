# US-MVP-BE-007: User Registration with Password Hashing

> **Epic**: [Epic 2: User & Account Management](./epic-02.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 2
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create users with bcrypt password hashing,
**So that** customer credentials are stored securely.

**Acceptance Criteria**:
- [ ] Given a valid email and password, when a user is created, then the password is stored as a bcrypt hash and never as plaintext.
- [ ] Given a duplicate email, when a user is created, then a conflict response is returned and no duplicate row is inserted.
- [ ] Given an invalid email or password format, when a user is created, then a validation error is returned.
- [ ] Given a new user, when they are persisted, then a role (customer) and active status are set by default.
