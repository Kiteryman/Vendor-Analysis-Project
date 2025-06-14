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

**Phase 1: Data Engineering & Feature Creation (`Data Cleaning & Feature Engineering.ipynb`)**
This phase focused on building the foundational dataset for analysis. It involved connecting to the `inventory.db` SQLite database, aggregating data from multiple transactional tables (sales, purchases, inventory), and creating a unified `vendor_sales_summary` table. Key Performance Indicators (KPIs) were engineered to measure performance, including `GrossProfit`, `ProfitMargin`, `StockTurnover`, and `SalesPurchaseratio`.

**Phase 2: Statistical Analysis & Visualization (`Vendor Performance Analysis.ipynb`)**
Using the cleaned dataset, this phase focused on deriving insights. The analysis involved:
* **Exploratory Data Analysis:** Using histograms and boxplots to understand the distribution and characteristics of the key metrics.
* **Vendor Segmentation:** Classifying vendors into "Top-Performing" (top 25% by sales) and "Low-Performing" (bottom 25% by sales) to enable direct comparison.
* **Hypothesis Testing:** Applying a Two-Sample T-Test to statistically determine if there was a significant difference in profitability between these two groups.

---

### 3. Analysis and Key Findings

The analysis produced clear, data-driven findings, supported by both visualization and statistical validation.

#### Key Visualization: Comparative Profit Margin Boxplot

A key visual from the analysis is the boxplot comparing the `ProfitMargin` of Top-Selling vs. Low-Selling vendors. This plot immediately highlights a difference in performance between the two groups, showing that the top vendors not only sell more but also operate at a higher median profitability.

* **Top Vendors Mean Profit Margin:** 48.77%
* **Low Vendors Mean Profit Margin:** 41.55%

#### Statistical Validation

To formally verify the visual findings, a hypothesis test was conducted:

* **$H_{0}$ (Null Hypothesis):** There is no significant difference in profit margins between top and low-performing vendors.
* **$H_{1}$ (Alternative Hypothesis):** A significant difference exists in profit margins between the two vendor groups.

**Result:** The Two-Sample T-Test resulted in a p-value less than 0.05. Therefore, the **null hypothesis is rejected**.

**Conclusion:** The analysis confirms with statistical confidence that top-selling vendors have a significantly higher profit margin than low-selling vendors. This indicates that the two groups operate under distinctly different profitability models.

---

### 4. Final Recommendations

Based on the analysis, the following actionable recommendations are proposed to enhance profitability and operational efficiency:

* **Re-evaluate Pricing:** For low-sales, high-margin brands, re-evaluate pricing strategies to boost sales volume without sacrificing existing profitability.
* **Diversify Vendor Partnerships:** Reduce dependency on a few key suppliers to mitigate supply chain risks.
* **Leverage Bulk Purchasing:** Continue to leverage bulk purchasing advantages with top vendors to maintain competitive pricing and optimize inventory.
* **Optimize Slow-Moving Inventory:** For products with low turnover, adjust purchase quantities, launch targeted clearance sales, or revise storage strategies to reduce holding costs.
* **Enhance Marketing for Low-Performers:** Develop enhanced marketing and distribution strategies for low-performing vendors to drive higher sales volume.

By implementing these recommendations, the company can achieve sustainable profitability, mitigate risks, and enhance overall operational efficiency.
