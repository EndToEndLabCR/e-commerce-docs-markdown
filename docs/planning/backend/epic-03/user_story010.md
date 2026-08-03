# US-MVP-BE-010: User Login with JWT Issuance

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
**Priority**: Must Have
**Effort Estimate**: 8

**As a** Backend Engineer,
**I want to** authenticate users with email and password and issue a signed JWT,
**So that** customers and admins can access protected resources.

**Acceptance Criteria**:
- [ ] Given valid credentials, when a login request is submitted, then a signed JWT is returned with the user identity and role.
- [ ] Given an incorrect password or unknown email, when a login is attempted, then a 401 response is returned without revealing which field was wrong.
- [ ] Given an inactive account, when a login is attempted, then a 403 response is returned.
- [ ] Given a login success, when the token is decoded, then it contains the expected claims and an expiry.
