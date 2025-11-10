# Superstore Sales & Profitability Dashboard

### [Download the Power BI File (.pbix)](Power-BI-Sales-Analysis.pbix)

---

## 📈 Project Objective

This project analyzes sales, profit, and discount data from the Superstore dataset. The goal is to build a comprehensive dashboard for an executive team to identify sales trends, top-performing products, and the impact of promotional discounts on profitability.

---

## 📸 Dashboard Screenshots

### 1. Executive Summary
This page provides a high-level overview of key performance indicators (KPIs), sales trends over time, and geographic performance. It identifies **`Technology`** as the highest-selling category.

![Executive Summary](https://github.com/aditisharma23-05/Power-BI-Sales-Analysis/blob/main/Executive%20summary.png?raw=true)

### 2. Profit & Discount Analysis
This page performs a deep dive into profitability. It uses slicers for `Region` and `Category` to filter a scatter plot and treemap, revealing the direct (and negative) impact of discounts on profit margin.

![Profit & Discount Analysis](https://github.com/aditisharma23-05/Power-BI-Sales-Analysis/blob/main/Profit%20analysis.png?raw=true)

---

## ⚙️ Technical Process

This project was built in Power BI Desktop, following data analytics best practices:

1.  **ETL (Transform):** Loaded the flat-file dataset into Power Query. Here, I:
    * "Carved out" the single sheet into a proper **Star Schema** data model.
    * Created four dimension tables: `Dim_Product`, `Dim_Customer`, `Dim_Location`.
    * Created a `Fact_Sales` table by removing descriptive columns and keeping only IDs and numerical data.
    * Generated a dynamic **`Dim_Date`** table using M-code to span the full range of the sales data.
    * Corrected data types (e.g., fixed date-locale errors).

2.  **Data Modeling:** Connected the tables in the Model view to create a clean, single-direction flow from dimensions to the fact table. This optimizes performance and ensures accurate filtering.

3.  **DAX (Analyze):** Wrote DAX measures to create complex calculations beyond simple sums:
    * **Core KPIs:** `Total Sales`, `Total Profit`, `Total Quantity`.
    * **Profitability Insights:** `Profit Margin` (using `DIVIDE`) and `Avg Discount` (using `AVERAGE`) to analyze their relationship.

---

## 💡 Key Insights & Actionable Recommendations

(These insights are drawn directly from the dashboard visuals.)

* **Insight 1 (Sales Trend):** The sales trend is **not driven by simple holiday seasonality**. The data shows inconsistent peaks: 2014 peaked in March, while 2015 and 2017 peaked in November. This suggests that sales are more likely influenced by specific marketing campaigns or regional factors rather than a predictable end-of-year rush.

* **Insight 2 (Overall Health):** The business is in a strong, profitable position. A key finding from the treemap is that **no sub-categories are unprofitable**, meaning the company does not have any "money-losing" items.

* **Insight 3 (High Performers):** The primary profit drivers are **`Copiers`**, **`Phones`**, **`Accessories`**, and **`Paper`**. These are high-margin items that should be protected.

* **Insight 4 (Low Performers):** The *least* profitable sub-categories are **`Fasteners`**, **`Machines`**, and **`Labels`**. While still profitable, their margins are significantly smaller than the high performers.

* **Insight 5 (The "Why"):** The scatter plot confirms a clear negative correlation: **as discounts increase, profit margins decrease.** This strategy is likely the reason for the low profits in the `Machines` category, which often sees high discounts.

* **Recommendation 1:** **Protect the Winners.** The discount strategy for high-profit items like **`Copiers`** and **`Phones`** should be minimal. These items sell well and are highly profitable; they do not need aggressive discounts.

* **Recommendation 2:** **Lift the Laggards.** Investigate the pricing and discount strategy for **`Machines`** and **`Fasteners`**. The goal is to raise their profit margins, likely by reducing unnecessary discounts, without harming sales volume.
