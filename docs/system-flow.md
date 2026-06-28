# System Flow

This document describes the main user and system flows for Gifte.

## Customer Shopping Flow

```text
Open website
   -> Browse home page collections
   -> Search or filter products
   -> Open product details
   -> Add product to cart
   -> Review cart
   -> Enter checkout details
   -> Submit order
   -> Receive confirmation
```

## Add To Cart Flow

```text
Customer clicks "Add to cart"
   -> Frontend checks selected product and quantity
   -> Cart state is updated
   -> Cart badge and totals refresh
   -> Customer can continue shopping or open cart
```

## Checkout Flow

```text
Customer opens checkout
   -> Frontend validates required fields
   -> API validates cart and product availability
   -> API calculates final totals
   -> Payment provider processes payment
   -> API creates order
   -> Email confirmation is sent
   -> Customer sees success page
```

## Admin Product Flow

```text
Admin signs in
   -> Opens product dashboard
   -> Creates or edits product
   -> Uploads product image
   -> Saves product
   -> Product appears in customer catalog
```

## Error Handling Flow

```text
API or payment error
   -> Return clear error response
   -> Show user-friendly message
   -> Keep cart data available
   -> Allow customer to retry
```

## Public Demo Scope

The public `gifte-demo` repository should show the flow and architecture without exposing private implementation details.

Included:

- Architecture documentation.
- Database schema example.
- System flow explanation.
- Loom walkthrough.
- Optional screenshots.

Excluded:

- Private production code.
- Real credentials.
- Payment keys.
- Customer data.
