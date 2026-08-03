# US-MVP-BE-014: Email Verification on Registration

> **Epic**: [Epic 3: Authentication & Authorization](./epic-03.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 3
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
