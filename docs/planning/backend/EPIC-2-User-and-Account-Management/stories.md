# Stories for Epic: User & Account Management

## Backend Engineer

### US-EP2-BE-001: User Registration with Password Hashing

**Story ID**: US-EP2-BE-001
**Epic Link**: EPIC-2
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create users with bcrypt password hashing,
**So that** customer credentials are stored securely.

**Acceptance Criteria**:

- [ ] Given a valid email and password, when a user is created, then the password is stored as a bcrypt hash and never as plaintext.
- [ ] Given a duplicate email, when a user is created, then a conflict response is returned and no duplicate row is inserted.
- [ ] Given an invalid email or password format, when a user is created, then a validation error is returned.
- [ ] Given a new user, when they are persisted, then a role (customer) and active status are set by default.

**Deliverables**:

- User registration endpoint with bcrypt password hashing
- Validation rules for email and password format

**Success Metrics**:

- No plaintext passwords are ever persisted.
- Duplicate registrations are rejected without creating orphaned rows.

---

### US-EP2-BE-002: User Profile Management

**Story ID**: US-EP2-BE-002
**Epic Link**: EPIC-2
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** retrieve, update, and delete user profiles,
**So that** customers can manage their account data.

**Acceptance Criteria**:

- [ ] Given an existing user ID, when the profile is fetched, then the user data is returned.
- [ ] Given a valid update payload, when the profile is updated, then the changed fields are persisted.
- [ ] Given an existing user ID, when the profile is deleted, then the user is removed and a confirmation is returned.
- [ ] Given a non-existent user ID, when any profile operation runs, then a 404 response is returned.

**Deliverables**:

- Profile retrieval, update, and delete endpoints
- Consistent 404 handling for missing users

**Success Metrics**:

- Profile updates persist only the submitted fields.
- Deleted or missing users consistently return a 404 response.

---

### US-EP2-BE-003: List Users Endpoint

**Story ID**: US-EP2-BE-003
**Epic Link**: EPIC-2
**Priority**: Must Have
**Effort Estimate**: 2

**As a** Backend Engineer,
**I want to** list users with pagination,
**So that** the account population can be browsed and paged consistently with other features.

**Acceptance Criteria**:

- [ ] Given a list request, when users are queried, then a paginated list of users is returned.
- [ ] Given `limit` and `offset` parameters, when users are listed, then the result honors them.
- [ ] Given an empty dataset, when users are listed, then an empty list is returned without error.

**Deliverables**:

- Paginated list users endpoint

**Success Metrics**:

- User listings honor pagination parameters consistently with other catalog endpoints.
