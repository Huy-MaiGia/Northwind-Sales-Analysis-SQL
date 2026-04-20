# Northwind-Sales-Analysis-SQL
Project Overview: Northwind Sales & Behavioral Analytics
This project is a deep-dive data analysis of the Northwind Traders database—a classic retail dataset representing a specialty foods export-import company. The goal of this project is to move beyond basic reporting and uncover hidden patterns in customer spending, product performance, and sales trends using advanced SQL techniques.

1. The Problem
Standard business reports often provide a flat view of data (e.g., "Total Sales this Month"). This leaves management with several unanswered questions:
The "Discount" Blind Spot: Raw sales figures often ignore discounts, leading to an overestimation of actual cash flow and profit margins.
Lack of Context: Individual order values are meaningless without comparing them to "normal" customer behavior or company-wide benchmarks. Is a $500 order good for a specific client, or is it a sign they are spending less than usual?
Data Density: Large categories make it difficult to identify which specific products are driving the most growth and which are underperforming.
2. The Solution
The project implemented a series of SQL-based analytical views designed to provide a "Net Revenue" perspective and identify outliers. Key solutions include:
Net Revenue Calculation: Modernizing the revenue logic to apply the formula $(Price \times Quantity) \times (1 - Discount)$ across all metrics.
Behavioral Flagging: A dynamic system to automatically categorize orders as "Above Average" or "Below Average" based on the specific historical spending of that customer.
Category Leaderboards: Utilizing window functions to isolate the Top 3 products in every category by revenue, allowing for immediate focus on high-impact inventory.
3. How the Solution was Solved
The analysis was executed using PostgreSQL within a Jupyter Notebook environment, utilizing several advanced SQL techniques:
Common Table Expressions (CTEs): Used to chain complex logic together, such as calculating product totals before applying ranking functions.
Window Functions: * SUM() OVER(ORDER BY month): Created running totals to track cumulative growth over time.
AVG() OVER(PARTITION BY customer_id): Created a localized baseline for each customer.
ROW_NUMBER(): Assigned ranks to products within categories to handle the "Top N" problem.
Conditional Logic: Employed CASE WHEN statements to transform numerical comparisons into readable status labels (e.g., "Above Average").
PostgreSQL Casting: Used ::numeric and ROUND() to ensure financial precision and avoid integer division errors commonly found in SQL.
4. Biases and Limitations
While the current solution provides deep insights, there are several biases not yet handled:
Seasonality Bias: The "Average" metrics treat all months equally. A customer who spends more in December (due to holidays) might be flagged as "Above Average" even if their behavior is normal for that specific season.
Outlier Weighting: The global average calculation is highly sensitive to a few "Whale" customers with massive orders, which can make 90% of other customers look "Below Average" by comparison.
The "Tie" Bias: The ROW_NUMBER() function arbitrarily picks a winner when two products have the same revenue. In a strict tie for 3rd place, one product is unfairly excluded from the report.
Discount Depth: The analysis tracks net revenue but doesn't yet account for the cost of the discount strategy (e.g., whether a 20% discount actually drove enough volume to justify the loss in margin).
