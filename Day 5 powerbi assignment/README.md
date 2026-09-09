# Executive Sales & Profitability Dashboard — Power BI Practical Assessment

**Course:** Business Intelligence & Data Analytics
**Dataset:** Sample Superstore
**Tool:** Microsoft Power BI Desktop
**Assessment:** In-Class Practical (60 Minutes | 100 Marks)

---

## 1. Project Overview

This project focuses on creating an Executive Dashboard using the Sample Superstore dataset in Power BI. The dashboard covers the complete process, starting from importing and cleaning the data in Power Query, creating useful DAX measures, and finally building an interactive dashboard with Region and Segment filters.

### Headline KPIs (Unfiltered View)

| KPI             | Value    |
| --------------- | -------- |
| Total Revenue   | $429.65K |
| Total Profit    | $60.30K  |
| Profit Margin % | 14.03%   |
| Total Orders    | 909      |

### Category-Level Breakdown

| Category        | Total Profit   | Total Revenue    | Profit Margin % |
| --------------- | -------------- | ---------------- | --------------- |
| Furniture       | $3,875.38      | $1,21,930.70     | 3.18%           |
| Office Supplies | $25,933.16     | $1,24,418.43     | 20.84%          |
| Technology      | $30,490.14     | $1,83,304.02     | 16.63%          |
| **Total**       | **$60,298.68** | **$4,29,653.15** | **14.03%**      |

---

## 2. Data Transformation (Power Query - Part 1)

Before creating the dashboard, I cleaned and prepared the dataset in Power Query.

* **Headers and Data Types:** Promoted the first row as headers and checked that the columns had the correct data types. For example, `Order Date` and `Ship Date` were set as Date, while `Sales`, `Profit`, and `Discount` were set as Decimal and `Quantity` was set as Whole Number.

* **Days to Ship:** Created a new column called **Days_to_Ship** to calculate how many days it took to ship an order. The following formula was used:
  `Duration.Days([Ship Date] - [Order Date])`

* **Data Cleaning:** Used the Trim function on `Category`, `Sub-Category`, and `Segment` to remove any unnecessary spaces and keep the data consistent.

---

## 3. DAX Measures (Part 2)

I created the following DAX measures to calculate the main business KPIs used in the dashboard:

```dax
Total Revenue = SUM(Orders[Sales])
Total Profit = SUM(Orders[Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Revenue], 0)
Total Orders = DISTINCTCOUNT(Orders[Order ID])
Average Order Value = DIVIDE([Total Revenue], [Total Orders], 0)
```

These measures are used to display the key revenue, profit, margin, order, and average order value information in the dashboard.
