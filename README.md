# 🚀 Databricks Medallion Data Engineering Project

## 📌 Overview

This project demonstrates an **end-to-end data engineering pipeline** built using Databricks and Medallion Architecture (Bronze, Silver, Gold layers).

The pipeline ingests raw pharmaceutical manufacturing data, applies transformations and data quality checks, and produces **analytics-ready datasets** for reporting and decision-making.

---

## 🏗️ Architecture

The project follows a Medallion Architecture:

* **Bronze Layer →** Raw data ingestion using Auto Loader
* **Silver Layer →** Data cleaning, standardization, and validation
* **Gold Layer →** Business-ready fact and dimension tables

```text id="arch1"
Source Data → Bronze → Silver → Gold → Analytics
```

---

## ⚙️ Technologies Used

* Databricks
* PySpark
* Delta Lake
* Auto Loader (cloudFiles)
* Unity Catalog

---

## 📂 Project Structure

```text id="struct1"
databricks-medallion-project/
│
├── data/
│   ├── dim_product_master.csv
│   ├── dim_product_attributes.csv
│   ├── dim_site.csv
│   ├── dim_equipment.csv
│   ├── batch_header.csv
│   ├── fact_events_src.csv
│   └── fact_qc_tests_src.csv
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
```

---

## 🧱 Pipeline Design

### 🥉 Bronze Layer (Raw Ingestion)

* Ingests raw CSV files from the `data/` folder using Auto Loader
* Stores data in Delta format
* Captures ingestion metadata
* Maintains raw data without filtering

---

### 🥈 Silver Layer (Data Quality & Transformation)

* Cleans and standardizes data
* Removes duplicates
* Handles null values
* Applies data quality rules:

  * Not-null validation
  * Duplicate detection
  * Foreign key validation
  * Timestamp validation (no future dates)
* Writes invalid records to quarantine tables

---

### 🥇 Gold Layer (Analytics)

* Builds business-ready datasets
* Implements star-schema style design
* Includes:

  * Fact tables (events and QC tests)
  * Dimension tables (product, site, equipment)
* Supports downstream analytics and reporting

---

## ✅ Data Quality Framework

Reusable data quality functions implemented:

* `dq_not_null` → validates required fields
* `dq_dedup` → removes duplicate records
* `dq_timeliness_no_future` → validates timestamps
* `dq_fk_exists` → enforces referential integrity
* `dq_write_quarantine` → stores failed records

---

## 📊 Business Use Cases

* Pharmaceutical batch monitoring
* Quality control analysis
* Event tracking and deviation analysis
* Batch release decision support

---

## 🔥 Key Highlights

* End-to-end Medallion Architecture implementation
* Scalable ingestion using Auto Loader
* Modular and reusable data quality framework
* Quarantine handling for bad data
* Analytical modeling for reporting

---

## ⚠️ Limitations

* No visualization/dashboard layer included
* Uses batch processing (can be extended to streaming)

---

## 🚀 Future Enhancements

* Integrate with Power BI for reporting
* Add real-time streaming pipelines
* Implement CI/CD pipelines
* Deploy on Azure/AWS cloud environments

---

## 👤 Author

**Sai Krishna Reddy Kaithi**
LinkedIn: https://www.linkedin.com/in/sai-krishna-reddy-k-14008b27a/

This project is published for learning and portfolio purposes.
