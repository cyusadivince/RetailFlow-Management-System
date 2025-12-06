## 📦 RetailFlow Backend System – Procedures & Functions Documentation

This document describes all stored **procedures**, **functions**, and **package routines** used in the RetailFlow Backend System, including their parameters and purpose.

---

## 🔹 Package Name: `ECOMMERCE_PKG`

### 1. `customer_exists`

**Type:** Function
**Return Type:** `BOOLEAN`
**Description:** Checks if a customer exists in the database.

**Parameters:**

| Name          | Mode | Type   | Description                    |
| ------------- | ---- | ------ | ------------------------------ |
| p_customer_id | IN   | NUMBER | ID of the customer to validate |

---

### 2. `product_exists`

**Type:** Function
**Return Type:** `BOOLEAN`
**Description:** Checks if a product exists in the database.

| Name         | Mode | Type   | Description                   |
| ------------ | ---- | ------ | ----------------------------- |
| p_product_id | IN   | NUMBER | ID of the product to validate |

---

### 3. `update_product_price`

**Type:** Procedure
**Description:** Updates the price of a specific product. Validates product existence before update.

| Name         | Mode | Type   | Description           |
| ------------ | ---- | ------ | --------------------- |
| p_product_id | IN   | NUMBER | Product to be updated |
| p_new_price  | IN   | NUMBER | New product price     |

**Exceptions:**

* `ex_invalid_product` – Product not found

---

### 4. `bulk_increase_price`

**Type:** Procedure
**Description:** Increases prices of all products by a given percentage using BULK COLLECT and FORALL.

| Name      | Mode | Type   | Description                   |
| --------- | ---- | ------ | ----------------------------- |
| p_percent | IN   | NUMBER | Percentage to increase prices |

---

### 5. `get_total_spent`

**Type:** Function
**Return Type:** `NUMBER`
**Description:** Calculates total amount spent by a customer.

| Name          | Mode | Type   | Description |
| ------------- | ---- | ------ | ----------- |
| p_customer_id | IN   | NUMBER | Customer ID |

---

### 6. `get_pending_orders`

**Type:** Function
**Return Type:** `SYS_REFCURSOR`
**Description:** Returns all orders with status **Pending**.

---

### 7. `customer_rank`

**Type:** Function
**Return Type:** `SYS_REFCURSOR`
**Description:** Ranks customers based on total order amount.


---

## 🔹 Standalone Functions

### 8. `check_stock_status`

**Type:** Function
**Return Type:** `VARCHAR2`
**Description:** Returns the stock status of a product:

* Out of Stock
* Low Stock (1–5)
* In Stock

| Name         | Mode | Type   | Description |
| ------------ | ---- | ------ | ----------- |
| p_product_id | IN   | NUMBER | Product ID  |

---

### 9. `get_total_sales_by_date`

**Type:** Function
**Return Type:** `NUMBER`
**Description:** Returns total completed sales within a given date range.

| Name         | Mode | Type | Description |
| ------------ | ---- | ---- | ----------- |
| p_start_date | IN   | DATE | Start date  |
| p_end_date   | IN   | DATE | End date    |

---

## 🔹 Procedure: Order Processing

### 10. `place_order`

**Type:** Procedure
**Description:** Creates a new order, reduces stock, and inserts into `Orders` and `OrderItem`.

**Parameters:**

| Name          | Mode | Type   | Description           |
| ------------- | ---- | ------ | --------------------- |
| p_customer_id | IN   | NUMBER | ID of the buyer       |
| p_product_id  | IN   | NUMBER | Product being ordered |
| p_quantity    | IN   | NUMBER | Quantity ordered      |

**Internal actions:**

* Validates customer & product
* Checks stock
* Creates new order
* Inserts order item
* Updates stock

**Outputs:**

* Displays order ID using `DBMS_OUTPUT`

---

## 🔹 Trigger

### 11. `trg_restrict_product_dml`

**Type:** Trigger
**Fires:** Before INSERT/UPDATE/DELETE on `Product`
**Description:**
Only allows DML operations:

* On **weekends**
* AND if **not a holiday**

All attempts are recorded in `Audit_Log`.

---

## ✅ Summary Table

| Name                    | Type      | Return Type   | Parameters               |
| ----------------------- | --------- | ------------- | ------------------------ |
| customer_exists         | Function  | BOOLEAN       | IN customer_id           |
| product_exists          | Function  | BOOLEAN       | IN product_id            |
| update_product_price    | Procedure | —             | IN product_id, new_price |
| bulk_increase_price     | Procedure | —             | IN percent               |
| get_total_spent         | Function  | NUMBER        | IN customer_id           |
| get_pending_orders      | Function  | SYS_REFCURSOR | None                     |
| customer_rank           | Function  | SYS_REFCURSOR | None                     |
| check_stock_status      | Function  | VARCHAR2      | IN product_id            |
| get_total_sales_by_date | Function  | NUMBER        | IN start_date, end_date  |
| place_order             | Procedure | —             | IN cust_id, prod_id, qty |


