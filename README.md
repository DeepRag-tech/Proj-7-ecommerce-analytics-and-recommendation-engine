```markdown
# End-to-End E-commerce Analytics & Recommendation Engine

## 🔴 LIVE DASHBOARD

**[View the Interactive Dashboard on Looker Studio] https://lookerstudio.google.com/reporting/961c29a1-323c-4293-92ba-4d389eb3d9f1**

---

## 1. Project Objective
This project simulates a real-world data analytics scenario for an e-commerce company. The primary objective was to analyze a large, multi-table dataset to uncover actionable insights, answer key business questions, and build a functional data product. The final deliverable is a comprehensive 3-page interactive dashboard for executive and marketing teams, showcasing sales performance, customer behavior, and a live product recommendation tool.

---

## 2. Tech Stack
*   **Data Storage:** PostgreSQL (hosted on [Neon.tech](https://neon.tech/))
*   **Data Processing & Modeling:** Python (in Google Colab) with Pandas, SQLAlchemy, and Scikit-learn
*   **Data Visualization:** Google Looker Studio
*   **Version Control:** Git & GitHub

---

## 3. Project Journey & Methodology
This project followed the CRISP-DM framework, but also embraced the realities of technical challenges and environmental constraints, requiring a pragmatic approach to problem-solving.

### Phase 1: Business & Data Understanding
- **Objective:** Increase profitability by identifying top products, valuable customers, and cross-selling opportunities.
- **Dataset:** The "Brazilian E-commerce by Olist" dataset from Kaggle was used, which contains 9 separate CSV files mimicking a real production database.

### Phase 2: Data Preparation (ETL)
- An initial ETL pipeline was built in Python to extract data from the CSVs, clean and transform it (e.g., converting data types), and load it into a normalized schema in a cloud-based PostgreSQL database on Neon. This created a robust "single source of truth."

### Phase 3: SQL Analysis & Modeling
- **Complex SQL queries** were written to join the relational tables and derive key business metrics, including:
  - Top 10 best-selling product categories.
  - Top 5 highest-value customers by lifetime spend.
  - Market basket analysis to find products frequently purchased together.
  - Average time between a customer's first and second purchase (81 days).
- A **collaborative filtering recommendation model** was built using Scikit-learn's `NearestNeighbors`. The model was trained on a memory-efficient sparse matrix of user-item interactions to identify products with similar purchase patterns.

### Phase 4: Overcoming Deployment Challenges (A Real-World Scenario)
The final deployment phase presented significant, real-world technical challenges that required adapting the initial plan.

*   **The Initial Plan:** The original project blueprint was to connect a BI tool (Tableau) directly to the live PostgreSQL database for real-time visualization.

*   **Problem #1: BI Tool Limitations.** It was discovered that Tableau Public (the free version) does not support a direct connector to PostgreSQL. This required a pivot in visualization tools. **Looker Studio** was chosen as a robust, browser-based alternative.

*   **Problem #2: Google Colab Environment Failure.** The plan then shifted to exporting the final data from Colab directly to Google Sheets for use in Looker Studio. However, the Colab environment repeatedly failed with `TransportError` and `RefreshError`. This was not a code error, but a fatal issue with the virtual machine's ability to authenticate with other Google services.

*   **The Solution: A Manual, Foolproof Workaround.** Recognizing the unreliability of the environment, a pragmatic decision was made to bypass the problematic Colab-to-Sheets connection entirely.
    1.  The final, aggregated SQL queries were run directly in the Neon SQL editor.
    2.  The results for each of the three dashboard pages were downloaded as clean CSV files.
    3.  These CSV files were manually imported into separate tabs of a Google Sheet.

This manual data export, while not automated, was the most effective solution to guarantee project delivery and demonstrates a critical professional skill: **choosing a reliable, simple solution when a complex, automated one fails due to external factors.**

### Phase 5: Final Deployment
- A 3-page dashboard was built in Looker Studio, connecting to the manually prepared Google Sheet. The final report is fully interactive and includes:
  - An executive overview with KPIs and cross-filtering.
  - A customer deep dive with geographic and segmentation analysis.
  - A functional product recommendation explorer powered by the machine learning model.

---

## 4. Key Business Insights
*   **Top Performers:** `Health & Beauty` and `Bed, Bath & Table` are the most valuable product categories, presenting clear marketing opportunities.
*   **Repurchase Window:** With an **81-day average** between the first and second purchase, a targeted re-engagement campaign should be triggered around the 60-day mark.
*   **Customer Segmentation:** The scatter plot reveals two key high-value segments: one-time "big spenders" and multi-order "loyalists," requiring different marketing strategies.
*   **Cross-Selling Goldmine:** The strong purchasing link between `Furniture/Decor` and `Bed/Bath` items can be leveraged for product bundling and on-page recommendations.

---

## 5. Repository Structure
```
├── notebooks/
│   └── e-commerce_analytics.ipynb   # The main Google Colab notebook used for ETL and model building.
├── sql/
│   └── analysis_queries.sql         # A file containing the core SQL queries used for business analysis.
└── README.md                        # This project overview.
```
```
