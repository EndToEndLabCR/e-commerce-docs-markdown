# Stories for Epic: Product Catalog & Discovery

## Backend Engineer

### US-EP4-BE-001: Band CRUD

**Story ID**: US-EP4-BE-001
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete bands,
**So that** the catalog can group products by artist.

**Acceptance Criteria**:

- [ ] Given a valid band payload, when a band is created, then it is persisted with a unique name.
- [ ] Given a duplicate band name, when a band is created, then a conflict response is returned.
- [ ] Given an existing band, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a list request, when bands are listed, then a paginated list is returned.

**Deliverables**:

- Full CRUD endpoints for bands
- Unique-name constraint enforcement

**Success Metrics**:

- Band name collisions are rejected with a conflict response.

---

### US-EP4-BE-002: Product (Design) CRUD

**Story ID**: US-EP4-BE-002
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete products,
**So that** the catalog can represent T-shirt designs independent of size, price, and stock.

**Acceptance Criteria**:

- [ ] Given a valid product payload, when a product is created, then it is persisted with a band reference, name, description, and fit.
- [ ] Given an existing product, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a list request, when products are listed, then a paginated list is returned.
- [ ] Given a product payload with price or stock fields, when it is created, then those fields are rejected since they belong to variants.

**Deliverables**:

- Full CRUD endpoints for products
- Validation rejecting variant-only fields on product payloads

**Success Metrics**:

- Products never carry price or stock fields directly.

---

### US-EP4-BE-003: T-Shirt Size Lookup CRUD

**Story ID**: US-EP4-BE-003
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** manage the standardized t-shirt size lookup table,
**So that** variants can reference a shared, non-duplicated size set.

**Acceptance Criteria**:

- [ ] Given a valid size payload, when a size is created, then it is persisted with a unique size value.
- [ ] Given a duplicate size, when a size is created, then a conflict response is returned.
- [ ] Given an existing size, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a list request, when sizes are listed, then all supported sizes are returned.

**Deliverables**:

- Full CRUD endpoints for the size lookup table

**Success Metrics**:

- Size values remain unique across the catalog.

---

### US-EP4-BE-004: Product Variant CRUD

**Story ID**: US-EP4-BE-004
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** create, list, get, update, and delete product variants,
**So that** sellable SKUs with size, price, and stock are managed correctly.

**Acceptance Criteria**:

- [ ] Given a valid variant payload, when a variant is created, then it is persisted with a unique SKU, product reference, size reference, price, and stock.
- [ ] Given a duplicate SKU, when a variant is created, then a conflict response is returned.
- [ ] Given an existing variant, when it is fetched, updated, or deleted, then the operation succeeds or returns a clear 404.
- [ ] Given a variant, when it is validated, then the size reference points to an existing size.

**Deliverables**:

- Full CRUD endpoints for product variants
- SKU uniqueness and size-reference validation

**Success Metrics**:

- Every variant references a valid size and unique SKU.

---

### US-EP4-BE-005: Paginated Product Listing Envelope

**Story ID**: US-EP4-BE-005
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** return product listings in a shared paginated envelope,
**So that** the frontend can render paging consistently across the catalog.

**Acceptance Criteria**:

- [ ] Given a list request, when products are returned, then the response uses the shared pagination envelope with items, total, limit, and offset.
- [ ] Given `limit` and `offset` parameters, when products are listed, then the result honors them.
- [ ] Given an empty catalog, when products are listed, then an empty items list is returned without error.

**Deliverables**:

- Shared pagination envelope used across product listing endpoints

**Success Metrics**:

- All catalog listing endpoints share the same envelope shape.

---

### US-EP4-BE-006: Search Products by Keyword

**Story ID**: US-EP4-BE-006
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** search products by keyword,
**So that** customers can find designs by band name or product name.

**Acceptance Criteria**:

- [ ] Given a search term, when the search endpoint is called, then products matching the band or product name are returned.
- [ ] Given an empty or whitespace term, when search is called, then a validation error is returned or all results are listed.
- [ ] Given no matches, when search is called, then an empty result set is returned.
- [ ] Given special characters in the term, when search is called, then it is handled safely without SQL errors.

**Deliverables**:

- Keyword search endpoint across band and product names
- Input sanitization for search terms

**Success Metrics**:

- Search terms with special characters never cause query errors.

---

### US-EP4-BE-007: Filter Products by Multiple Criteria

**Story ID**: US-EP4-BE-007
**Epic Link**: EPIC-4
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** filter products by size, color, price range, fit, and genre,
**So that** customers can narrow the catalog to what they want.

**Acceptance Criteria**:

- [ ] Given filter parameters, when products are queried, then results honor every supplied criterion.
- [ ] Given a price range, when filtering, then only variants within the range are returned.
- [ ] Given a size filter, when filtering, then only products with a matching variant are returned.
- [ ] Given conflicting filters with no matches, when queried, then an empty result set is returned.

**Deliverables**:

- Combined filtering support across size, color, price, fit, and genre

**Success Metrics**:

- Combined filters return only results matching every criterion.

---

### US-EP4-BE-008: Product Categories

**Story ID**: US-EP4-BE-008
**Epic Link**: EPIC-4
**Priority**: Should Have
**Effort Estimate**: 5

**As a** Backend Engineer,
**I want to** assign products to categories,
**So that** customers can browse by music genre category.

**Acceptance Criteria**:

- [ ] Given a category model, when it is defined, then products can be assigned to one or more categories.
- [ ] Given a category filter, when products are queried, then only products in that category are returned.
- [ ] Given a product update, when categories change, then the assignment is persisted correctly.
- [ ] Given a deleted category, when products reference it, then the delete is handled gracefully.

**Deliverables**:

- Category model and product-category assignment
- Category-based filtering on catalog endpoints

**Success Metrics**:

- Category deletions never leave orphaned product references.

---

### US-EP4-BE-009: Product Images

**Story ID**: US-EP4-BE-009
**Epic Link**: EPIC-4
**Priority**: Could Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** store product image references,
**So that** product detail pages can display design images.

**Acceptance Criteria**:

- [ ] Given an image URL, when a product is created or updated, then the image reference is persisted.
- [ ] Given a product response, when it is returned, then image references are included.
- [ ] Given a missing image, when a product is returned, then the response degrades gracefully without error.

**Deliverables**:

- Image reference field on product records
- Graceful handling of missing image data

**Success Metrics**:

- Missing product images never cause a request failure.

---

### US-EP4-BE-010: Foreign-Key Constraints and ORM Relationships

**Story ID**: US-EP4-BE-010
**Epic Link**: EPIC-4
**Priority**: Must Have
**Effort Estimate**: 3

**As a** Backend Engineer,
**I want to** enforce foreign keys and ORM relationships between catalog tables,
**So that** referential integrity is guaranteed at the database level.

**Acceptance Criteria**:

- [ ] Given the schema, when it is inspected, then foreign keys exist between products-bands, variants-products, and variants-sizes.
- [ ] Given a delete on a parent record with children, when the delete is attempted, then it is blocked by the constraint or handled gracefully.
- [ ] Given ORM models, when relationships are defined, then related data can be loaded via the ORM.
- [ ] Given a migration, when it is applied, then the constraints are created and the chain upgrades cleanly.

**Deliverables**:

- Foreign-key constraints across catalog tables
- ORM relationship definitions and corresponding Alembic migration

**Success Metrics**:

- No orphaned catalog rows can be created after the constraints are applied.
