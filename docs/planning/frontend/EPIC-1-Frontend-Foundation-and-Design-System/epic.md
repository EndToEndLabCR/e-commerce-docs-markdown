# Epic: Frontend Foundation & Design System

**Epic Title**: Frontend Foundation & Design System
**Epic Key**: EPIC-1
**Summary**: Establish the React application foundation, design system, layouts, routing, API integration, and accessible responsive behavior for the storefront.
**Labels**: frontend, foundational, design-system
**Priority**: Must Have
**Components**: Frontend, Design System
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: The React project contains a starter shell, but it needs consistent application conventions before customer-facing features can be delivered reliably.

Objective: Provide a typed, responsive, accessible frontend foundation using React, TypeScript, Vite, Redux Toolkit with RTK Query, Ant Design, React Router, and SCSS modules.

Included scope:
- Environment-aware API client and feature-level RTK Query endpoints
- Shared layouts, route configuration, error states, and route guards
- Design tokens, Ant Design theme configuration, responsive styling, and dark-mode support
- Shared loading, empty, error, and feedback components

Excluded scope:
- Store-specific customer workflows
- Backend API implementation

Dependencies:
- [Frontend README](../../../../../e-commerce-web-react/README.md)
- [Backend Epic 1: Backend Foundation & Infrastructure](../../backend/EPIC-1-Backend-Foundation-and-Infrastructure/epic.md)
- [Non-Functional Requirements](../../../requirements/non-functional-requirements.md)

Measurable success criteria:
- Given any supported viewport, when a public page renders, then it remains usable from 320px through 1440px and wider.
- Given an API request, when it is pending, succeeds, or fails, then the UI presents a consistent loading, success, or recoverable error state.
- Given a protected route, when the visitor lacks the required role, then they are redirected without rendering protected content.
- Given the frontend project, when lint and production build run, then both complete successfully.
