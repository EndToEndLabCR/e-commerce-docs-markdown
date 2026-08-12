# Story: User Login with JWT Issuance

**Story Title**: User Login with JWT Issuance
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to authenticate users with email and password and issue a signed JWT
**So that** customers and admins can access protected resources.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 8

---

**Acceptance Criteria:**

- Given valid credentials, when a login request is submitted, then a signed JWT is returned with the user identity and role.
- Given an incorrect password or unknown email, when a login is attempted, then a 401 response is returned without revealing which field was wrong.
- Given an inactive account, when a login is attempted, then a 403 response is returned.
- Given a login success, when the token is decoded, then it contains the expected claims and an expiry.

---

# Story: Token Validation & Current-User Dependency

**Story Title**: Token Validation & Current-User Dependency
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to validate JWTs and resolve the current user in a reusable dependency
**So that** protected endpoints can rely on a consistent auth check.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a valid token, when a protected endpoint is called, then the current user is resolved from the token claims.
- Given an expired or malformed token, when a protected endpoint is called, then a 401 response is returned.
- Given a missing `Authorization` header, when a protected endpoint is called, then a 401 response is returned.
- Given a token for a deleted user, when it is validated, then the request is rejected.

---

# Story: Get Current User Profile

**Story Title**: Get Current User Profile
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to expose a "get me" endpoint
**So that** the frontend can load the authenticated user's own profile.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given an authenticated user, when the profile endpoint is called, then their own data is returned.
- Given an unauthenticated request, when the profile endpoint is called, then a 401 response is returned.
- Given an authenticated user, when the response is returned, then it never includes the password hash.

---

# Story: Logout & Token Revocation

**Story Title**: Logout & Token Revocation
**Story Key**: STORY-4
**As a** Backend Engineer
**I want** to support logout with token revocation
**So that** a signed-out token can no longer access protected resources.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given an authenticated user, when logout is called, then the token is revoked or otherwise invalidated.
- Given a revoked token, when a protected endpoint is called, then a 401 response is returned.
- Given a repeated logout, when it is called again, then the response is safe and does not error.

---

# Story: Email Verification on Registration

**Story Title**: Email Verification on Registration
**Story Key**: STORY-5
**As a** Backend Engineer
**I want** to send a verification email on registration and verify the email address
**So that** only verified accounts can access the full store experience.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a new registration, when the user is created, then a verification email with a token is sent.
- Given a valid verification token, when the email is verified, then the account is marked verified.
- Given an expired token, when verification is attempted, then a clear error is returned and a resend option is offered.
- Given an unverified account, when a restricted action is attempted, then the action is blocked with an appropriate response.

---

# Story: Password Reset via Email

**Story Title**: Password Reset via Email
**Story Key**: STORY-6
**As a** Backend Engineer
**I want** to support password reset through an emailed link
**So that** users can recover access when they forget their password.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a registered email, when a reset is requested, then a reset link with a single-use token is emailed.
- Given a valid reset token, when a new password is submitted, then the password is updated and the old one no longer works.
- Given an invalid or expired token, when a reset is attempted, then a clear error is returned.
- Given an unknown email, when a reset is requested, then the response does not reveal whether the email exists.

---

# Story: Role-Based Access Control Guards

**Story Title**: Role-Based Access Control Guards
**Story Key**: STORY-7
**As a** Backend Engineer
**I want** to enforce role-based access control on endpoints
**So that** admin-only operations are protected from customers and vice versa.
**Labels**: backend, auth, security
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given an admin token, when an admin-only endpoint is called, then access is granted.
- Given a customer token, when an admin-only endpoint is called, then a 403 response is returned.
- Given a missing token, when a role-guarded endpoint is called, then a 401 response is returned.
- Given the create-user endpoint, when a user is created, then the client cannot arbitrarily escalate its own role.
