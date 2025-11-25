
# 📘 RetailFlow Management System – MIS Summary Report 

## 1. Scope of the System

This MIS supports the **end-to-end order processing lifecycle** within an e-commerce environment. It covers customer interactions, order creation, inventory validation, payment verification, and delivery scheduling. The scope aligns with MIS principles by integrating people, processes, and technology to manage business operations efficiently.

The system uses seven database tables to coordinate workflow: **customer, product, category, orders, order_item, payment, delivery**.

---

## **2. Business Process Overview**

1. Customers browse products and submit orders.
2. System validates stock and sends order details to Admin.
3. Admin approves the order and adjusts inventory.
4. Finance verifies payment and handles retries if needed.
5. Delivery schedules and dispatches orders to customers.

---

## **3. Objectives & Outcomes**

### **Objectives**

* Provide accurate, automated order tracking.
* Ensure real-time inventory monitoring.
* Maintain secure, traceable financial transactions.
* Improve communication between sales, finance, and logistics.
* Enhance customer experience through timely delivery.

### **Expected Outcomes**

* Reduced order-to-delivery time.
* Lower inventory discrepancies and stockouts.
* Improved accuracy of financial records.
* Streamlined departmental coordination.
* Increased customer satisfaction and trust.

---

## **4. Key Entities (Based on Schema Tables)**

### **1. Customer**

Stores customer details, enabling user identification, order history tracking, and personalized service.

### **2. Product**

Contains product information including price and stock level.

### **3. Category**

This Holds the list of all Products currently we have.

### **4. Orders**

Represents each order placed by a customer.

### **5. Order_Item**

Breaks down each order into individual product items, quantities, and totals. Critical for revenue calculation and stock management.

### **6. Payment**

Captures transaction detail.

### **7. Delivery**

Stores delivery schedule, dispatch status, and logistics information.



## **5. Roles & Responsibilities**

* **Customer** – Initiates orders through the website.
* **Sales System** – Receives orders and validates stock.
* **Admin** – Reviews orders, approves them, updates inventory tables.
* **Finance Team/System** – Confirms payments using the *payment* table.
* **Delivery Team** – Plans delivery and updates the *delivery* table after dispatch.

---

## **6. MIS Components & Organizational Impact**

### **Key MIS Functions**

* **Transaction Processing:**
  Orders, payments, deliveries, and stock adjustments recorded in real-time.

* **Data Storage & Integration:**
  The seven-table schema ensures structured data flow between departments.

* **Internal Control & Accuracy:**
  Payment verification, stock validation, and delivery confirmation reduce errors.

* **Decision Support:**
  Management can analyze sales, customer trends, high-demand categories, and stock turnover.

### **Organizational Impact**

* Greater operational efficiency and faster processing.
* More accurate forecasting and purchasing decisions.
* Reduced financial and logistic errors.
* Better customer service and repeat purchases.

---

