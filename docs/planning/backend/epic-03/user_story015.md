# US-MVP-BE-015: Password Reset via Email

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
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
