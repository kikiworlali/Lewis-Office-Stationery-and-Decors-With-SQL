## Project Description

Lewis is a US-based retailer specializing in office supplies, furnishings, maintenance, and housekeeping equipment. This project involves performing a comprehensive performance analysis for the business owner to understand historical sales trends and product performance. As a data analyst, the primary objective is to extract, transform, and analyze raw transaction data stored in a SQL database to provide actionable business intelligence regarding revenue, order volume, and inventory movement.

---

## Overview

The analysis focuses on several key performance indicators (KPIs) and business logic requirements:
* **Revenue Optimization:** Calculating total revenue while accounting for tiered discount structures based on product pricing.
* **Data Integrity:** Handling missing values (NULLs) in product pricing by applying default valuations to ensure accurate financial reporting.
* **Temporal Analysis:** Isolating business performance specifically for the 2015 fiscal year.
* **Product Insights:** Identifying top-performing products and evaluating the financial footprint of stagnant inventory (products never ordered).

---

## Technologies Used

* **SQL (Structured Query Language):** The primary tool used for data extraction and transformation.
* **Relational Database Management System:** Used to manage the `orders` and `products` tables.
* **Data Transformation Functions:**
    * `COALESCE` for null handling.
    * `CASE` statements for conditional logic (discounts).
    * `CAST` for data type conversion and date formatting.
    * `JOIN` operations for relational mapping between sales and inventory.

---

## Instructions

To replicate this analysis, follow these steps:
1.  **Database Connection:** Ensure you are connected to the SQL environment containing the `orders` and `products` tables.
2.  **Schema Alignment:** Verify that the `ProductID` column exists in both tables to facilitate accurate joins.
3.  **Data Cleaning:** Note that the scripts include logic to treat NULL prices as 10 to prevent calculation errors.
4.  **Date Handling:** Ensure the `OrderDate` column is either in a standard date format or use the `CAST(... AS date)` function provided in the script to filter by the 2015 calendar year.

---

## Queries and Insights

### 1. Tiered Revenue by Category
**Logic:** A 10% discount is applied to products over \$100 and a 5% discount to those between \$50 and \$100.
* **Insight:** This query allows Lewis to see which categories contribute most to the bottom line after promotional pricing is factored in.

### 2. Revenue with Default Pricing
**Logic:** Replaces NULL prices with a default value of 10.
* **Insight:** This ensures that no sales quantity goes uncounted due to missing price metadata, providing a "floor" for total revenue estimates.

### 3. 2015 Order Volume
**Logic:** Counts unique `OrderID` entries within the 2015 date range.
* **Insight:** Establishes a baseline for customer activity and transaction frequency for the specific fiscal year.

### 4. Top-Selling Product (2015)
**Logic:** Joins products and orders to find the item with the highest total quantity sold.
* **Insight:** Identifies the "hero product," allowing the business to prioritize stock levels and marketing for high-demand items.

### 5. Stagnant Inventory Analysis
**Logic:** Calculates the average price of products that have $0$ orders.
* **Insight:** Highlights capital tied up in unsold inventory. If the average price is high, it suggests that expensive items may be overvalued or under-marketed.

---

## Recommendation

* **Promotional Review:** Analyze if the 5% and 10% discounts are driving enough volume to justify the margin squeeze, especially in the highest-selling categories.
* **Data Governance:** Address the root cause of NULL values in the `Price` column. Relying on a default value of 10 may skew financial accuracy over time.
* **Inventory Clearance:** For products identified as "never ordered," consider a clearance sale or bundling them with the "top-selling" products of 2015 to recover tied-up capital.

---

## Conclusion

The SQL analysis provides a robust framework for Lewis to understand his business performance. By bridging the gap between raw sales data and strategic insights—such as discounted revenue and inventory health—the business can move toward more data-driven decision-making. The 2015 data serves as a critical benchmark for future growth and inventory optimization.

**Would you like me to generate a visualization of how the tiered discounts affect the final revenue per category?**
