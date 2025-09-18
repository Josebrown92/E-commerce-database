# E-commerce Store Database (MySQL)

## 📌 Overview
This project is a **relational database management system** (RDBMS) for an **E-commerce Store**.  
It is designed and implemented in **MySQL** and demonstrates proper database design principles:

- Normalized schema
- Primary & foreign keys
- One-to-One, One-to-Many, and Many-to-Many relationships
- Referential integrity constraints

---

## 🏗️ Database Schema

### Entities & Relationships
- **Customers**  
  Stores user information.  
  - One customer can have many addresses.  
  - One customer can make many orders.

- **Addresses**  
  Stores shipping/billing addresses linked to customers.  

- **Categories**  
  Hierarchical product categories.  
  - Self-referencing parent-child relationship.  

- **Products**  
  Product catalog with SKU, price, and description.  

- **Product Categories**  
  Bridge table to implement a Many-to-Many between `products` and `categories`.  

- **Inventory**  
  One-to-One relationship with `products` to track stock levels.  

- **Orders**  
  Order header details (who placed the order, total amount, date).  

- **Order Items**  
  Line items for each order.  
  Implements Many-to-Many between `orders` and `products`.  

---

## 🗂️ Tables & Keys

| Table              | Primary Key          | Foreign Keys |
|--------------------|----------------------|--------------|
| `customers`        | `customer_id`        | - |
| `addresses`        | `address_id`         | `customer_id → customers(customer_id)` |
| `categories`       | `category_id`        | `parent_id → categories(category_id)` |
| `products`         | `product_id`         | - |
| `product_categories` | `(product_id, category_id)` | `product_id → products(product_id)`<br>`category_id → categories(category_id)` |
| `inventory`        | `product_id`         | `product_id → products(product_id)` |
| `orders`           | `order_id`           | `customer_id → customers(customer_id)` |
| `order_items`      | `order_item_id`      | `order_id → orders(order_id)`<br>`product_id → products(product_id)` |

---

## ⚙️ How to Run

1. Save the SQL file as `ecommerce.sql`.
2. Open a MySQL client or terminal.
3. Run the script:


   ```bash
   mysql -u root -p < ecommerce.sql
