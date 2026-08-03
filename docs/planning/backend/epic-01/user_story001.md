# US-MVP-BE-001: App Bootstrap & Environment Configuration

> **Epic**: [Epic 1: Backend Foundation & Infrastructure](./epic-01.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 1
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** bootstrap the FastAPI app from environment-driven configuration,
**So that** the API runs consistently across local, test, stage, and production without hardcoded values.

**Acceptance Criteria**:
- [ ] Given a configured environment, when the API starts, then configuration is loaded from the correct per-environment source and `.env` overrides.
- [ ] Given a missing required setting, when the app boots, then startup fails with a clear error instead of a silent default.
- [ ] Given the app entrypoint, when the API serves, then the root and health endpoints respond.
