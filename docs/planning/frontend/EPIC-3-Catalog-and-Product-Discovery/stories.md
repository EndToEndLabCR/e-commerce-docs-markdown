# Stories for Epic: Catalog & Product Discovery

## Frontend Engineer

### US-EP3-FE-001: Display a Paginated Product Catalog

**Story ID**: US-EP3-FE-001
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Store Visitor,
**I want to** browse a paginated grid of products,
**So that** I can compare available band T-shirts and open a product for more detail.

**Acceptance Criteria**:

- [ ] Given a successful catalog response, when the catalog page renders, then each card shows image, product name, band, starting price, and availability.
- [ ] Given pagination metadata, when a shopper changes page, then the requested page is fetched and the page state is reflected in the URL.
- [ ] Given no matching products, when the catalog response is empty, then an empty state offers a way to clear discovery criteria.

**Deliverables**:

- Catalog route, typed product API endpoint, and reusable product card
- Pagination control integrated with URL state

**Success Metrics**:

- Catalog pagination never loses the shopper's selected discovery criteria.

---

### US-EP3-FE-002: Provide Search, Sort, Category, and Filtering Controls

**Story ID**: US-EP3-FE-002
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Store Visitor,
**I want to** search and filter the catalog,
**So that** I can quickly find designs matching my music and apparel preferences.

**Acceptance Criteria**:

- [ ] Given a search term of at least two characters, when I pause typing, then a debounced request queries the catalog without issuing redundant calls.
- [ ] Given selected size, color, price, fit, or category criteria, when filters are applied, then the catalog uses all selected criteria.
- [ ] Given an updated search, sort, or filter, when the URL is copied and reopened, then the same state is restored.
- [ ] Given a mobile viewport, when filters are opened, then they are usable in an accessible drawer or equivalent responsive control.

**Deliverables**:

- Search, sort, category, and multi-filter controls
- URL query-state serialization and restoration

**Success Metrics**:

- A shared catalog URL restores the visible search, sort, filters, and page.

---

### US-EP3-FE-003: Build Product Details and Variant Selection

**Story ID**: US-EP3-FE-003
**Epic Link**: EPIC-3
**Priority**: Must Have
**Effort Estimate**: 5

**As a** Store Visitor,
**I want to** inspect a product and choose an available variant,
**So that** I can make an informed purchase decision.

**Acceptance Criteria**:

- [ ] Given a product identifier, when the detail page loads, then it displays the product description, band, images, available sizes and colors, price, and stock status.
- [ ] Given a variant choice, when it is out of stock, then it is visually identified and cannot be selected for purchase.
- [ ] Given an unavailable or missing product, when the API returns an error, then the page shows a clear not-found or recoverable error state.
- [ ] Given a selected in-stock variant, when the shopper activates the cart action, then the selected variant and quantity are supplied to the cart workflow.

**Deliverables**:

- Product-detail route, media gallery, variant selector, and cart handoff

**Success Metrics**:

- The cart workflow never receives an unselected or out-of-stock variant from the product page.
