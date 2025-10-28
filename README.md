🧩 Project 2: SQL + Power BI Sales Performance Dashboard

🎯 Overview
This project builds an interactive 'Sales Performance Dashboard' using 'MySQL + Power BI' with the same Superstore dataset to analyze sales, profit, and customer performance across regions and time.

🧰 Tools & Technologies
- MySQL 8.0
- Power BI Desktop
- DAX (for KPIs)
- CSV dataset (Superstore Sales)

📂 Project Structure

superstore-dashboard/
│
├── superstore_sales.csv
├── superstore_sales_dashboard.pbix
└── README.md


⚙️ Step-by-Step Setup

1. Create MySQL Database and Table
-sql
CREATE DATABASE sales_db;
USE sales_db;

CREATE TABLE superstore (
    Row_ID INT,
    Order_ID VARCHAR(50),
    Order_Date DATE,
    Ship_Date DATE,
    Ship_Mode VARCHAR(50),
    Customer_ID VARCHAR(50),
    Customer_Name VARCHAR(100),
    Segment VARCHAR(50),
    Country VARCHAR(50),
    City VARCHAR(100),
    State VARCHAR(100),
    Postal_Code VARCHAR(20),
    Region VARCHAR(50),
    Product_ID VARCHAR(50),
    Category VARCHAR(50),
    Sub_Category VARCHAR(50),
    Product_Name VARCHAR(255),
    Sales DECIMAL(10,2)
);

2. Import CSV Data
-sql
LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/superstore_sales.csv'
INTO TABLE superstore
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS
(order_id, order_date, ship_date, ship_mode, customer_id, customer_name, segment, country, city, state, postal_code, region, product_id, category, sub_category, product_name, sales)
SET order_date = STR_TO_DATE(order_date, '%m/%d/%Y'),
    ship_date = STR_TO_DATE(ship_date, '%m/%d/%Y');

3. Connect Power BI to MySQL
- Open 'Power BI → Get Data → MySQL Database'
- Enter server = `localhost` and database = `sales_db`
- Load the 'superstore' table

4. Create Dashboard Components
- KPIs: Total Sales, Orders, Customers, Avg Order Value
- Bar Chart: Sales by Region
- Line Chart: Monthly Sales Trend
- Pie Chart: Category-wise Sales
- Table: Top 10 Customers by Sales

5. Example DAX Measures
-DAX
Total Sales = SUM('superstore'[Sales])
Total Orders = DISTINCTCOUNT('superstore'[Order_ID])
Total Customers = DISTINCTCOUNT('superstore'[Customer_ID])
Avg Order Value = DIVIDE([Total Sales], [Total Orders])

6. Styling
- Add a rectangle shape behind KPI cards
- Use light gray background and white cards
- Add borders and slicers for Region, Category, Year


📸 Dashboard Preview

<img width="1521" height="855" alt="Screenshot 2025-10-28 021026" src="https://github.com/user-attachments/assets/d0386f0e-f1d6-443b-a1a5-ccdab3fd49d2" />
<img width="1516" height="853" alt="Screenshot 2025-10-28 021048" src="https://github.com/user-attachments/assets/b9e8e647-6809-4dcb-acd0-a770a25a5aef" />



Author: Mohammed Mohiuddin Khan  
GitHub: [Mohiuddin2003](https://github.com/Mohiuddin2003)
