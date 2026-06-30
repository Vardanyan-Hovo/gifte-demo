# Architecture

This document explains the high-level architecture of the Gifte ecommerce platform.

Gifte is built as a Dockerized full-stack system using Next.js, TypeScript, Node.js, Prisma ORM, PostgreSQL, BullMQ, Redis, AI integration, Docker Compose, and Nginx.

## System Diagram

```text
Customer
   |
   v
Nginx Reverse Proxy
   - Routes public traffic
   - Separates frontend and API access
   - Can handle SSL in production
   |
   v
Next.js Frontend
   - Home page
   - Product listing
   - Product details
   - Cart and checkout
   - Admin dashboard
   |
   v
Node.js TypeScript API
   - Product service
   - Cart service
   - Order service
   - Admin service
   - AI integration service
   |
   +--> Prisma ORM
   |       |
   |       v
   |   PostgreSQL
   |   - Products
   |   - Categories
   |   - Users
   |   - Orders
   |   - Order items
   |
   +--> BullMQ Workers
           |
           v
        Redis
        - Background jobs
        - Queue state
        - Async processing
```

## Frontend Layer

The frontend is built with Next.js, React, TypeScript, and Tailwind CSS. It provides the customer-facing shopping experience and the admin dashboard.

Typical frontend modules:

- `Home`: featured gifts and collections.
- `Products`: category browsing, search, and filtering.
- `ProductDetails`: product media, description, price, and add-to-cart action.
- `Cart`: selected products, quantity updates, and totals.
- `Checkout`: customer details, shipping, payment, and order review.
- `Admin`: product, order, and content management views.

## Backend / API Layer

The backend is built with Node.js and TypeScript. It connects the frontend to the database, queue system, AI services, and ecommerce business logic.

Responsibilities:

- Load product and category data.
- Validate cart items and stock availability.
- Calculate subtotal, tax, shipping, discounts, and final total.
- Create customer orders.
- Integrate with AI-powered ecommerce features.
- Push background tasks into BullMQ queues.
- Protect private operations such as admin actions.

## Database Layer

Prisma ORM is used to model and access PostgreSQL data. The database stores product, customer, and order information. In production, product images can be served from a media storage service or CDN.

Core data groups:

- Product catalog.
- Categories and collections.
- Customers and addresses.
- Cart and order records.
- Payment and shipping statuses.

## Queue Layer

BullMQ and Redis are used for background jobs and async work.

Example queue jobs:

- AI product description generation.
- Email notifications.
- Order processing tasks.
- Admin import/export jobs.
- Scheduled cleanup or sync tasks.

## Docker And Proxy Layer

Docker and Docker Compose are used to run the application services consistently across local and server environments.

Typical services:

- `web`: Next.js frontend.
- `api`: Node.js TypeScript backend.
- `worker`: BullMQ background worker.
- `postgres`: PostgreSQL database.
- `redis`: Redis queue broker.
- `nginx`: Reverse proxy.

## Security Notes

- Keep production source code in the private `gifte` repo.
- Keep this repo limited to demo assets and documentation.
- Never commit real `.env` files.
- Use `.env.example` only for public documentation.
- Restrict admin APIs and payment operations on the backend.
