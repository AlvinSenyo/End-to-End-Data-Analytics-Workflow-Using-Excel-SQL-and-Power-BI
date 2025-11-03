🧩 End-to-End Data Analytics Workflow Using Excel, SQL, and Power BI

This project demonstrates a complete, automated data analytics pipeline—from raw data collection and cleaning to advanced visualization—using Excel, PostgreSQL (SQL), and Power BI.

It showcases how to integrate these tools to deliver consistent, accurate, and interactive business intelligence across multiple regions.

🚀 Project Overview

Scenario:
You’ve been hired as a data analyst for a multinational retail company struggling with inconsistent regional reporting.
Your task: build a unified analytics system that consolidates data from multiple countries, cleans and processes it in SQL, and delivers a dynamic Power BI dashboard accessible remotely by stakeholders.

🌟 Highlights
Category	Key Feature
💾 Workflow Integration	Combines Excel (data prep), PostgreSQL (storage + cleaning), and Power BI (reporting).
🧹 SQL Data Cleaning	Handles nulls, removes duplicates, and standardizes formats.
📊 Analytical SQL Queries	Generates top products, countries, and representatives with key metrics.
☁️ Cloud Backup	Automated SQL backups synced to Google Drive.
📈 Interactive Dashboard	KPIs, filters, and maps for dynamic business insights.
🌍 Geospatial & Temporal Analysis	Visuals for sales by region and time period.
⚙️ Optimization	Fast execution, clean design, and smooth performance.
🧠 Key Insights

Unified Pipeline: Excel → SQL → Power BI delivers a scalable and transparent workflow.

Data Integrity: SQL standardization (columns, data types, primary keys) ensures clean analytics.

Business Insights via SQL: Analytical queries uncover trends like bestsellers and profit leaders.

Cloud Resilience: Automated Drive backups protect and version data.

Dashboard Interactivity: Power BI slicers and visuals empower self-service analytics.

Design Matters: Consistent themes and minimalist visuals enhance clarity.

🧩 Detailed Workflow
1️⃣ Data Preparation (Excel & CSV)

Six datasets (one per country) with 15 identical columns.

Converted Excel files to CSV format.

Ensured all columns align in structure and naming before import.

📁 Example Files:

sales_canada.csv  
sales_china.csv  
sales_brazil.csv  
sales_usa.csv  
sales_uk.csv  
sales_australia.csv

2️⃣ Database Setup in PostgreSQL

Created database: data_professionals.

Defined tables (sales_canada, sales_china, etc.) using correct data types (text, date, numeric).

Set primary key on transaction_id to avoid duplicates.

Imported CSVs via pgAdmin’s Import Tool.

Combined all datasets with a UNION ALL query:

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

3️⃣ Data Cleaning and Processing (SQL)

Checked for missing values:

SELECT * FROM sales_data WHERE price_per_unit IS NULL OR quantity_purchased IS NULL;


Replaced nulls:

UPDATE sales_data
SET price_per_unit = (SELECT AVG(price_per_unit) FROM sales_data)
WHERE price_per_unit IS NULL;


Removed duplicates and standardized entries.

Added calculated fields:

ALTER TABLE sales_data ADD COLUMN total_amount NUMERIC;
UPDATE sales_data
SET total_amount = (price_per_unit * quantity_purchased) - discount_applied;

4️⃣ Analytical SQL Queries

Key business questions addressed:

Revenue and Profit by Country

Top 5 Bestselling Products

Top 5 Sales Representatives

Top 5 Store Locations

Summary Statistics

Example Query:

SELECT country, SUM(total_amount) AS total_sales, SUM(profit) AS total_profit
FROM sales_data
GROUP BY country
ORDER BY total_sales DESC;

5️⃣ Automating SQL Backups

Installed Google Drive for Desktop.

Configured PostgreSQL to back up the database to a synced folder:

pg_dump -U postgres data_professionals > "C:\DriveSync\backups\data_backup_2025_02_14.sql"


Backups automatically upload to Google Drive.

✅ Free, version-controlled, cloud-safe.

6️⃣ Importing into Power BI

Connected Power BI to PostgreSQL using credentials:

Server: localhost

Database: data_professionals

Imported or transformed data in Power Query.

Live connection enabled — SQL updates refresh dynamically in Power BI.

7️⃣ Building the Dashboard (Power BI)

Created KPIs using Measures:

Total Sales = SUM(sales_data[total_amount])
Total Profit = SUM(sales_data[profit])
Average Order Value = DIVIDE([Total Sales], DISTINCTCOUNT(sales_data[transaction_id]))


Added Visuals:

KPI Cards → Sales, Profit, Orders, Discounts

Slicers → Country, Store, Category, Payment Method, Date Range

Map Visual → Sales by Location

Line & Bar Charts → Monthly & Daily Trends

Donut Chart → Payment Method Distribution

Scatter Plot → Discount vs Profit (Animated by Month)

🎨 Design Tips:

Consistent colors (purple/blue scheme)

Shadows and glow for card emphasis

Minimal clutter for readability

8️⃣ Testing and Publishing

Tested slicers and visual interactivity.

Saved .pbix file and published to Power BI Service.

Used Publish to Web to share public dashboard link.

⚠️ Note: Free Power BI requires manual refresh after SQL updates.

📊 Key Insights and Conclusions

End-to-end automation transforms scattered data into actionable insights.

SQL-driven transformations ensure accuracy and scalability.

Power BI’s visuals empower decision-makers with interactive storytelling.

Cloud backups provide a low-cost, reliable safeguard for ongoing projects.

This workflow bridges technical data handling and business communication—a vital skillset for analysts.

🧩 Recommendations for Learners

✅ Verify column count and types before importing into SQL.
✅ Use primary keys to maintain uniqueness.
✅ Apply GROUP BY, ORDER BY, and LIMIT for report queries.
✅ Use Power Query for cleaning before visualizing.
✅ Keep dashboard design clean and consistent.
✅ Automate backups to protect work.
✅ Use AI tools (like ChatGPT) for DAX and SQL debugging.
