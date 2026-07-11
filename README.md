# Product Sales Analysis

End-to-end data analytics project covering SQL exploration, Python EDA, time series forecasting, and a Power BI dashboard — built to answer two core business questions:

>  **Which regions, categories, and time periods generate the highest profit margins?**  
>  **What is the projected revenue for Q1 2025?**

---

## Tech Stack

| Layer | Tools |
|-------|-------|
| Data storage & querying | SQLite · SQL |
| Analysis & visualization | Python · pandas · matplotlib · seaborn |
| Forecasting | Prophet |
| Dashboard | Power BI |
| Environment | Jupyter Notebook |

---

## Project Structure

```
product-sales-analysis/
├── notebooks/
│   ├── 01_sql_exploration.ipynb
│   ├── 02_python_eda.ipynb
│   └── 03_forecasting.ipynb
├── dashboard/
│   └── product_sales_dashboard.pbix
├── exports/
│   ├── sales_final.csv
│   ├── monthly_timeseries.csv
│   ├── forecast_q1_2025.csv
│   └── charts/
├── data/
│   └── (see dataset link below)
└── README.md
```

## Dataset

**Product Sales Dataset 2023–2024** — [Kaggle](https://www.kaggle.com/datasets/yashyennewar/product-sales-dataset-2023-2024)  
200,000 synthetic sales transactions across 4 regions and 4 product categories in the United States.

---

## Workflow

### Notebook 1 — SQL Exploration
The raw CSV was loaded into a SQLite database to simulate a real enterprise data environment where an analyst queries a database rather than receiving a flat file directly.

Exploration covered: row counts, unique orders, customers and products, date range validation, null checks, and a full catalogue of available categories, sub-categories and regions. Aggregate queries calculated global KPIs and year-over-year comparisons. Window functions (`RANK()`, `LAG()`) were used to rank regions by revenue within each year and calculate month-over-month revenue growth. Results were exported as CSV files for the next phase.

### Notebook 2 — Python EDA
Working from the cleaned exports, the analysis focused on understanding profit margin distribution, monthly seasonality, and performance by region and product.

Key steps: datetime parsing and feature extraction (year, month, year-month), IQR-based outlier detection on revenue, profit margin distribution by category, and a side-by-side monthly revenue comparison between 2023 and 2024. Top 10 products by revenue were identified with their corresponding profit margins.

### Notebook 3 — Forecasting
Monthly revenue was aggregated into a time series and modeled using Prophet with annual seasonality enabled. The model was trained on 24 months of historical data and projected revenue for Q1 2025 (January, February, March) with a 95% confidence interval. Component decomposition was used to separate trend from seasonality and interpret the model output.

---

## Key Findings

- **West** is the highest-revenue region across both years
- **Clothing & Apparel** delivers the strongest profit margin among all categories
- **Q4 seasonality is dominant** — revenue starts climbing in September and peaks in November, consistently in both 2023 and 2024. The last quarter significantly outperforms all others
- **February is the weakest month** of the year — confirmed by both the historical data and Prophet's seasonality decomposition
- **The Instant Pot** is the top-selling product by revenue
- **Q1 2025 forecast** projects higher revenue than the same period in prior years across all three months. January ($4.95M), February ($3.19M), March ($4.80M) — consistent with an upward trend identified in the second half of 2024

---

## Dashboard

Two-page Power BI dashboard built on the cleaned and forecasted data.

**Page 1 — Performance Analysis**  
General KPI's and Profit margin breakdown by region, category, and time period.

**Page 2 — Revenue Trend & Forecast**  
Full historical monthly revenue (2023–2024) alongside Q1 2025 predictions with confidence interval bounds. Includes a forecast data table with exact figures per month.


