# Global Sales Executive Analytics 📊

## Overview
This Power BI project provides a comprehensive, interactive dashboard for tracking and analyzing global sales performance. The goal of this project was to transform raw transactional data into actionable insights for senior leadership, focusing on Year-over-Year (YoY) growth, regional market share, and top-tier customer performance.

![Dashboard Preview](./dashboard_preview.png)

## Business Questions Answered
* **Revenue Trends:** How is revenue trending month-over-month, and how does the current year compare to the previous year?
* **Product Performance:** Which product categories are driving the most revenue?
* **Geographic Impact:** What is the revenue distribution across different global markets (APAC, Europe, LATAM, etc.)?
* **Customer Concentration:** Who are the top 10 most valuable customers, and what is their total contribution to the bottom line?

## Data Modeling & Architecture
I built a robust Star Schema to ensure efficient querying and accurate time-intelligence calculations:
* Established a dedicated Dim_Date table marked as the official date table.
* Created active 1-to-many relationships between Dim_Date[Date] and Fact_Sales[OrderDate].
* Integrated a Python ETL script (ETL-Script.ipynb) for initial data cleaning and normalization.

![Data Model](./data_model.png)

## Key DAX Measures
To ensure dynamic and error-free calculations regardless of the filter context, I used safe division and explicit time-shifting functions.

**Year-over-Year Growth:**
YoY Growth = 
DIVIDE(
    [Total Revenue] - [Revenue LY], 
    [Revenue LY], 
    0
)

**Revenue Last Year (LY):**
Revenue LY = 
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR('Dim_Date'[Date])
)

## UI/UX Design & Features
* **Dark Mode Theme:** Designed a custom dark UI to reduce eye strain and make KPI colors "pop" for quick cognitive processing.
* **Conditional Formatting:** Applied dynamic Green/Red font rules to the YoY Growth KPI to instantly indicate performance momentum.
* **Interactive Slicers:** Integrated Year, Country, and Category filters to allow for deep-dive exploratory analysis.
* **Top N Filtering:** Restricted the customer table to a "Top 10" leaderboard using the Filter Pane to focus on high-impact accounts.
* **Modern UI Elements:** Implemented rounded corners (10px) and subtle borders across all visuals for a premium, application-like feel.

## Tools Used
* **Power BI Desktop:** Data Modeling, DAX, and Visualization.
* **Python (Pandas/Jupyter):** ETL and data cleaning.
* **GitHub:** Version control and technical documentation.
