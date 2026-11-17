# Enterprise E-Commerce Data Cleaning & RFM Customer Intelligence (1.06M+ Rows)

[01_nafezly_cover_thumbnail.png]

An end-to-end data engineering, data quality audit, exploratory data analysis (EDA), and RFM customer segmentation pipeline built on the [Online Retail II UCI Dataset on Kaggle](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci) ([UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/online+retail+II)).

## 1. Executive Summary & Business Impact

This project processes **1,067,371 raw transaction records** spanning **731 business days** (December 2009 – December 2011) across **43 countries** ([SentinelBI AI Study](https://www.researchgate.net/publication/414158081_Sentinelbi_AI_an_AI-Powered_Business_Intelligence_System_for_Revenue_Monitoring_and_Anomaly_Detection)), transforming messy commercial logs into an analysis-ready dataset of **779,425 verified customer transactions** across **5,878 unique customers**.

| KPI Metric | Verified Value | Analytical Scope |
| :--- | :--- | :--- |
| **Raw Transaction Rows** | `1,067,371` | 2-year transactional log across 8 attributes |
| **Clean Customer Rows** | `779,425` | Verified, deduplicated registered customer purchases |
| **Gross Product Revenue** | `£19,600,000` | Product line revenue prior to cancellations ([Case Study](https://www.rmportfolio.co.uk/case-studies/online-retail-ii.html)) |
| **Returns & Cancellations** | `-£1,460,000` | `7.4%` revenue leakage isolated into dedicated audit table |
| **Net Verified Revenue** | `£18,200,000` | Net commercial sales across `39,517` orders and `4,901` products |
| **Average Order Value (AOV)** | `£497.00` | With a `72.4%` repeat-customer purchase rate |

## 2. Data Quality Audit & Cleaning Funnel (Before vs. After)

[02_data_cleaning_audit_visual.png]

| Audit Stage / Anomaly Category | Record Count | Share of Raw Data | Engineering Action Taken |
| :--- | :--- | :--- | :--- |
| **1. Initial Raw Dataset** | `1,067,371` | `100.00%` | Standardized 8-column transactional schema |
| **2. Missing Customer IDs** | `243,007` | `22.77%` | Flagged as `GUEST` checkouts; isolated from longitudinal RFM spine |
| **3. Exact Duplicate Records** | `26,479` | `2.48%` | Removed identical duplicate invoice-item records |
| **4. Cancelled Orders & Negative Qty** | `10,624` | `1.00%` | Isolated `C`-prefixed cancellations into dedicated returns audit table |
| **5. Service Codes & Zero-Price** | `7,836` | `0.73%` | Filtered `POST`, `D`, `M`, `BANK CHARGES`, and invalid zero-price rows |
| **6. Final Clean Customer Spine** | `779,425` | `73.02%` | Exported clean dataset across `5,878` unique customers |

## 3. RFM Customer Segmentation & K-Means Clustering

[03_rfm_segmentation_dashboard.png]

| Customer Segment | Customers | Customer Share | Revenue Share | Avg Recency | Avg Frequency | Avg Spend | Strategic CRM Action |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Champions** | `1,738` | `29.6%` | `80.8%` | `38 days` | `15.0` | `£8,244` | VIP tier rewards & early seasonal access ([RFM Study](https://www.reddit.com/r/dataisbeautiful/comments/1vilinc/oc_i_analyzed_1_million_retail_transactions_296/)) |
| **Loyal Customers** | `1,781` | `30.3%` | `11.4%` | `69 days` | `8.8` | `£2,943` | Cross-category product bundling & volume incentives ([K-Means Study](https://www.researchgate.net/publication/408536455_SEGMENTASI_PELANGGAN_MENGGUNAKAN_METODE_RFM_DAN_K-MEANS_CLUSTERING_UNTUK_MENDUKUNG_STRATEGI_PEMASARAN_PADA_ONLINE_RETAIL)) |
| **At Risk** | `1,784` | `30.4%` | `6.8%` | `307 days` | `2.9` | `£777` | Win-back campaigns targeting `£829,843` recoverable spend |
| **Lost** | `575` | `9.8%` | `1.0%` | `548 days` | `1.0` | `£317` | Suppress paid retargeting to optimize ad ROI |

## 4. Repository Files

- `Online_Retail_II_Colab_Pipeline.ipynb` — Automated Google Colab / Jupyter notebook (`kagglehub` ingestion, audit, cleaning, RFM, cohort retention).
- `Online_Retail_II_Executive_Dashboard.xlsx` — Multi-sheet executive Excel dashboard with dynamic formulas and embedded charts.
- `01_nafezly_cover_thumbnail.png` — Executive project cover card.
- `02_data_cleaning_audit_visual.png` — Data cleaning funnel & gross-to-net revenue audit visual.
- `03_rfm_segmentation_dashboard.png` — RFM Pareto concentration & K-Means segmentation dashboard.
