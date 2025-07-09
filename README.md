# 🛒 Olist Retail Domain Analysis on Databricks

**A domain-driven analytics project** for Brazilian e-commerce data using PySpark + SQL on Databricks.

## 📌 Objective

Explore and analyze core business domains in a retail e-commerce dataset, including:
- **Customer state**
- **Customer payment**
- **Customer segmentation**

This project focuses on **data exploration and analysis**, not a full ETL pipeline.

---

## 📚 Dataset

**[Olist Brazilian E-Commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)**  
An open dataset containing:
- Orders, order items
- Customers
- Payments
- Products
- Reviews
- Sellers
- Geolocation

---

## 📁 Notebook Structure

### `01_load_data_to_table`  
🔹 **Purpose:** Load CSV files into Delta tables on Databricks  
🔹 **Action:**
- Read CSVs from `DBFS Volumes`
- Create tables in `puttaradol.runtest` catalog  
🔹 **Tables:** `olist_orders`, `olist_customers`, `olist_payments`, etc.

---

### `02_customer_state_analysis`  
🔹 **Purpose:** Analyze customer distribution by state  
🔹 **Focus:**
- Join `customers` and `orders` tables
- Group by `customer_state`
- Count `unique_customers` and `total_orders` per state
- Save result to: `puttaradol.runtest.customer_order_summary_by_state`

---

### `03_customer_payment_analysis`  
🔹 **Purpose:** Calculate spending behavior per customer  
🔹 **Focus:**
- Join `customers`, `orders`, and `order_items` tables
- Group by `customer_unique_id`
- Calculate:
  - `order_count`: Number of unique orders per customer
  - `total_spent`: Total amount spent by each customer
  - `avg_order_value`: Average amount spent per order
- Save result to: `puttaradol.runtest.customer_summary_payments`

---

### `04_visualize_summary`  
🔹 **Purpose:** Visualize customer payment summary metrics  
🔹 **Source Table:** `puttaradol.runtest.customer_summary_payments`

🔹 **Charts:**
- **Bar Chart**: Total spent per customer
- **Bar Chart**: Average order value (AOV)
- **Bar Chart**: Order count per customer

🔹 **Tools:** `pandas`, `matplotlib`
  
---

### `05_customer_segmentation`  
🔹 **Purpose:** Classify customers into segments based on their total spending  
🔹 **Source Table:** `puttaradol.runtest.customer_summary_payments`  
🔹 **Logic:**
- `VIP` → total_spent > 1000  
- `Loyal` → total_spent > 500  
- `Normal` → otherwise

🔹 **Output Table:** `puttaradol.runtest.customer_segments`

🔹 **Visualization:**
- Pie Chart showing the proportion of each segment  
  (Built with `matplotlib` and `pandas`)

---

## 🧠 Tech Stack

- Databricks (PySpark, SQL, Delta Lake, DBFS)
- Kaggle Olist Dataset
- matplotlib
- GitHub for documentation

---

## 🙋 Author

**Puttaradol Pongpanich**  
CPAXTRA Intern | CEDT Chulalongkorn University  
