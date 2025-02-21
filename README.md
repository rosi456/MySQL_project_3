# MySQL_project_3
BEGINNER FRIENDLY PROJECT 
# Makeup Store Database

This project is a simple beginner-friendly MySQL database for a makeup store. It includes tables for products, customers, orders, and order items.

## Database Schema

The database schema includes the following tables:

1. **Products**: Contains information about makeup products.
2. **Customers**: Contains information about customers.
3. **Orders**: Contains information about orders placed by customers.
4. **Order Items**: Contains information about the items in each order.

## Table Definitions

### Products Table

| Column       | Data Type      | Description                          |
|--------------|----------------|--------------------------------------|
| product_id   | INT            | Primary key, auto-incremented        |
| product_name | VARCHAR(100)   | Name of the product                  |
| brand        | VARCHAR(50)    | Brand of the product                 |
| price        | DECIMAL(10, 2) | Price of the product                 |
| stock        | INT            | Stock quantity                       |

### Customers Table

| Column       | Data Type     | Description                          |
|--------------|---------------|--------------------------------------|
| customer_id  | INT           | Primary key, auto-incremented        |
| first_name   | VARCHAR(50)   | First name of the customer           |
| last_name    | VARCHAR(50)   | Last name of the customer            |
| email        | VARCHAR(100)  | Email of the customer, unique        |
| phone        | VARCHAR(15)   | Phone number of the customer         |

### Orders Table

| Column       | Data Type      | Description                          |
|--------------|----------------|--------------------------------------|
| order_id     | INT            | Primary key, auto-incremented        |
| customer_id  | INT            | Foreign key referencing customers    |
| order_date   | DATE           | Date the order was placed            |
| total_amount | DECIMAL(10, 2) | Total amount of the order            |

### Order Items Table

| Column         | Data Type      | Description                          |
|----------------|----------------|--------------------------------------|
| order_item_id  | INT            | Primary key, auto-incremented        |
| order_id       | INT            | Foreign key referencing orders       |
| product_id     | INT            | Foreign key referencing products     |
| quantity       | INT            | Quantity of the product              |
| price          | DECIMAL(10, 2) | Price of the product at order time   |

## Sample Data

The following sample data is included in the database:

### Products Table

| product_name | brand   | price | stock |
|--------------|---------|-------|-------|
| Lipstick     | Brand A | 9.99  | 100   |
| Foundation   | Brand B | 19.99 | 50    |
| Mascara      | Brand C | 12.99 | 200   |

### Customers Table

| first_name | last_name | email                 | phone       |
|------------|------------|-----------------------|-------------|
| Jane       | Doe        | jane.doe@example.com  | 123-456-7890|
| John       | Smith      | john.smith@example.com| 555-555-5555|

### Orders Table

| customer_id | order_date | total_amount |
|-------------|------------|--------------|
| 1           | 2025-02-20 | 29.97        |
| 2           | 2025-02-21 | 19.99        |

### Order Items Table

| order_id | product_id | quantity | price |
|----------|------------|----------|-------|
| 1        | 1          | 1        | 9.99  |
| 1        | 2          | 1        | 19.99 |
| 2        | 3          | 1        | 19.99 |

## How to Use

1. Create the database and tables using the provided SQL script.
2. Insert the sample data into the tables.
3. Use the provided queries to retrieve information from the database.

## Queries

### Select All Products
```sql
SELECT * FROM products;
```

### Select All Customers
```sql
SELECT * FROM customers;
```

### Select All Orders
```sql
SELECT * FROM orders;
```

### Select All Order Items
```sql
SELECT * FROM order_items;
```

### Get Orders with Customer Details
```sql
SELECT 
    o.order_id,
    o.order_date,
    o.total_amount,
    c.first_name,
    c.last_name,
    c.email
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```

### Get Order Details with Product Information
```sql
SELECT 
    oi.order_item_id,
    o.order_id,
    p.product_name,
    oi.quantity,
    oi.price
FROM order_items oi
JOIN orders o ON oi.order_id = o.order_id
JOIN products p ON oi.product_id = p.product_id;
```
