# Databricks Medallion Data Engineering Project

## Overview
This project demonstrates an end-to-end data engineering pipeline built in Databricks using Medallion Architecture (Bronze, Silver, Gold).

The pipeline ingests raw source data, applies transformations and data quality checks, and produces analytics-ready datasets for downstream reporting and analysis.

## Architecture
The project follows a Medallion Architecture pattern:

- Bronze Layer -> raw ingestion
- Silver Layer -> cleaned and validated data
- Gold Layer -> analytics-ready fact and dimension tables

## Technologies Used
- Databricks
- PySpark
- Delta Lake
- Auto Loader
- Unity Catalog

## Project Structure
```text
databricks-medallion-project/
│
├── notebooks/
│   ├── 00_common_dq_functions.ipynb
│   ├── 01_bronze_ingestion_autoloader.ipynb
│   ├── 02_silver_dimensions_joined_product.ipynb
│   ├── 03_silver_fact_events_dq.ipynb
│   ├── 04_silver_fact_qc_tests_dq.ipynb
│   └── 05_gold_two_facts_star_schema.ipynb
│
├── docs/
└── README.md
