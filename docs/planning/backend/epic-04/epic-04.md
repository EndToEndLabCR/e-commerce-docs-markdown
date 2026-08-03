# Epic 4: Product Catalog & Discovery

> **Index**: [epics.md](../epics.md) · **User Stories**: [user-stories.md](../user-stories.md)

**Problem Statement:** The store needs a browsable catalog, but the backend only provides raw CRUD on bands, products, sizes, and variants, with no search, filtering, categories, images, or referential integrity.

**Objective:** Provide a complete catalog foundation: CRUD for bands, T-shirt designs, sizes, and sellable variants, plus paginated listing, keyword search, filtering, categories, product images, and enforced foreign keys.

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
- [Epic 1: Backend Foundation & Infrastructure](#epic-1-backend-foundation--infrastructure)
- [MVP Database Design](../../../database/v1_mvp_database_design.md)
- [Functional Requirements FR2](../../../requirements/functional-requirements.md)

Acceptance criteria:
- Given a catalog request, when products are listed, then the response uses the shared paginated envelope.
- Given a search term, when the search endpoint is called, then matching products by band or name are returned.
- Given filter criteria, when filtering is applied, then results honor all selected criteria.
- Given a delete on a referenced record, when foreign keys are enforced, then the operation is blocked or handled gracefully.

## User Stories

- [US-MVP-BE-017: Band CRUD](./user_story017.md)
- [US-MVP-BE-018: Product (Design) CRUD](./user_story018.md)
- [US-MVP-BE-019: T-Shirt Size Lookup CRUD](./user_story019.md)
- [US-MVP-BE-020: Product Variant CRUD](./user_story020.md)
- [US-MVP-BE-021: Paginated Product Listing Envelope](./user_story021.md)
- [US-MVP-BE-022: Search Products by Keyword](./user_story022.md)
- [US-MVP-BE-023: Filter Products by Multiple Criteria](./user_story023.md)
- [US-MVP-BE-024: Product Categories](./user_story024.md)
- [US-MVP-BE-025: Product Images](./user_story025.md)
- [US-MVP-BE-026: Foreign-Key Constraints & ORM Relationships](./user_story026.md)
