# E-commerce Catalog API - Postman Guide

This API supports nested categories (subcategories) and product associations.

## Base URL
`http://localhost:3000/api`

---

## 1. Create a Root Category
**POST** `/categories`
- **Body (JSON):**
```json
{
  "name": "Electronics",
  "description": "Gadgets and devices"
}
```
*Note: Save the `_id` from the response to use as `parentId` in the next step.*

---

## 2. Create a Subcategory (Nested Item)
**POST** `/categories`
- **Body (JSON):**
```json
{
  "name": "Laptops",
  "parentId": "REPLACE_WITH_ELECTRONICS_ID"
}
```

---

## 3. Create a Product
**POST** `/products`
- **Body (JSON):**
```json
{
  "name": "MacBook Pro",
  "price": 1999,
  "sku": "mac123",
  "description": "High performance laptop"
}
```
*Note: Save the product `_id` to add it to a category.*

---

## 4. Add Product to Category
**PUT** `/categories/REPLACE_WITH_LAPTOP_ID`
- **Body (JSON):**
```json
{
  "products": ["REPLACE_WITH_PRODUCT_ID"]
}
```

---

## 5. Get Category with Nested Data
**GET** `/categories/REPLACE_WITH_ELECTRONICS_ID`
- This will return the category with its `subcategories` and `products` populated.

---

## Running the Server
1. Navigate to the folder: `cd Exp2.1.3Tannu`
2. Install dependencies: `npm install`
3. Start the server: `node index.js` (or `npm run dev` if permitted)
