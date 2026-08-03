# US-MVP-BE-004: Dependency Injection & Composition Wiring

> **Epic**: [Epic 1: Backend Foundation & Infrastructure](./epic-01.md) · **Index**: [user-stories.md](../user-stories.md)

**Epic**: Epic 1
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** wire repositories and use cases through a composition root,
**So that** features are loosely coupled and easy to test and swap.

**Acceptance Criteria**:
- [ ] Given the composition layer, when the app resolves a use case, then its repository dependency is injected.
- [ ] Given a new feature, when its providers are added, then routes can consume them via `Depends`.
- [ ] Given the app startup, when dependency graphs are resolved, then there are no circular or missing dependencies.
