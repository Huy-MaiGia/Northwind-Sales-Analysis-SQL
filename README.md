
📊 Northwind Traders: Advanced Sales & Behavioral Analytics
Unlocking strategic business insights through PostgreSQL and high-performance SQL engineering.

📋 Project Overview
This project presents a comprehensive technical analysis of the Northwind Traders database—a classic retail dataset representing a specialty foods export-import company. Moving beyond standard transactional reporting, this analysis utilizes advanced SQL techniques to solve complex business problems such as identifying the "Discount Blind Spot," establishing granular customer behavioral baselines, and ranking intra-category product performance with high precision.

🛠️ Tech Stack & Skills
Language: SQL (PostgreSQL)

Environment: Jupyter Notebook

Libraries: ipython-sql, psycopg2-binary, pandas

Core Competencies: CTE Nesting, Window Function Framing, Conditional Aggregation, and Financial Data Precision (Casting).

🎯 Strategic Analytical Solutions
1. The "Discount Blind Spot"
Standard revenue reports often ignore the cost of customer incentives, leading to skewed profit perceptions.

Implementation: Developed a standardized Net Revenue formula (Price×Quantity)×(1−Discount) applied across all performance metrics to reflect actual cash flow.

2. Behavioral Behavioral Baselines
Global averages fail to account for individual customer tiers. A "small" order for a VIP client may actually signal a risk of churn.

Implementation: Leveraged Window Function Partitioning to calculate localized averages for each customer. I engineered a dynamic flagging system to categorize orders as "Above" or "Below Average" relative to that specific customer’s historical spending patterns.

3. Intra-Category Competition Ranking
Identifying market leaders within diverse product niches is difficult in flat tables.

Implementation: Built a Top-N Ranking Model using ROW_NUMBER() partitioned by category_id. This isolates the top 3 revenue-driving products for every category, allowing for immediate inventory and marketing focus.

🏗️ Core Logic & Advanced SQL
The project showcases several sophisticated query structures:

Cumulative Growth Tracking: Used SUM() OVER(ORDER BY month) to generate running totals of monthly revenue, allowing stakeholders to visualize long-term momentum.

Performance Ranking: Utilized RANK() OVER(ORDER BY revenue DESC) to create definitive employee performance leaderboards based on total generated sales.

Precision Handling: Explicit use of ::numeric casting and ROUND() to ensure financial data remains accurate during complex divisions and aggregations.

⚠️ Critical Assessment (Analytical Boundaries)
A robust analysis acknowledges its own limitations. This model considers:

Seasonality Bias: Metrics currently treat all months equally, which may misrepresent holiday spending spikes as abnormal behavior.

Outlier Sensitivity: Global benchmarks are sensitive to high-volume "Whale" customers, which can make healthy mid-sized clients appear under-performing.

Ranking Logic: The use of ROW_NUMBER() arbitrarily breaks ties; a future iteration could implement DENSE_RANK() for more equitable competitive analysis.
