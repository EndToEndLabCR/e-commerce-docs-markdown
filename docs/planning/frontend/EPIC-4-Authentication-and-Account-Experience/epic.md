# Epic: Authentication & Account Experience

**Epic Title**: Authentication & Account Experience
**Epic Key**: EPIC-4
**Summary**: Give customers secure, understandable account entry, recovery, profile management, and authenticated navigation experiences.
**Labels**: frontend, auth, account
**Priority**: Must Have
**Components**: Frontend, Identity
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: The frontend has no account pages or session state, preventing customers from registering, signing in, managing profiles, and accessing protected shopping journeys.

Objective: Implement typed authentication flows, persisted session state, protected routes, and account profile management against the backend authentication contract.

Included scope:
- Registration, login, logout, email verification, and password-reset flows
- Session hydration, current-user display, and authenticated routing
- Customer profile and default shipping-address management
- Form validation and safe user-facing API errors

Excluded scope:
- Social sign-on and multi-factor authentication
- Admin operational tools (Epic 7)

Dependencies:
- [Epic 1: Frontend Foundation & Design System](../EPIC-1-Frontend-Foundation-and-Design-System/epic.md)
- [Backend Epic 2: User & Account Management](../../backend/EPIC-2-User-and-Account-Management/epic.md)
- [Backend Epic 3: Authentication & Authorization](../../backend/EPIC-3-Authentication-and-Authorization/epic.md)
- [Functional Requirements FR1](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given valid credentials, when a customer signs in, then their session and intended protected destination are restored.
- Given an expired or invalid session, when a protected API call fails with authorization error, then protected state is cleared and the customer is guided to sign in.
- Given profile changes, when the form is submitted successfully, then the visible account state updates without a full reload.
