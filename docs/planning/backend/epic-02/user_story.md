# Story: User Registration with Password Hashing

**Story Title**: User Registration with Password Hashing
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to create users with bcrypt password hashing
**So that** customer credentials are stored securely.
**Labels**: backend, accounts, identity
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a valid email and password, when a user is created, then the password is stored as a bcrypt hash and never as plaintext.
- Given a duplicate email, when a user is created, then a conflict response is returned and no duplicate row is inserted.
- Given an invalid email or password format, when a user is created, then a validation error is returned.
- Given a new user, when they are persisted, then a role (customer) and active status are set by default.

---

# Story: User Profile Management

**Story Title**: User Profile Management
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to retrieve, update, and delete user profiles
**So that** customers can manage their account data.
**Labels**: backend, accounts, identity
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given an existing user ID, when the profile is fetched, then the user data is returned.
- Given a valid update payload, when the profile is updated, then the changed fields are persisted.
- Given an existing user ID, when the profile is deleted, then the user is removed and a confirmation is returned.
- Given a non-existent user ID, when any profile operation runs, then a 404 response is returned.

---

# Story: List Users Endpoint

**Story Title**: List Users Endpoint
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to list users with pagination
**So that** the account population can be browsed and paged consistently with other features.
**Labels**: backend, accounts, identity
**Priority**: Must Have
**Story Points**: 2

---

**Acceptance Criteria:**

- Given a list request, when users are queried, then a paginated list of users is returned.
- Given `limit` and `offset` parameters, when users are listed, then the result honors them.
- Given an empty dataset, when users are listed, then an empty list is returned without error.
