# Sales Data Analysis Dashboard

**Project Type:**

Power BI Sales & Business Performance Analysis


---

## Problem Statement

This dashboard helps **ElectroHub**(Example Company) understand its **sales performance, profitability, and customer behavior** across different products, promotions, and time periods.

By analyzing **Net Sales, Profit, Orders, Discounts, and Trends**, the dashboard enables the business to:

* Identify high- and low-performing products
* Understand the impact of promotions on sales
* Track sales and profit trends over time
* Analyze customer purchasing behavior
* Support data-driven decisions to improve revenue and profitability

---

## Dataset Overview

The dataset contains transactional sales data including:

* Order details
* Product and category information
* Customer data
* Promotional discounts
* Sales, profit, and quantity metrics
* Date-level sales records

---

## Steps Followed

### Step 1: Data Loading

* Imported sales data into **Power BI Desktop**
* Source file: structured sales dataset (Excel)

---

### Step 2: Data Cleaning (Power Query)

* Opened **Power Query Editor**
* Enabled:

  * Column Distribution
  * Column Quality
  * Column Profile
* Switched profiling to **entire dataset**
* Verified:

  * No duplicate records
  * Corrected data types (Date, Currency, Numbers)
* **Merged tables** & **Added Conditional Columns** to bring the required columns/data to the **Fact Table** from the **Dimension Tables**.
* Added **Profit Column** by using the existed columns in the **Fact Table**.
---

### Step 3: Data Modeling

* Created a **star schema** model:

  * Fact Sales Table
  * Dimension tables:

    * Date
    * Product
    * Customer
    * Promotion
* Established proper relationships
* Marked Date table for time intelligence

---

### Step 4: DAX Measures Created

Key measures include:

```DAX
Sum of Net Sales = CALCULATE(SUM('Fact Table'[Net Sales]),
ALL('Date Table 1'),
USERELATIONSHIP('Date Table 2'[Date],'Fact Table'[Date (dd/mm/yyyy)]))

Sum of Profit = CALCULATE(SUM('Fact Table'[Profit]),
ALL('Date Table 1'),
USERELATIONSHIP('Date Table 2'[Date],'Fact Table'[Date (dd/mm/yyyy)]))

Sum of Quantity = CALCULATE(SUM('Fact Table'[Units Sold]),
ALL('Date Table 1'),
USERELATIONSHIP('Date Table 2'[Date],'Fact Table'[Date (dd/mm/yyyy)]))

Sum Dim = SUM('Fact Table'[Net Sales])

Date Table 1 = CALENDARAUTO()

Date Table 2 = CALENDARAUTO()
```

These measures are reused across visuals to maintain consistency.

---

### Step 5: Date Tables, Slicers & Time Analysis

* Created two separate Date tables to support independent date-based analysis

* Used these Date tables as dedicated slicers

* Enabled users to:

* Filter Sales, Quantity, and Profit across different time periods

* Compare business performance dynamically using slicers

* Enabled drill-down functionality in trend visuals

This approach improves flexibility and allows users to analyze multiple KPIs over time without affecting unrelated visuals.
---

### Step 6: Report Design & Theme

* Applied a consistent theme for:

  * Fonts
  * Colors
  * Backgrounds
* Used clear section titles and aligned layouts
* Focused on **business readability**

---

### Step 7: Visuals Created

The following visuals were added:

* **KPI Cards**

  * Total Net Sales
  * Total Profit
  * Total Orders
* **Line Chart**

  * Sales Trend by Period
* **Bar / Column Charts**

  * Top & Bottom Products
  * Sales by Category
* **Scatter Plot**

  * Profit vs Net Sales
* **Promotion Analysis**

  * Average Discount by Promotion Type
* **Geographical Analysis**

  * Azure Maps (City-wise Sales)
* **Slicers**

  * Date
  * Product Category
  * Promotion
  * Customer Segment

---

### Step 8: Interactivity

* Enabled:

  * Drill-down
  * Cross-filtering
  * Tooltip insights
* Created a clean navigation flow across report pages

---

## Snapshot of Dashboard (Power BI Desktop)

> **Over View Page**
![Overview page](images/Overview_report.png)

> **Top & Bottom 5 Analysis Page**
![Top & Bottom 5 Analysis](images/Top_&_Bottom_5_Analysis.png)

> **Comparison of Sales/Profit/Quantity Sold Page**
![Comparison of Sales/Profit/Quantity Sold](images/Comparison_of_Sales_Profit_Quantity_Sold.png)

> **Table View Page**
![Table View](images/Table_View.png)

---

## Insights

### [1] Overall Performance

* The dashboard provides a consolidated view of **sales, profit, and orders**
* Certain product categories contribute disproportionately to revenue

---

### [2] Sales Trend Analysis

* Sales show **seasonal fluctuations**
* Peak sales periods align with promotional campaigns
* Drill-down reveals month-level performance variations

---

### [3] Profit vs Net Sales

* Higher sales do not always result in higher profit
* Some products generate high revenue but low margins
* This insight helps optimize pricing and promotions

---

### [4] Promotion Impact

* Promotions increase order volume
* Excessive discounts reduce overall profitability
* Balanced promotional strategies perform best

---

### [5] Customer & Product Insights

* A small number of products drive a large share of revenue
* Repeat customers contribute significantly to total sales
* Product performance varies by region and time period




