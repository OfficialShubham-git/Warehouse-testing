# Admin Guide

## Product Creation
1. Click Add Product.
2. Enter product name, SKU, category, price, initial quantity, and low-stock threshold.
3. Save.

If initial quantity is greater than zero, the backend creates an initial `IN` movement.

## Product Editing
Admins can edit product metadata. Quantity is not edited directly after creation. Use stock adjustment instead.

## Stock Adjustment
1. Open a product detail page.
2. Click Adjust Stock.
3. Select `IN` or `OUT`.
4. Enter quantity and optional note.
5. Save.

Rules:
- `IN` increases quantity.
- `OUT` decreases quantity.
- `OUT` cannot make quantity negative.
- Every adjustment creates a movement log.

## Product Deletion
Deleting a product removes the product and related movement records in this implementation. For stricter audit requirements, convert deletion to soft delete before production use.

