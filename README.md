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

---

### **3️⃣ Data Cleaning and Processing (SQL)**
Checked for missing values:

SELECT * FROM sales_data 
WHERE price_per_unit IS NULL OR quantity_purchased IS NULL;


Replaced nulls:

UPDATE sales_data
SET price_per_unit = (SELECT AVG(price_per_unit) FROM sales_data)
WHERE price_per_unit IS NULL;


Removed duplicates and standardized entries.

Added calculated field:

ALTER TABLE sales_data ADD COLUMN total_amount NUMERIC;
UPDATE sales_data
SET total_amount = (price_per_unit * quantity_purchased) - discount_applied;

---

### **4️⃣ Analytical SQL Queries**

Revenue and Profit by Country
- Top 5 Bestselling Products
- Top 5 Sales Representatives
- Top 5 Store Locations

Summary Statistics

Example Query:

SELECT country, 
       SUM(total_amount) AS total_sales, 
       SUM(profit) AS total_profit
FROM sales_data
GROUP BY country
ORDER BY total_sales DESC;

---

### **5️⃣ Automating SQL Backups

Installed Google Drive for Desktop.

Configured PostgreSQL to back up automatically:

pg_dump -U postgres data_professionals > "C:\DriveSync\backups\data_backup_2025_02_14.sql"


Backups automatically sync to Google Drive.

✅ Provides free, version-controlled cloud safety.

### **6️⃣ Importing into Power BI

Connected Power BI to PostgreSQL:
Server: localhost
Database: data

Imported or transformed data via Power Query.

Enabled live connection for dynamic refresh from SQL.

### **7️⃣ Building the Dashboard (Power BI)

Created Measures (DAX):

Total Sales = SUM(sales_data[total_amount])
Total Profit = SUM(sales_data[profit])
Average Order Value = DIVIDE([Total Sales], DISTINCTCOUNT(sales_data[transaction_id]))


Added Visuals:

📊 KPI Cards → Sales, Profit, Orders, Discounts

🔍 Slicers → Country, Store, Category, Payment Method, Date Range

🗺️ Map → Sales by Region

📈 Line & Bar Charts → Monthly & Daily Trends

🍩 Donut Chart → Payment Method Distribution

⚡ Scatter Plot → Discount vs Profit (Animated by Month)

🎨 Design Tips:

Consistent purple/blue color theme

Subtle shadows & glow for emphasis

Clean layout, no clutter

8️⃣ Testing and Publishing

Verified slicers & interactivity

Saved .pbix file and published to Power BI Service

Used Publish to Web for public link

⚠️ Free Power BI users must manually refresh after SQL updates.

📊 Key Takeaways

End-to-end automation from data prep to visualization.

SQL-driven transformations ensure data accuracy.

Power BI enables insightful storytelling with interactivity.

Cloud backup ensures security & version control.

Seamless integration of Excel, SQL, and Power BI for business impact.

🧩 Recommendations for Learners

✅ Verify columns before importing to SQL
✅ Always use primary keys
✅ Use GROUP BY, ORDER BY, and LIMIT for summaries
✅ Leverage Power Query for data cleaning
✅ Maintain a consistent design theme
✅ Automate database backups
✅ Use AI tools (e.g., ChatGPT) for DAX & SQL troubleshooting
