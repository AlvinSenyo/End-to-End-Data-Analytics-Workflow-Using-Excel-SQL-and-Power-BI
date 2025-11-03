# 🧩 End-to-End Data Analytics Workflow Using Excel, SQL, and Power BI

This project demonstrates a **complete, automated data analytics pipeline** — from raw data collection and cleaning to advanced visualization — using **Excel**, **PostgreSQL (SQL)**, and **Power BI**.

It showcases how to integrate these tools to deliver consistent, accurate, and interactive business intelligence across multiple regions.

---

## 🚀 Project Overview

**Scenario:**  
You’ve been hired as a data analyst for a multinational retail company struggling with inconsistent regional reporting.  
Your task: **build a unified analytics system** that consolidates data from multiple countries, cleans and processes it in SQL, and delivers a **dynamic Power BI dashboard** accessible remotely by stakeholders.

---

## 🌟 Highlights

| Category | Key Feature |
|-----------|--------------|
| 💾 **Workflow Integration** | Combines Excel (data prep), PostgreSQL (storage + cleaning), and Power BI (reporting). |
| 🧹 **SQL Data Cleaning** | Handles nulls, removes duplicates, and standardizes formats. |
| 📊 **Analytical SQL Queries** | Generates top products, countries, and representatives with key metrics. |
| ☁️ **Cloud Backup** | Automated SQL backups synced to Google Drive. |
| 📈 **Interactive Dashboard** | KPIs, filters, and maps for dynamic business insights. |
| 🌍 **Geospatial & Temporal Analysis** | Visuals for sales by region and time period. |
| ⚙️ **Optimization** | Fast execution, clean design, and smooth performance. |

---

## 🧠 Key Insights

- **Unified Pipeline:** Excel → SQL → Power BI delivers a scalable and transparent workflow.  
- **Data Integrity:** SQL standardization (columns, data types, primary keys) ensures clean analytics.  
- **Business Insights via SQL:** Analytical queries uncover trends like bestsellers and profit leaders.  
- **Cloud Resilience:** Automated Drive backups protect and version data.  
- **Dashboard Interactivity:** Power BI slicers and visuals empower self-service analytics.  
- **Design Matters:** Consistent themes and minimalist visuals enhance clarity.

---

## 🧩 Detailed Workflow

### **1️⃣ Data Preparation (Excel & CSV)**
- Six datasets (one per country) with **15 identical columns**.  
- Converted Excel files to **CSV** format.  
- Ensured all columns align in structure and naming before import.  

**📁 Example Files:**
sales_canada.csv
sales_china.csv
sales_brazil.csv
sales_usa.csv
sales_uk.csv
sales_australia.csv

---

### **2️⃣ Database Setup in PostgreSQL**
- Created database: `data_professionals`  
- Defined tables (`sales_canada`, `sales_china`, etc.) with correct **data types**.  
- Set **primary key** on `transaction_id`.  
- Imported CSVs using **pgAdmin Import Tool**.  
- Combined datasets using `UNION ALL`:

```sql
CREATE TABLE sales_data AS
SELECT * FROM sales_canada
UNION ALL
SELECT * FROM sales_china
UNION ALL
SELECT * FROM sales_usa
UNION ALL
SELECT * FROM sales_brazil
UNION ALL
SELECT * FROM sales_uk
UNION ALL
SELECT * FROM sales_australia;
