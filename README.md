# Dynamic-Pricing-Simulation-Dashboard
Dynamic Pricing Simulation Dashboard built using Excel, SQL, and Power BI. This project analyzes historical sales data and simulates the impact of price changes on demand and revenue using DAX What-If parameters, price elasticity analysis, and interactive visuals to support data-driven pricing decisions.

# 📊 Dynamic Pricing Simulation Dashboard

## 📌 Project Overview
The **Dynamic Pricing Simulation Dashboard** is an end-to-end data analytics and business intelligence project designed to evaluate how price changes impact product demand and revenue. Using historical retail data, SQL-based feature engineering, and Power BI simulations, the project enables data-driven pricing decisions through interactive analysis.

---

## 🛠️ Tech Stack
- **Excel (.xlsx)** – Raw data storage & preprocessing  
- **SQL (MySQL)** – Data modeling, aggregation, and feature engineering  
- **Power BI** – Dashboard development & visualization  
- **Power Query** – ETL & data transformation  
- **DAX** – KPIs, price elasticity, and simulation logic  

---

## 📁 Repository Structure
Dynamic-Pricing-Simulation-Dashboard/
│
├── data/
│ └── elasticity_model.xlsx
│
├── sql/
│ └── dynamic_pricing.sql
│
├── powerbi/
│ └── Dynamic_Pricing_Simulation_Dashboard.pbix
│
├── screenshots/
│ ├── dashboard_overview.png
│ ├── category_filter_view.png
│ ├── price_simulation_view.png
│ ├── sql_schema.png
│ ├── sql_feature_engineering.png
│
└── README.md


---

## 📊 Dataset – Excel (.xlsx)
The dataset (`elasticity_model.xlsx`) contains historical retail sales data at the **product-category and monthly level**.

### Key Fields
- Product ID & Category  
- Month & Year  
- Quantity Sold  
- Unit Price & Lag Price  
- Total Price & Freight Cost  
- Holiday, Weekend & Weekday Indicators  
- Customer Count  
- Product Attributes (score, weight, photos)  
- Competitor Pricing (PS1, PS2, PS3)  

### Excel Processing
- Removed duplicates and invalid records  
- Standardized column formats  
- Verified pricing and quantity accuracy  
- Prepared structured input for SQL ingestion  

---

## 🗄️ SQL Data Modeling & Feature Engineering

### Database & Raw Table Creation
```sql
CREATE DATABASE dynamic_pricing;
USE dynamic_pricing;

CREATE TABLE retail_raw (
  product_id VARCHAR(50),
  product_category_name VARCHAR(100),
  month_year VARCHAR(20),
  qty INT,
  total_price DECIMAL(10,2),
  freight_price DECIMAL(10,2),
  unit_price DECIMAL(10,2),
  lag_price DECIMAL(10,2)
);
```
Feature Engineering

Key features created in SQL:

Revenue = qty * unit_price

Date conversion from month_year

Customer behavior flags (weekday, weekend, holiday)

Product attributes (weight, score, description length)

Competitor pricing comparison

```
(ps1 + ps2 + ps3) / 3 AS avg_comp_price,
unit_price / NULLIF((ps1 + ps2 + ps3) / 3, 0) AS price_index

```
🔄 Power BI & Power Query

Power Query was used to:

Import Excel and SQL data

Clean and transform columns

Merge tables and define relationships

Optimize the data model for performance

📐 DAX Measures & Price Simulation

Custom DAX measures were created for:

Historical Revenue

Simulated Revenue After Price Change

Quantity Impact

Average Unit Price

Price Elasticity by Category

🔘 What-If Parameter

A Price Change % slider allows users to dynamically adjust prices and instantly view:

Revenue impact

Demand response

Category-level elasticity

📈 Dashboard Features

KPI cards for Revenue, Quantity Sold, and Average Price

Price elasticity comparison across product categories

Annual revenue trend analysis

Price vs demand relationship visuals

Actual vs simulated revenue comparison

Interactive slicers for categories and pricing scenarios

💡 Business Value

Identifies price-sensitive and inelastic products

Supports data-driven pricing decisions

Reduces revenue risk before price changes

Enables scenario-based pricing strategy testing

👤 Author

Vanij Prasher
Data Analytics & Business Intelligence Project

⭐ If you found this project useful, feel free to star the repository!
