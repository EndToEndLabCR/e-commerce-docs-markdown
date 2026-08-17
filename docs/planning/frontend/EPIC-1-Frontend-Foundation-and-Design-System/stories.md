# Stories for Epic: Frontend Foundation & Design System

## Frontend Engineer

### US-EP1-FE-001: Configure API Client and Typed Feature Endpoints

**Story ID**: US-EP1-FE-001
**Epic Link**: EPIC-1
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Frontend Engineer,
**I want to** configure the RTK Query API client and typed feature endpoint injection,
**So that** every feature calls the versioned backend consistently and benefits from shared caching and error handling.

**Acceptance Criteria**:

- [ ] Given a Vite environment, when the app starts, then the API base URL is read only from `VITE_`-prefixed configuration.
- [ ] Given a feature endpoint, when it is added, then it injects into the shared RTK Query API slice with typed request and response models.
- [ ] Given a failed API request, when the UI consumes it, then it receives a normalized error shape suitable for a user-facing message.

**Deliverables**:

- Typed RTK Query base API and feature endpoint convention
- Environment-aware API configuration

**Success Metrics**:

- No feature hardcodes an API host or version path.

---

### US-EP1-FE-002: Establish Shared Layouts, Routing, and Access Guards

**Story ID**: US-EP1-FE-002
**Epic Link**: EPIC-1
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Frontend Engineer,
**I want to** provide public, authenticated, and admin layouts with centralized route configuration,
**So that** each feature has a consistent shell and access boundary.

**Acceptance Criteria**:

- [ ] Given a public route, when it renders, then it uses the shared header, content area, and footer.
- [ ] Given an unauthenticated visitor to a protected route, when navigation occurs, then they are redirected to sign in with the intended destination preserved.
- [ ] Given a non-admin visitor to an admin route, when navigation occurs, then they receive an unauthorized experience without protected content flashing.

**Deliverables**:

- Public, private, and admin layouts
- Guest, authenticated, and admin route guards

**Success Metrics**:

- Feature routes are declared centrally and resolve to the correct layout and access rule.

---

### US-EP1-FE-003: Deliver Shared Responsive and Accessible UI States

**Story ID**: US-EP1-FE-003
**Epic Link**: EPIC-1
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Frontend Engineer,
**I want to** create reusable loading, empty, error, and feedback states using the design system,
**So that** asynchronous pages are clear, accessible, and visually consistent.

**Acceptance Criteria**:

- [ ] Given a pending request, when a page loads, then an accessible loading indicator communicates progress.
- [ ] Given an empty response, when a collection page renders, then it explains the state and offers a relevant next action.
- [ ] Given a recoverable error, when an API request fails, then an actionable message and retry path are displayed.
- [ ] Given keyboard-only navigation, when shared controls are used, then focus is visible and every action is operable.

**Deliverables**:

- Shared feedback-state components
- Responsive and accessibility conventions documented in the design system

**Success Metrics**:

- Customer-facing feature pages do not introduce bespoke loading, empty, or error patterns.
