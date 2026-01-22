# Music Band T-Shirt E-Commerce – MVP Database Design

This document describes the **MVP database schema** for the Music Band T-Shirt E-Commerce backend.
The design focuses on supporting the full purchase flow while remaining simple, scalable, and correct from a commerce perspective.

---

## Design Goals

- Enable a complete e-commerce flow (browse → cart → checkout → payment)
- Keep schema minimal and MVP-friendly
- Correctly model apparel inventory (size/color per SKU)
- Preserve clean upgrade paths for future features

---

## Core Modeling Principle

- **Products** represent the *design / concept*
- **Product Variants** represent the *actual sellable units* (size + color)

> Any attribute that affects **stock, price, or checkout** belongs to `product_variants`, not `products`.

---

## Tables Overview

## Users

### `users`
- id (UUID, PK)
- email (unique)
- password_hash
- role (`customer`, `admin`)
- is_active
- created_at

---

## Catalog

### `bands`
- id (UUID, PK)
- name (unique)
- created_at

### `genres`
- id (UUID, PK)
- name (unique)
- created_at

### `products`
Represents a T-shirt **design**, not a sellable unit.

- id (UUID, PK)
- name
- band_id (FK → bands.id)
- genre_id (FK → genres.id)
- base_price
- is_active
- created_at

**Important**
- No size
- No color
- No stock
- No SKU

---

### `product_variants`
Represents **sellable SKUs** (size + color).

- id (UUID, PK)
- product_id (FK → products.id)
- size (e.g. S, M, L, XL)
- color
- sku (unique)
- stock_quantity
- price_override (nullable)

---

## Cart

### `carts`
- id (UUID, PK)
- user_id (nullable, FK → users.id)
- session_id (nullable)
- created_at
- updated_at

### `cart_items`
- id (UUID, PK)
- cart_id (FK → carts.id)
- product_variant_id (FK → product_variants.id)
- quantity
- unit_price

---

## Orders

### `orders`
- id (UUID, PK)
- user_id (nullable, FK → users.id)
- status (`pending`, `paid`, `cancelled`)
- total_amount
- currency
- shipping_address (JSON / TEXT snapshot)
- billing_address (JSON / TEXT snapshot)
- created_at

### `order_items`
Snapshot of purchased variants.

- id (UUID, PK)
- order_id (FK → orders.id)
- product_variant_id (FK → product_variants.id)
- product_name
- size
- color
- unit_price
- quantity

---

## Payments

### `payments`
- id (UUID, PK)
- order_id (FK → orders.id)
- provider (`stripe`)
- provider_payment_id
- amount
- currency
- status (`pending`, `succeeded`, `failed`)
- created_at

---

## Entity Relationship Diagram (Mermaid)

```mermaid
erDiagram

    USERS {
        UUID id PK
        string email
        string password_hash
        string role
        boolean is_active
        datetime created_at
    }

    BANDS {
        UUID id PK
        string name
        datetime created_at
    }

    GENRES {
        UUID id PK
        string name
        datetime created_at
    }

    PRODUCTS {
        UUID id PK
        string name
        UUID band_id FK
        UUID genre_id FK
        decimal base_price
        boolean is_active
        datetime created_at
    }

    PRODUCT_VARIANTS {
        UUID id PK
        UUID product_id FK
        string size
        string color
        string sku
        int stock_quantity
        decimal price_override
    }

    CARTS {
        UUID id PK
        UUID user_id FK
        string session_id
        datetime created_at
        datetime updated_at
    }

    CART_ITEMS {
        UUID id PK
        UUID cart_id FK
        UUID product_variant_id FK
        int quantity
        decimal unit_price
    }

    ORDERS {
        UUID id PK
        UUID user_id FK
        string status
        decimal total_amount
        string currency
        json shipping_address
        json billing_address
        datetime created_at
    }

    ORDER_ITEMS {
        UUID id PK
        UUID order_id FK
        UUID product_variant_id FK
        string product_name
        string size
        string color
        decimal unit_price
        int quantity
    }

    PAYMENTS {
        UUID id PK
        UUID order_id FK
        string provider
        string provider_payment_id
        decimal amount
        string currency
        string status
        datetime created_at
    }

    USERS ||--o{ CARTS : owns
    USERS ||--o{ ORDERS : places

    BANDS ||--o{ PRODUCTS : has
    GENRES ||--o{ PRODUCTS : categorizes

    PRODUCTS ||--o{ PRODUCT_VARIANTS : has

    CARTS ||--o{ CART_ITEMS : contains
    PRODUCT_VARIANTS ||--o{ CART_ITEMS : added_as

    ORDERS ||--o{ ORDER_ITEMS : includes
    PRODUCT_VARIANTS ||--o{ ORDER_ITEMS : purchased_as

    ORDERS ||--|| PAYMENTS : paid_by
```

---

## Notes

- Size and color exist **only** in `product_variants`
- Orders store size/color as immutable snapshots
- Schema is optimized for MVP correctness, not shortcuts

---

**Status:** Approved for MVP implementation
