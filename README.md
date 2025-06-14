### **Project Title: Vendor Performance and Profitability Analysis**

#### **1. Project Overview**

This project provides a data-driven framework for evaluating vendor performance, moving beyond simple sales metrics to focus on true profitability. The analysis leverages an inventory database to engineer key performance indicators (KPIs) and employs statistical testing to deliver actionable insights. The core finding is that **top-selling vendors are, as a group, statistically more profitable than low-selling vendors**, providing a clear direction for procurement and partnership strategy.

The project is executed in two distinct phases, encapsulated in two Jupyter Notebooks:
* `EDA.ipynb`: Handles all data engineering, from raw database tables to a clean, feature-rich analytical dataset.
* `Vendor Performance Analysis.ipynb`: Conducts the statistical analysis, visualization, and hypothesis testing to derive the final conclusions.

---

#### **2. Business Objective**

The primary goal was to answer a critical business question: **"Are our highest-volume vendors also our most profitable?"** Many businesses evaluate vendors primarily on sales volume, but this can be misleading. A high-volume vendor might operate on thin margins, while a lower-volume partner could be highly profitable. This project was designed to:

* Create a robust, multi-faceted vendor scoring system using KPIs like profit margin and stock turnover.
* Statistically validate whether a significant relationship exists between sales volume and profitability.
* Provide a data-backed strategy for vendor management and selection.

---

#### **3. Methodology**

**Phase 1: Data Engineering & Feature Creation (`EDA.ipynb`)**

The initial phase focused on transforming raw transactional data into a usable format.

1.  **Data Aggregation:** The process began by connecting to the `inventory.db` SQLite database. Data from multiple tables (`sales`, `purchases`, `begin_inventory`, `end_inventory`) were aggregated to create a single, comprehensive summary table named `vendor_sales_summary`.
2.  **Feature Engineering:** To enable a deeper analysis, several crucial KPIs were calculated for each vendor:
    * `GrossProfit`: The absolute profit from sales.
    * `ProfitMargin`: The core metric, representing gross profit as a percentage of total sales revenue.
    * `StockTurnover`: The ratio of sales quantity to purchase quantity, measuring inventory efficiency.
    * `SalesPurchaseratio`: The ratio of sales dollars to purchase dollars.
3.  **Data Cleaning:** The resulting dataset was cleaned to handle inconsistencies and prepare it for the analysis phase.

**Phase 2: Statistical Analysis & Results (`Vendor Performance Analysis.ipynb`)**

This phase used the cleaned `vendor_sales_summary` table to extract insights.

1.  **Exploratory Visualization (Histograms & Boxplots):**
    * **Histograms** were used to visualize the distribution of the newly created KPIs. This allowed for an initial understanding of the data's shape and the presence of outliers.
    * A **Boxplot** of `ProfitMargin` was then generated to clearly visualize the median profitability, its spread across vendors, and to identify vendors with exceptionally high or low performance.

2.  **Hypothesis Testing:**
    * **Segmentation:** Vendors were segmented into two groups: "top-performing" (top 25% by `TotalSalesDollars`) and "low-performing" (bottom 25% by `TotalSalesDollars`).
    * **Hypothesis:** A formal hypothesis was established:
        * **Null Hypothesis (H₀):** There is no significant difference in profit margins between top and low-performing vendors.
    * **Statistical Test:** A **Two-Sample T-Test** was performed to compare the `ProfitMargin` means of the two groups.

---

#### **4. Results and Conclusion**

The Two-Sample T-Test yielded a statistically significant result. The p-value was below the standard threshold of 0.05, leading to a definitive conclusion.

**Finding:** The null hypothesis was **rejected**. The analysis demonstrates that there is a **statistically significant difference in profit margins between top-selling and low-selling vendors.**

**Interpretation:** This is a crucial business insight. It confirms that the vendors driving the highest sales revenue are not just volume players; they are also, as a group, generating higher profit margins for the business. The "80/20 rule" appears to hold true in this context, where a vital few vendors contribute disproportionately to overall profitability.

**Actionable Recommendation:**
Based on this result, the business should prioritize and strengthen its relationships with its top-selling vendors. This data-driven framework can be adopted for ongoing vendor evaluations, ensuring that future partnership and procurement decisions are optimized for maximum profitability.
