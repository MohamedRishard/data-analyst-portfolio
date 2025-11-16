# Walmart Sales Analysis – Data Analyst Portfolio Project

## Project Overview
This project analyzes Walmart sales data to uncover key insights about store performance, department sales, holiday impacts, and monthly sales trends. The analysis uses SQL for data aggregation, Python for initial exploration, and Power BI for visual reporting.

---

## Dataset
- **Source:** Walmart Sales Forecasting Dataset  
- **Files Used:** `train.csv`, `stores.csv`, `features.csv`  
- **Columns of Interest:** 
  - `Store`, `Dept`, `Date`, `Weekly_Sales`, `IsHoliday`
  - `Temperature`, `Fuel_Price`, `CPI`, `Unemployment`
  - `Store Type`, `Store Size`

---

## Tools Used
- **SQL (MySQL)** – Data aggregation, calculating total sales, department ranking, holiday sales, and monthly trends.
- **Power BI** – Dashboard creation with interactive visualizations.

---

## Key Insights
1. **Total Sales Overview:** Shows the overall sales across all stores.
2. **Top Stores by Sales:** Highlights the highest-grossing stores.
3. **Department Sales Analysis:** Identifies top-performing departments in each store.
4. **Monthly Sales Trends:** Reveals seasonal sales patterns across months.
5. **Department Rank per Store:** Ranks each department within a store based on sales, with conditional formatting for easy visualization.

---

## Power BI Dashboard
The Power BI dashboard contains the following visuals:
- Total Sales (Card)  
- Store Sales (Bar Chart)  
- Department Sales (Bar Chart)  
- Monthly Sales Trends (Line Chart)  
- Department Rank per Store  

**Screenshot Example:**

(screenshot.png)

---

## SQL Queries
Some example queries used in this project:

```sql
-- Total Sales per Store
SELECT Store, SUM(Weekly_Sales) AS Store_Sales
FROM train
GROUP BY Store
ORDER BY Store_Sales DESC;

-- Total Sales
SELECT SUM(Weekly_Sales) AS Total_Sales
FROM train;

-- Department Sales per Store with Ranking
SELECT Store, Dept, SUM(Weekly_Sales) AS Dept_Sales,
       RANK() OVER (PARTITION BY Store ORDER BY SUM(Weekly_Sales) DESC) AS Dept_Rank
FROM train
GROUP BY Store, Dept;
