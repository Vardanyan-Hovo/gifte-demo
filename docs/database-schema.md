# Database Schema

This document describes a suggested database structure for the Gifte ecommerce platform.

## Entity Relationship Overview

```text
User
  └── Order
        └── OrderItem
              └── Product

Category
  └── Product

Product
  └── ProductImage
```

## Tables / Collections

### users

Stores customer account data.

| Field | Type | Notes |
| --- | --- | --- |
| id | string / uuid | Primary key |
| name | string | Customer full name |
| email | string | Unique email address |
| password_hash | string | Only if using password auth |
| created_at | datetime | Created timestamp |
| updated_at | datetime | Updated timestamp |

### categories

Stores product categories and gift groupings.

| Field | Type | Notes |
| --- | --- | --- |
| id | string / uuid | Primary key |
| name | string | Category name |
| slug | string | URL-friendly identifier |
| description | text | Optional description |
| created_at | datetime | Created timestamp |

### products

Stores product catalog data.

| Field | Type | Notes |
| --- | --- | --- |
| id | string / uuid | Primary key |
| category_id | string / uuid | Linked category |
| name | string | Product name |
| slug | string | URL-friendly identifier |
| description | text | Product description |
| price | decimal | Product price |
| stock | integer | Available quantity |
| rating | decimal | Optional average rating |
| is_featured | boolean | Used for homepage sections |
| created_at | datetime | Created timestamp |
| updated_at | datetime | Updated timestamp |

### product_images

Stores product media references.

| Field | Type | Notes |
| --- | --- | --- |
| id | string / uuid | Primary key |
| product_id | string / uuid | Linked product |
| url | string | Image URL |
| alt | string | Accessible image description |
| sort_order | integer | Display order |

### orders

Stores customer order records.

| Field | Type | Notes |
| --- | --- | --- |
| id | string / uuid | Primary key |
| user_id | string / uuid | Optional linked user |
| customer_name | string | Checkout name |
| customer_email | string | Checkout email |
| subtotal | decimal | Items total |
| shipping | decimal | Shipping cost |
| tax | decimal | Tax amount |
| total | decimal | Final total |
| payment_status | string | pending, paid, failed, refunded |
| shipping_status | string | pending, shipped, delivered |
| created_at | datetime | Created timestamp |

### order_items

Stores individual purchased products.

| Field | Type | Notes |
| --- | --- | --- |
| id | string / uuid | Primary key |
| order_id | string / uuid | Linked order |
| product_id | string / uuid | Linked product |
| product_name | string | Snapshot at purchase time |
| quantity | integer | Purchased quantity |
| unit_price | decimal | Price at purchase time |
| line_total | decimal | quantity * unit_price |

## Notes

- Store purchase snapshots in `order_items` so old orders do not change when products are edited.
- Use unique indexes for `email`, product `slug`, and category `slug`.
- Keep payment provider secrets outside the database and outside the public repository.
