# 🛒 FMCG Retail Lakehouse ETL Pipeline

A end-to-end data engineering project built on **Databricks** that simulates a real-world FMCG industry scenario: a large retail company acquires a smaller one, and we build a unified data pipeline to consolidate data from both companies into a single **Lakehouse** using the **Medallion Architecture**.

---

## 📌 Project Overview

In the FMCG (Fast-Moving Consumer Goods) industry, mergers and acquisitions create complex data consolidation challenges. This project tackles that head-on by building a production-style ETL pipeline that:

- Ingests raw data from **2 separate retail companies**
- Consolidates it into a **unified Lakehouse** on Databricks
- Enforces **data quality** at every layer
- Enables **self-serve analytics** via Databricks Genie and BI dashboards


---

## 🏗️ Architecture
```
Raw Sources (Amazon S3)
        │
        ▼
┌───────────────┐
│  BRONZE Layer │  ← Raw ingestion, no transformations
└───────────────┘
        │
        ▼
┌───────────────┐
│  SILVER Layer │  ← Cleaned, standardized, deduplicated
└───────────────┘
        │
        ▼
┌───────────────┐
│   GOLD Layer  │  ← Aggregated, business-ready, analytics-optimized
└───────────────┘
        │
        ▼
  Databricks Genie / BI Dashboards
```

---

## 🧰 Tech Stack

| Technology | Purpose |
|---|---|
| **Databricks (Free Edition)** | Unified analytics platform |
| **Apache Spark** | Distributed data processing |
| **Python** | Pipeline logic and transformations |
| **SQL** | Data querying and transformations |
| **Amazon S3** | Cloud data storage (source + lakehouse) |
| **Medallion Architecture** | Layered data quality framework |
| **Databricks Genie** | Natural language self-serve analytics |

---

## 📂 Project Structure
```
fmcg-retail-lakehouse-etl/
│
├── 0_data/                                  # Source data for both companies
│   ├── 1_parent_company/
│   │   ├── full_load/                       # Full load data for parent company
│   │   └── incremental_load/               # Incremental load data for parent company
│   └── 2_child_company/
│       ├── full_load/                       # Full load data for child company
│       └── incremental_load/               # Incremental load data for child company
│
└── 1_codes/                                 # All pipeline notebooks
    ├── 1_setup/                             # Environment & catalog setup
    │   ├── dim_date_table_creation.ipynb    # Date dimension table creation
    │   ├── setup_catalog.ipynb             # Databricks catalog configuration
    │   └── utilities.ipynb                 # Shared utility functions
    │
    ├── 2_dimension_data_processing/         # Dimension table pipelines
    │   ├── 1_customers_data_processing.ipynb
    │   ├── 2_products_data_processing.ipynb
    │   └── 3_pricing_data_processing.ipynb
    │
    └── 3_fact_data_processing/              # Fact table pipelines
        ├── 1_full_load_fact.ipynb           # Full load for fact tables
        └── 2_incremental_load_fact.ipynb    # Incremental load for fact tables
```



---

## 📊 Data Layers Explained

### 🥉 Bronze — Raw Ingestion
- Data ingested as-is from both companies
- No transformations applied
- Full audit trail preserved
- Schema-on-read approach

### 🥈 Silver — Cleansed & Standardized
- Null handling and deduplication
- Schema harmonization across both companies
- Data type standardization
- Business rule validation

### 🥇 Gold — Analytics-Ready
- Aggregated KPIs and metrics
- Dimensional modeling (facts & dimensions)
- Optimized for BI tools and Databricks Genie queries

---

## 📈 Use Cases & Analytics

Once the Gold layer is populated, the following analytics are available:

- **Sales Performance** — Revenue trends by product, region, and time
- **Inventory Analysis** — Stock levels and turnover rates
- **Customer Segmentation** — Buying behavior across both companies
- **Post-Merger Comparison** — Side-by-side metrics before and after consolidation



---

## 🙌 Credits & Inspiration

This project was inspired by and built following the tutorial by **codebasics**.

- 📺 **Tutorial:** [(https://www.youtube.com/watch?v=U6ZUKWdfSLY)]

All credit for the original project concept and dataset goes to them. This repository is my personal implementation for learning and portfolio purposes.
