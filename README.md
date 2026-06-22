# 📊 E-Commerce Sales Analysis Using Power BI and DAX

An interactive Power BI dashboard developed to analyze e-commerce sales performance, profitability, sales targets, and customer purchasing trends using DAX calculations and data visualization techniques.

## 📑 Table of Contents

* Project Overview
* Data Sources & Architecture
* Data Transformation (ETL)
* Data Model & DAX
* Dashboard Features
* Key Insights
* How To Use

---

# 🎯 Project Overview

### Business Problem

E-commerce businesses generate large volumes of transactional data, making it difficult to monitor sales performance, profitability, and target achievement effectively. This project aims to transform raw sales data into meaningful business insights through interactive dashboards.

### Objective

* Analyze sales performance across categories and regions.
* Compare actual sales against predefined targets.
* Identify profitable products and sales trends.
* Support data-driven business decision-making through interactive visualizations.

### Target Audience

* Business Managers
* Sales Operations Teams
* Executive Leadership
* Data Analysts

---

# 🗃️ Data Sources & Architecture

### Source Systems

* Local Excel Files (.xlsx)

### Datasets Used

1. List of Orders

   * Order ID
   * Order Date
   * Customer Name
   * City
   * State
   * Category
   * Amount
   * Profit

2. Order Details

   * Order ID
   * Category
   * Sub-Category
   * Quantity
   * Amount
   * Profit

3. Sales Target

   * Category
   * Month of Order Date
   * Target

### Data Volume

* Multiple years of e-commerce transactional data containing customer orders, product information, and sales targets.

### Storage Mode

* Import Mode

---

# ⚙️ Data Transformation (ETL)

### Tool Used

* Power Query Editor

### Key Cleanups

* Removed null and duplicate records.
* Corrected data types.
* Created relationships between tables.
* Standardized column names.
* Prepared data for reporting and analysis.

### Custom Functions

* No custom M scripts were used.

---

# 🧠 Data Model & DAX

### Model Type

* Relational Data Model (Star Schema)

### Fact Tables

* Order Details
* List of Orders

### Dimension Tables

* Sales Target
* Date Table (created using Order Date)

### Key DAX Calculations

```dax
Category Type = [Category] & " - " & [Sub-Category]
```

```dax
Revenue = [Amount] * [Quantity]
```

```dax
Sales Category =
IF(
    'Order Details'[Revenue] >
    AVERAGE('Order Details'[Revenue]),
    "Above Average",
    "Below Average"
)
```

```dax
Order Count =
DISTINCTCOUNT('Order Details'[Order ID])
```

```dax
Average Profit in Delhi =
CALCULATE(
    AVERAGE('Order Details'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

```dax
YTD Sales =
TOTALYTD(
    SUM('Order Details'[Amount]),
    'List of Orders'[Order Date]
)
```

---

# 🖥️ Dashboard Features

### Page 1: Sales Performance Dashboard

* Sales Target Achievement by Category
* Monthly Sales Trend
* Maximum Profit Margin by Sub-Category
* Profit vs Quantity Analysis

### Page 2: Business Performance Dashboard

* Total Sales Amount vs Target
* Sales Performance Matrix
* Geographic Sales Analysis
* Sales Distribution by Sub-Category
* Order Count Analysis by State

### Design Theme

* Interactive dashboard with cross-filtering capabilities.
* Business-focused visual storytelling.
* Clean and professional layout.

---

# 💡 Key Insights

* Clothing exceeded its sales target, while Electronics failed to achieve its target.
* January and March recorded the highest sales, whereas July had the lowest sales.
* Handkerchief, T-Shirt, and Stole generated the highest profit margins.
* Higher sales quantities do not always result in higher profits.
* The company narrowly missed its overall sales target.
* Sales are concentrated in a few major cities.
* Printers, Phones, Bookcases, and Sarees contributed the highest sales.
* Madhya Pradesh and Maharashtra recorded the highest number of orders.

### Business Recommendations

* Increase promotional activities for Electronics products.
* Implement sales campaigns during low-performing months.
* Maintain inventory for high-performing products.
* Develop targeted strategies for low-performing products and regions.
* Use dashboard insights to improve forecasting and business planning.

<img width="1221" height="357" alt="Ecommerce-Sales Dashboard Using DAX and Data Visualization" src="https://github.com/user-attachments/assets/c2e5c2e1-57ac-4fbf-8488-5c9448f4b30d" />


---

# 🚀 How To Use

### Prerequisites

* Microsoft Power BI Desktop installed.

### Steps

1. Download or clone the repository.
2. Open the `.pbix` file in Power BI Desktop.
3. Update the data source path if required.
4. Refresh the data.
5. Explore the interactive dashboard using filters and slicers.

---

# 🛠️ Tools & Technologies Used

* Microsoft Power BI Desktop
* Power Query Editor
* DAX (Data Analysis Expressions)
* Data Modeling
* Data Visualization
* Business Intelligence & Analytics
