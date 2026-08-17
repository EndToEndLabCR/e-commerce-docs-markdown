# Epic: Catalog & Product Discovery

**Epic Title**: Catalog & Product Discovery
**Epic Key**: EPIC-3
**Summary**: Enable customers to browse, search, filter, and inspect music T-shirt products before selecting a sellable variant.
**Labels**: frontend, catalog, discovery
**Priority**: Must Have
**Components**: Frontend, Catalog
**Fix Version**: MVP-1

---

**Epic Description:**
Problem Statement: The frontend has no catalog experience, despite the planned backend catalog APIs and product discovery requirements.

Objective: Create responsive catalog, search, filtering, product-detail, and variant-selection experiences powered by the catalog API contract.

Included scope:
- Product-listing and pagination UI
- Search, sorting, categories, and filter controls with URL state
- Product details, media gallery, availability, and variant selection
- API contract integration with loading, empty, and error states

Excluded scope:
- Product reviews, wishlists, and promotions (Phase 1)
- Admin catalog management (Epic 7)

Dependencies:
- [Epic 1: Frontend Foundation & Design System](../EPIC-1-Frontend-Foundation-and-Design-System/epic.md)
- [Backend Epic 4: Product Catalog & Discovery](../../backend/EPIC-4-Product-Catalog-and-Discovery/epic.md)
- [Functional Requirements FR2](../../../requirements/functional-requirements.md)

Measurable success criteria:
- Given a catalog request, when results load, then products display name, band, image, price, and availability.
- Given search, sorting, or filters, when a shopper shares the URL, then the same catalog state can be restored.
- Given a product with variants, when the product page is displayed, then unavailable choices cannot be added to cart.
