# Stories for Epic: Authentication & Authorization

## Backend Engineer

### US-EP3-BE-001: User Login with JWT Issuance

**Story ID**: US-EP3-BE-001
**Epic Link**: EPIC-3
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

**Deliverables**:

- Login endpoint with signed JWT issuance
- Claim structure covering identity, role, and expiry

**Success Metrics**:

- Login responses never reveal whether the email or password was incorrect.
- Every issued token includes a verifiable expiry.

---

### US-EP3-BE-002: Token Validation and Current-User Dependency

**Story ID**: US-EP3-BE-002
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** validate JWTs and resolve the current user in a reusable dependency,
**So that** protected endpoints can rely on a consistent auth check.

**Acceptance Criteria**:

- [ ] Given a valid token, when a protected endpoint is called, then the current user is resolved from the token claims.
- [ ] Given an expired or malformed token, when a protected endpoint is called, then a 401 response is returned.
- [ ] Given a missing `Authorization` header, when a protected endpoint is called, then a 401 response is returned.
- [ ] Given a token for a deleted user, when it is validated, then the request is rejected.

**Deliverables**:

- Reusable current-user dependency for protected routes
- Token validation covering expiry, malformed, and missing-header cases

**Success Metrics**:

- All protected endpoints share the same auth dependency.
- Invalid or stale tokens are consistently rejected with 401.

---

### US-EP3-BE-003: Get Current User Profile

**Story ID**: US-EP3-BE-003
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** expose a "get me" endpoint,
**So that** the frontend can load the authenticated user's own profile.

**Acceptance Criteria**:

- [ ] Given an authenticated user, when the profile endpoint is called, then their own data is returned.
- [ ] Given an unauthenticated request, when the profile endpoint is called, then a 401 response is returned.
- [ ] Given an authenticated user, when the response is returned, then it never includes the password hash.

**Deliverables**:

- Authenticated "get me" endpoint
- Response schema that excludes sensitive fields

**Success Metrics**:

- Password hashes are never exposed in any profile response.

---

### US-EP3-BE-004: Logout and Token Revocation

**Story ID**: US-EP3-BE-004
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** support logout with token revocation,
**So that** a signed-out token can no longer access protected resources.

**Acceptance Criteria**:

- [ ] Given an authenticated user, when logout is called, then the token is revoked or otherwise invalidated.
- [ ] Given a revoked token, when a protected endpoint is called, then a 401 response is returned.
- [ ] Given a repeated logout, when it is called again, then the response is safe and does not error.

**Deliverables**:

- Logout endpoint with token revocation mechanism
- Idempotent handling of repeated logout calls

**Success Metrics**:

- Revoked tokens are rejected on every subsequent request.

---

### US-EP3-BE-005: Email Verification on Registration

**Story ID**: US-EP3-BE-005
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** send a verification email on registration and verify the email address,
**So that** only verified accounts can access the full store experience.

**Acceptance Criteria**:

- [ ] Given a new registration, when the user is created, then a verification email with a token is sent.
- [ ] Given a valid verification token, when the email is verified, then the account is marked verified.
- [ ] Given an expired token, when verification is attempted, then a clear error is returned and a resend option is offered.
- [ ] Given an unverified account, when a restricted action is attempted, then the action is blocked with an appropriate response.

**Deliverables**:

- Verification email flow with single-use token
- Resend verification capability

**Success Metrics**:

- Unverified accounts cannot complete restricted actions.

---

### US-EP3-BE-006: Password Reset via Email

**Story ID**: US-EP3-BE-006
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** support password reset through an emailed link,
**So that** users can recover access when they forget their password.

**Acceptance Criteria**:

- [ ] Given a registered email, when a reset is requested, then a reset link with a single-use token is emailed.
- [ ] Given a valid reset token, when a new password is submitted, then the password is updated and the old one no longer works.
- [ ] Given an invalid or expired token, when a reset is attempted, then a clear error is returned.
- [ ] Given an unknown email, when a reset is requested, then the response does not reveal whether the email exists.

**Deliverables**:

- Password reset request and confirmation endpoints
- Single-use, expiring reset tokens

**Success Metrics**:

- Reset requests never reveal account existence for unknown emails.

---

### US-EP3-BE-007: Role-Based Access Control Guards

**Story ID**: US-EP3-BE-007
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** enforce role-based access control on endpoints,
**So that** admin-only operations are protected from customers and vice versa.

**Acceptance Criteria**:

- [ ] Given an admin token, when an admin-only endpoint is called, then access is granted.
- [ ] Given a customer token, when an admin-only endpoint is called, then a 403 response is returned.
- [ ] Given a missing token, when a role-guarded endpoint is called, then a 401 response is returned.
- [ ] Given the create-user endpoint, when a user is created, then the client cannot arbitrarily escalate its own role.

**Deliverables**:

- Reusable role-guard dependency for admin-only routes
- Safeguards preventing client-driven role escalation

**Success Metrics**:

- No customer-authenticated request can reach an admin-only endpoint.
