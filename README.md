# Vendor Performance and Profitability Analysis

### 1. Business Problem & Objectives

Effective inventory and sales management are critical for optimizing profitability. This project addresses the need to ensure the company is not incurring losses due to inefficient pricing, poor inventory turnover, or vendor dependency.

The primary objectives of this analysis are to:
* Identify underperforming brands that require promotional or pricing adjustments.
* Determine top vendors contributing to sales and gross profit.
* Analyze the impact of bulk purchasing on unit costs.
* Assess inventory turnover to reduce holding costs and improve efficiency.
* Investigate and statistically validate the profitability variance between high-performing and low-performing vendors.

---

### 2. Methodology

The project was executed in two main phases using two separate Jupyter Notebooks:

**Phase 1: Data Engineering & Feature Creation (`Vendor Performance Analysis.ipynb`)**
This phase focused on building the foundational dataset for analysis. It involved connecting to the `inventory.db` SQLite database, aggregating data from multiple transactional tables (sales, purchases, inventory), and creating a unified `vendor_sales_summary` table. Key Performance Indicators (KPIs) were engineered to measure performance, including `GrossProfit`, `ProfitMargin`, `StockTurnover`, and `SalesPurchaseratio`.

**Phase 2: Statistical Analysis & Visualization (`Vendor Performance Analysis.ipynb`)**
Using the cleaned dataset, this phase focused on deriving insights. The analysis involved:
* **Exploratory Data Analysis:** Using a correlation matrix, donut chart, and boxplots to understand relationships and distributions in the data.
* **Vendor Segmentation:** Classifying vendors into "Top-Performing" (top 25% by sales) and "Low-Performing" (bottom 25% by sales) to enable direct comparison.
* **Hypothesis Testing:** Applying a Two-Sample T-Test to statistically determine if there was a significant difference in profitability between these two groups.

---

### 3. Analysis and Key Findings

The analysis produced clear, data-driven findings, supported by multiple visualizations and statistical validation. This exploratory phase was crucial for building a comprehensive understanding before the final test.

#### Insight 1: Correlation Analysis (Correlation Matrix)
A correlation matrix was generated to quantify the relationships between key numerical variables.
* There was a very strong, positive correlation between `TotalSalesDollars` and `GrossProfit`, which is expected.
* More importantly, there was a **negative correlation between `TotalSalesDollars` and `ProfitMargin`**, suggesting increasing sales prices may lead to reduced margins, possibly due to competitive pricing pressures.

#### Insight 2: Sales Concentration (Donut Chart)
A donut chart visualizing the contribution of vendor segments to total sales revealed a significant concentration of revenue.
* The analysis showed that the **top 10 vendors are responsible for approximately 66% of the total purchase**. This visual powerfully over-reliance on a few 
vendors may introduce risks such as supply chain disruptions, indicating a need for diversification.

#### Insight 3: Profitability Comparison (Histogram)
A comparative histogram of `ProfitMargin` for Top-Selling vs. Low-Selling vendors provided a clear visual distinction in their performance.
* **Top Vendors Mean Profit Margin:** 31.17%
* **Low Vendors Mean Profit Margin:** 41.55%

#### Statistical Validation
The insights from the visualizations were formally validated with a hypothesis test:
* **$H_{0}$ (Null Hypothesis):** There is no significant difference in profit margins between top and low-performing vendors.
* **$H_{1}$ (Alternative Hypothesis):** A significant difference exists in profit margins between the two vendor groups.

**Result:** The Two-Sample T-Test resulted in a p-value less than 0.05. Therefore, the **null hypothesis is rejected**.

**Conclusion:** The analysis confirms with statistical confidence that top-selling vendors have a different profit margin than low-selling vendors.

---

### 4. Final Recommendations

Based on the analysis, the following actionable recommendations are proposed:
* **Re-evaluate Pricing:** For low-sales, high-margin brands, re-evaluate pricing strategies to boost sales volume.
* **Diversify Vendor Partnerships:** Reduce dependency on the few key suppliers identified in the sales concentration analysis to mitigate supply chain risks.
* **Leverage Bulk Purchasing:** Continue to leverage bulk purchasing advantages with top vendors.
* **Optimize Slow-Moving Inventory:** Adjust purchase quantities or launch clearance sales for products with low turnover.
* **Enhance Marketing for Low-Performers:** Develop targeted strategies for low-performing vendors to drive higher sales volumes.

---

### 5. Acknowledgments

This project and its methodology are inspired by the end-to-end data analytics project tutorial on Vendor Performance Analysis provided by **Tech Classes**. Their detailed guide served as a valuable reference for the project structure, analytical approach, and KPI selection.
