# Gifte Demo

Gifte Demo is the public showcase repository for **Gifte**, a gift-focused ecommerce platform. This repository is intentionally limited to documentation, architecture, screenshots, and a walkthrough video. It does not contain the private production source code.

## Why This Repo Exists

This repository is designed to show the project clearly without exposing private implementation details.

- It presents the product idea and user experience.
- It explains the system architecture.
- It documents the expected database structure.
- It shares a Loom walkthrough for quick review.
- It keeps secrets, private code, and production logic out of the public repo.

## Recommended Repository Setup

```text
GitHub
  ├── gifte        PRIVATE  -> full real project code
  └── gifte-demo   PUBLIC   -> demo, architecture, docs, screenshots
```

## Loom Walkthrough

Watch the demo video:

<div>
  <a href="https://www.loom.com/share/9f17455eef0549e384515014eff34dd7">
    <p>localhost - 29 June 2026 - Watch Video</p>
  </a>
  <a href="https://www.loom.com/share/9f17455eef0549e384515014eff34dd7">
    <img style="max-width:300px;" src="https://cdn.loom.com/sessions/thumbnails/9f17455eef0549e384515014eff34dd7-380979f6512f01cd-full-play.gif#t=0.1" alt="Gifte ecommerce demo Loom preview">
  </a>
</div>

## Project Overview

Gifte is an ecommerce website for discovering and buying gifts by occasion, recipient, category, and budget. The product is focused on making gift shopping faster and more personal through curated collections, clear product pages, cart management, and checkout flow.

## Core Features

- Gift discovery by occasion, recipient, category, and price.
- Featured product collections on the home page.
- Product listing and filtering.
- Product detail pages with image, description, price, and actions.
- Shopping cart with quantity updates and item removal.
- Checkout flow for customer and order details.
- Responsive UI for desktop and mobile.

## Screenshots

### Main Storefront

![Gifte main storefront](./screenshots/gifte_main.png)

### Admin Dashboard

![Gifte admin dashboard](./screenshots/gitfte_admin.png)

## Tech Stack

| Area | Example Stack |
| --- | --- |
| Frontend | React, Next.js, or Vite |
| Styling | Tailwind CSS, CSS Modules, or plain CSS |
| State Management | React Context, Zustand, Redux Toolkit, or framework state |
| Backend | Node.js, Express, NestJS, or Next.js API routes |
| Database | PostgreSQL, MongoDB, Firebase, or Supabase |
| Payments | Stripe |
| Deployment | Vercel, Netlify, Render, Railway, or similar |

## Architecture

Gifte follows a standard ecommerce architecture with a frontend layer, an application/API layer, and a data layer.

```text
Customer
   |
   v
Browser / Frontend UI
   |
   v
Application / API Layer
   |
   v
Database + Media Storage
```

More details are available in:

- [Architecture Diagram](./docs/architecture.md)
- [Database Schema](./docs/database-schema.md)
- [System Flow](./docs/system-flow.md)

## Folder Structure

```text
gifte-demo/
  README.md
  .env.example
  docs/
    architecture.md
    database-schema.md
    system-flow.md
  screenshots/
    gifte_main.png
    gitfte_admin.png
    README.md
```

## Environment Variables

This public repository includes only `.env.example`. It shows the expected environment variable structure without exposing secrets.

```bash
cp .env.example .env
```

Never commit real API keys, database URLs, payment keys, or private tokens.

## What Is Not Included

- Production source code.
- Private business logic.
- Real database credentials.
- Payment provider secrets.
- Customer data.
- Admin credentials.

## Status

This repository is a public demo and documentation package. The real implementation should stay in the private `gifte` repository.
