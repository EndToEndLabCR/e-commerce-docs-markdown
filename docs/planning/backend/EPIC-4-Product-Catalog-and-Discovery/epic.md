# Epic: Product Catalog & Discovery

**Epic Title**: Product Catalog & Discovery
**Epic Key**: EPIC-4
**Summary**: Deliver complete catalog management and discovery APIs for bands, products, variants, search, filtering, media, and referential integrity.
**Labels**: backend, catalog, discovery
**Priority**: Must Have
**Components**: Backend, Database
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: The store needs a browsable catalog, but the backend only provides raw CRUD on bands, products, sizes, and variants, with no search, filtering, categories, images, or referential integrity.

Objective: Provide a complete catalog foundation: CRUD for bands, T-shirt designs, sizes, and sellable variants, plus paginated listing, keyword search, filtering, categories, product images, and enforced foreign keys.

Included scope:
- Band CRUD
- Product (design) CRUD
- T-shirt size lookup CRUD
- Product variant CRUD (SKU, price, stock)
- Paginated product listing envelope
- Keyword search (band name and product name)
- Filtering (size, color, price range, fit, genre)
- Product categories
- Product images
- Foreign-key constraints and ORM relationships

Excluded scope:
- Advanced full-text search and ranking (Phase 1)
- Product reviews and ratings (Phase 1)
- Wishlist (Phase 1)

Dependencies:
- [Epic 1: Backend Foundation & Infrastructure](../EPIC-1-Backend-Foundation-and-Infrastructure/epic.md)
- [MVP Database Design](../../../database/v1_mvp_database_design.md)
- [Functional Requirements FR2](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given a catalog request, when products are listed, then the response uses the shared paginated envelope.
- Given a search term, when the search endpoint is called, then matching products by band or name are returned.
- Given filter criteria, when filtering is applied, then results honor all selected criteria.
- Given a delete on a referenced record, when foreign keys are enforced, then the operation is blocked or handled gracefully.
