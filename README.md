```markdown
# My End-to-End E-commerce Analytics & Recommendation Engine Project

## 🔴 LIVE DASHBOARD

**I invite you to explore the final interactive dashboard I built in Looker Studio:**

**[View the Interactive Dashboard] https://lookerstudio.google.com/reporting/961c29a1-323c-4293-92ba-4d389eb3d9f1**

---

## 1. Project Objective

In this project, I took on the role of a Data Analyst for a fictional e-commerce company. My goal was to conduct a full-cycle analysis of their business operations, starting from raw, multi-table data and ending with a deployed, interactive dashboard that would provide actionable insights for the executive team.

I set out to answer these key business questions:
- What are our top-selling product categories?
- Who are our most valuable customers?
- Which products are our customers frequently buying together?
- What is the typical customer repurchase cycle?

---

## 2. My Tech Stack

*   **Data Storage:** PostgreSQL (hosted on [Neon.tech](https://neon.tech/))
*   **Data Processing & Modeling:** Python (in Google Colab) with Pandas, SQLAlchemy, and Scikit-learn
*   **Data Visualization:** Google Looker Studio
*   **Version Control:** Git & GitHub

---

## 3. The Project Journey: From Raw Data to Insights

I structured my workflow using the CRISP-DM framework, but the real story of this project is in adapting to the unexpected technical challenges I encountered along the way.

### Step 1: Data Preparation & ETL
My first step was to build a robust data foundation. I chose the "Brazilian E-commerce by Olist" dataset because its multi-file structure accurately mimics a real-world database.

Using Python in Google Colab, I built an ETL (Extract, Transform, Load) pipeline that:
1.  **Extracted** data from 9 separate CSV files.
2.  **Transformed** the data by cleaning it and, most critically, converting all text-based timestamps into proper `datetime` objects.
3.  **Loaded** the cleaned data into a cloud-based PostgreSQL database I provisioned on Neon, creating a normalized schema that served as my single source of truth.

### Step 2: Analysis & Modeling
With the data cleaned and structured, I connected to the database from my notebook.
- **SQL Analysis:** I wrote a series of complex SQL queries (using CTEs and Window Functions) to answer my initial business questions. You can see these queries in the `/sql` folder.
- **Machine Learning:** For the predictive component, I developed a collaborative filtering recommendation model using Scikit-learn's `NearestNeighbors`. I engineered a memory-efficient sparse matrix of user-item interactions to train the model, which proved essential for handling the dataset's size within the Colab environment.

### Step 3: Overcoming Real-World Deployment Challenges
This is where my project took a critical, real-world turn. My initial plan faced significant roadblocks, forcing me to pivot my strategy—a common experience in any data role.

*   **Initial Plan:** Connect a BI tool directly to the live PostgreSQL database for real-time visualization. I started with Tableau.
*   **Challenge #1: Tool Limitation.** I discovered that the free Tableau Public edition does not have a native connector for PostgreSQL. My initial choice of tool was incompatible with my database.
*   **Pivot #1: Change of Tools.** I adapted by moving to **Google Looker Studio**, a powerful and flexible browser-based alternative that I knew would meet the project's needs.

*   **New Plan:** Automate the export of my final datasets from Colab to Google Sheets to serve as the data source for Looker Studio.
*   **Challenge #2: Environment Failure.** This plan was consistently blocked by a critical `TransportError` and `RefreshError` from the Google Colab environment itself. After extensive troubleshooting, I concluded that this was not a bug in my code, but a fundamental authentication failure within the specific virtual machine assigned to my session.
*   **The Final Solution: A Pragmatic Workaround.** Rather than let the project fail due to an unreliable environment, I made a pragmatic decision to implement a manual but 100% reliable data export process.
    1.  I ran my final SQL queries directly in the Neon SQL Editor.
    2.  I downloaded the three required datasets as clean CSV files.
    3.  I manually uploaded these CSVs into a Google Sheet.

This workaround demonstrates a crucial professional skill: **when a complex, automated solution is failing due to external factors, the ability to implement a simpler, reliable solution to ensure project delivery is paramount.**

### Step 4: Final Dashboard Deployment
With the data successfully staged in Google Sheets, I built the final 3-page interactive dashboard in Looker Studio, which includes:
- An executive overview with cross-filtering capabilities.
- A customer deep dive with geographic and segmentation visuals.
- The fully functional Product Recommendation Explorer, powered by my machine learning model.

---

## 4. My Key Findings & Business Recommendations
Through my analysis, I uncovered several key insights:
*   **Top Performers:** The `Health & Beauty` and `Bed, Bath & Table` categories are the most valuable and should be a primary focus for marketing.
*   **Repurchase Window:** I calculated an **81-day average** between a customer's first and second purchase, giving the marketing team a precise window to launch re-engagement campaigns.
*   **Customer Segmentation:** The scatter plot I created clearly identifies two key high-value segments: high-spending, one-time buyers and loyal, repeat customers, each requiring a different marketing approach.
*   **Cross-Selling:** The strong purchasing link between `Furniture/Decor` and `Bed/Bath` items is a clear opportunity for creating product bundles and improving on-page recommendations.

---

## 5. Repository Structure
```
├── notebooks/
│   └── proj_7_E_commerce_Product_Recom...  # My primary Google Colab notebook.
├── sql/
│   └── analysis_queries.sql                # The core SQL queries for the project.
└── README.md                               # This project summary.
```

```
