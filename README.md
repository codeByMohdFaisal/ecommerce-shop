# EcommerceShop

A full-stack e-commerce application built to demonstrate practical backend and frontend engineering: authentication, authorization, product catalog, cart, checkout, order/inventory management, reviews, and an admin dashboard with basic analytics.

> **Status:** In active development. This README describes the target scope and will be updated as features land.

## Why this project

This isn't a template clone — it's built to show real decision-making around the parts of e-commerce systems that are easy to get wrong:

- The backend never trusts client-supplied prices; totals are always recomputed server-side from the current product data.
- Inventory updates are designed to prevent overselling under concurrent purchases.
- Reviews are tied to verified purchases, with duplicate-review prevention.
- Consistent, centralized error handling and a predictable API response shape.
- Role-based authorization separating customer and admin capabilities.

## Tech stack

**Frontend:** Next.js, TypeScript, React, Tailwind CSS, Redux Toolkit (where appropriate)

**Backend:** Node.js, Express.js, TypeScript, MongoDB, Mongoose

**Auth:** JWT + HttpOnly cookies, password hashing

**Tooling:** Postman, Git/GitHub

## Features

### Customer

- Register / login / logout, profile management, address book
- Browse, search, filter, sort, and paginate products
- Product detail pages with pricing, stock, and ratings
- Cart with server-verified pricing and stock checks
- Checkout with server-calculated subtotal, discount, shipping, and tax
- Order history, order tracking, and cancellation where allowed
- Product reviews and ratings (purchase-verified)

### Admin

- Role-based admin authentication
- Product and category management (CRUD)
- User management (view, search, block/unblock)
- Order management with status updates
- Review moderation
- Dashboard with basic analytics (revenue, order counts, sales by day/month, top-selling products) via MongoDB aggregation

## API overview

RESTful, resource-based routes:

```
/api/auth
/api/users
/api/products
/api/categories
/api/cart
/api/orders
/api/reviews
/api/admin/analytics
```

Product listing supports query-based search, filtering, sorting, and pagination, e.g.:

```
GET /api/products?search=chair&category=furniture&minPrice=5000&maxPrice=30000&sort=price_asc&page=1&limit=20
```

Standard response shape:

```json
{
  "success": false,
  "message": "Product not found"
}
```

## Architecture

```
backend/
├── src/
│   ├── config/
│   ├── modules/
│   │   ├── auth/
│   │   ├── users/
│   │   ├── products/
│   │   ├── categories/
│   │   ├── cart/
│   │   ├── orders/
│   │   ├── reviews/
│   │   └── analytics/
│   ├── middleware/
│   ├── utils/
│   ├── app.ts
│   └── server.ts
├── .env
└── package.json
```

Modular, feature-based organization rather than a single flat MVC tree — each domain (auth, products, orders, etc.) owns its routes, controller, service, and model.

## Scope

**In scope:** authentication, user management, product catalog, search/filter/sort/pagination, cart, checkout, orders, inventory control, reviews, admin panel, basic analytics.

**Stretch goals (time permitting):** payment gateway integration, image upload, wishlist, coupons, email notifications.

**Deliberately out of scope:** microservices, message queues, complex caching layers, recommendation engines, multi-vendor support, real-time chat, and other infrastructure beyond what a focused single-service e-commerce app needs.

## Getting started

Setup instructions will be added once the initial backend and frontend scaffolding is in place.

## License

TBD
