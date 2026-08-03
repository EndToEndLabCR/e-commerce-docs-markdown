# US-MVP-BE-006: Containerized Deployment

> **Epic**: [Epic 1: Backend Foundation & Infrastructure](./epic-01.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 1
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** run the API in a container behind Gunicorn,
**So that** it can be deployed to staging and production predictably.

**Acceptance Criteria**:
- [ ] Given the Docker image, when it is built, then production dependencies are installed without development packages.
- [ ] Given a container start, when the entrypoint runs, then migrations are applied before the server starts.
- [ ] Given a health check, when the container is probed, then the health endpoint returns a success status.
