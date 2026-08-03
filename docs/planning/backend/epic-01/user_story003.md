# US-MVP-BE-003: Structured JSON Logging with Correlation IDs

> **Epic**: [Epic 1: Backend Foundation & Infrastructure](./epic-01.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 1
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** emit structured JSON logs with request and user correlation IDs,
**So that** I can trace requests and debug issues across services.

**Acceptance Criteria**:
- [ ] Given a handled request, when a log line is emitted, then it is JSON-formatted and includes a request ID and timestamp.
- [ ] Given an authenticated request, when a log line is emitted, then it includes the user ID when available.
- [ ] Given sensitive fields, when logging, then passwords and tokens are redacted.
