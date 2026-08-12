# Story: Band CRUD

**Story Title**: Band CRUD
**Story Key**: STORY-1
**As a** Backend Engineer
**I want** to create, list, get, update, and delete bands
**So that** the catalog can group products by artist.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a valid band payload, when a band is created, then it is persisted with a unique name.
- Given a duplicate band name, when a band is created, then a conflict response is returned.
- Given an existing band, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- Given a list request, when bands are listed, then a paginated list is returned.

---

# Story: Product (Design) CRUD

**Story Title**: Product (Design) CRUD
**Story Key**: STORY-2
**As a** Backend Engineer
**I want** to create, list, get, update, and delete products
**So that** the catalog can represent T-shirt designs independent of size, price, and stock.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a valid product payload, when a product is created, then it is persisted with a band reference, name, description, and fit.
- Given an existing product, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- Given a list request, when products are listed, then a paginated list is returned.
- Given a product payload with price or stock fields, when it is created, then those fields are rejected since they belong to variants.

---

# Story: T-Shirt Size Lookup CRUD

**Story Title**: T-Shirt Size Lookup CRUD
**Story Key**: STORY-3
**As a** Backend Engineer
**I want** to manage the standardized t-shirt size lookup table
**So that** variants can reference a shared, non-duplicated size set.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given a valid size payload, when a size is created, then it is persisted with a unique size value.
- Given a duplicate size, when a size is created, then a conflict response is returned.
- Given an existing size, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- Given a list request, when sizes are listed, then all supported sizes are returned.

---

# Story: Product Variant CRUD

**Story Title**: Product Variant CRUD
**Story Key**: STORY-4
**As a** Backend Engineer
**I want** to create, list, get, update, and delete product variants
**So that** sellable SKUs with size, price, and stock are managed correctly.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a valid variant payload, when a variant is created, then it is persisted with a unique SKU, product reference, size reference, price, and stock.
- Given a duplicate SKU, when a variant is created, then a conflict response is returned.
- Given an existing variant, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- Given a variant, when it is validated, then the size reference points to an existing size.

---

# Story: Paginated Product Listing Envelope

**Story Title**: Paginated Product Listing Envelope
**Story Key**: STORY-5
**As a** Backend Engineer
**I want** to return product listings in a shared paginated envelope
**So that** the frontend can render paging consistently across the catalog.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given a list request, when products are returned, then the response uses the shared pagination envelope with items, total, limit, and offset.
- Given `limit` and `offset` parameters, when products are listed, then the result honors them.
- Given an empty catalog, when products are listed, then an empty items list is returned without error.

---

# Story: Search Products by Keyword

**Story Title**: Search Products by Keyword
**Story Key**: STORY-6
**As a** Backend Engineer
**I want** to search products by keyword
**So that** customers can find designs by band name or product name.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a search term, when the search endpoint is called, then products matching the band or product name are returned.
- Given an empty or whitespace term, when search is called, then a validation error is returned or all results are listed.
- Given no matches, when search is called, then an empty result set is returned.
- Given special characters in the term, when search is called, then it is handled safely without SQL errors.

---

# Story: Filter Products by Multiple Criteria

**Story Title**: Filter Products by Multiple Criteria
**Story Key**: STORY-7
**As a** Backend Engineer
**I want** to filter products by size, color, price range, fit, and genre
**So that** customers can narrow the catalog to what they want.
**Labels**: backend, catalog, discovery
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given filter parameters, when products are queried, then results honor every supplied criterion.
- Given a price range, when filtering, then only variants within the range are returned.
- Given a size filter, when filtering, then only products with a matching variant are returned.
- Given conflicting filters with no matches, when queried, then an empty result set is returned.

---

# Story: Product Categories

**Story Title**: Product Categories
**Story Key**: STORY-8
**As a** Backend Engineer
**I want** to assign products to categories
**So that** customers can browse by music genre category.
**Labels**: backend, catalog, discovery
**Priority**: Should Have
**Story Points**: 5

---

**Acceptance Criteria:**

- Given a category model, when it is defined, then products can be assigned to one or more categories.
- Given a category filter, when products are queried, then only products in that category are returned.
- Given a product update, when categories change, then the assignment is persisted correctly.
- Given a deleted category, when products reference it, then the delete is handled gracefully.

---

# Story: Product Images

**Story Title**: Product Images
**Story Key**: STORY-9
**As a** Backend Engineer
**I want** to store product image references
**So that** product detail pages can display design images.
**Labels**: backend, catalog, discovery
**Priority**: Could Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given an image URL, when a product is created or updated, then the image reference is persisted.
- Given a product response, when it is returned, then image references are included.
- Given a missing image, when a product is returned, then the response degrades gracefully without error.

---

# Story: Foreign-Key Constraints & ORM Relationships

**Story Title**: Foreign-Key Constraints & ORM Relationships
**Story Key**: STORY-10
**As a** Backend Engineer
**I want** to enforce foreign keys and ORM relationships between catalog tables
**So that** referential integrity is guaranteed at the database level.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Story Points**: 3

---

**Acceptance Criteria:**

- Given the schema, when it is inspected, then foreign keys exist between products-bands, variants-products, and variants-sizes.
- Given a delete on a parent record with children, when the delete is attempted, then it is blocked by the constraint or handled gracefully.
- Given ORM models, when relationships are defined, then related data can be loaded via the ORM.
- Given a migration, when it is applied, then the constraints are created and the chain upgrades cleanly.
