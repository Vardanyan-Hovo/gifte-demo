# Architecture

This document explains the high-level architecture of the Gifte ecommerce platform.

## System Diagram

```text
Customer
   |
   v
Frontend Application
   - Home page
   - Product listing
   - Product details
   - Cart
   - Checkout
   |
   v
API / Business Logic
   - Product service
   - Cart service
   - Order service
   - Auth service
   - Payment service
   |
   v
Database
   - Products
   - Categories
   - Users
   - Orders
   - Order items
   |
   v
External Services
   - Payment provider
   - Email provider
   - Image/CDN storage
```

## Frontend Layer

The frontend provides the customer-facing shopping experience. It is responsible for layout, routing, reusable components, product browsing, cart interaction, and checkout screens.

Typical frontend modules:

- `Home`: featured gifts and collections.
- `Products`: category browsing, search, and filtering.
- `ProductDetails`: product media, description, price, and add-to-cart action.
- `Cart`: selected products, quantity updates, and totals.
- `Checkout`: customer details, shipping, payment, and order review.

## API / Business Logic Layer

The API layer connects the UI to the data layer and handles ecommerce rules.

Responsibilities:

- Load product and category data.
- Validate cart items and stock availability.
- Calculate subtotal, tax, shipping, discounts, and final total.
- Create customer orders.
- Integrate with payment and email providers.
- Protect private operations such as admin actions.

## Data Layer

The data layer stores product, customer, and order information. In production, product images should be served from a media storage service or CDN.

Core data groups:

- Product catalog.
- Categories and collections.
- Customers and addresses.
- Cart and order records.
- Payment and shipping statuses.

## Security Notes

- Keep production source code in the private `gifte` repo.
- Keep this repo limited to demo assets and documentation.
- Never commit real `.env` files.
- Use `.env.example` only for public documentation.
- Restrict admin APIs and payment operations on the backend.
