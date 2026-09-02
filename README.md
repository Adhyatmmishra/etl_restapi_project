# 🚀 End-to-End Data Engineering Pipeline using Azure Databricks

## 📌 Project Overview

This project demonstrates an end-to-end **data engineering pipeline** built using **Azure Databricks**, with data ingested from a **REST API** and processed through a three-layer **Medallion Architecture**.

The pipeline transforms raw, nested JSON data into structured, analytics-ready datasets and ultimately into a **Star Schema** consisting of fact and dimension tables.

### Architecture

```text
                    REST API
                       │
                       ▼
              ┌─────────────────┐
              │  Bronze Layer   │
              │   Raw JSON Data │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │  Silver Layer  │
              │ JSON Flattening │
              │   & Cleansing   │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │   Gold Layer    │
              │   Star Schema   │
              │ Fact + Dimension│
              └────────┬────────┘
                       │
                       ▼
                 Analytics / BI

       ADLS Gen2 + Delta Lake
       Databricks Workflows
```

## 🏗️ Medallion Architecture

### 🥉 Bronze Layer — Raw Data

The Bronze layer is responsible for ingesting data directly from the REST API.

**Key activities:**

* Connect to the REST API
* Retrieve JSON responses
* Preserve the original source structure
* Store raw data in Delta Lake
* Maintain the raw layer for traceability and reprocessing

**Storage:**
Azure Data Lake Storage Gen2 + Delta Lake

---

### 🥈 Silver Layer — Data Transformation

The Silver layer converts the raw JSON data into clean and structured datasets.

**Key activities:**

* Read Bronze Delta tables
* Parse nested JSON structures
* Flatten nested JSON objects and arrays
* Convert JSON data into tabular format
* Handle data types and schema
* Clean and standardize data
* Apply required transformations
* Store processed datasets as Delta tables

**Technology:**
PySpark / Databricks

---

### 🥇 Gold Layer — Data Modeling

The Gold layer contains business-ready data designed for analytics and reporting.

A **Star Schema** is implemented using:

* **Fact Tables** — transactional/measurable business data
* **Dimension Tables** — descriptive business attributes
* Surrogate/business keys where required
* Business-level transformations and aggregations

The resulting Gold tables are stored in **Delta Lake** on ADLS Gen2.

---

## ⚙️ Pipeline Orchestration

The complete pipeline is orchestrated using **Databricks Workflows**.

The workflow manages the execution sequence:

```text
REST API
   ↓
Bronze Ingestion
   ↓
Silver Transformation
   ↓
Gold Data Modeling
   ↓
Analytics Ready Data
```

Databricks Workflows are used to manage:

* Job dependencies
* Task execution
* Pipeline scheduling
* Sequential Bronze → Silver → Gold processing
* Automated pipeline execution

---

## ☁️ Data Storage

**Azure Data Lake Storage Gen2** is used as the underlying cloud storage platform.

All three layers use **Delta Lake** as the storage format:

```text
ADLS Gen2
│
├── Bronze
│   └── Delta Tables
│
├── Silver
│   └── Delta Tables
│
└── Gold
    └── Delta Tables
```

Using Delta Lake provides a reliable and structured storage layer for the data pipeline.

---

## 🛠️ Technology Stack

| Technology                 | Purpose                          |
| -------------------------- | -------------------------------- |
| **Azure Databricks**       | Data processing & engineering    |
| **PySpark**                | Data transformation              |
| **Python**                 | API integration & pipeline logic |
| **SQL**                    | Data transformation & querying   |
| **REST API**               | Source system                    |
| **ADLS Gen2**              | Cloud data storage               |
| **Delta Lake**             | Data storage format              |
| **Databricks Workflows**   | Pipeline orchestration           |
| **Medallion Architecture** | Data processing architecture     |
| **Star Schema**            | Gold-layer dimensional modeling  |
| **Git**                    | Source-code version control      |

```

## 🎯 Key Learning Outcomes

Through this project, I gained practical experience in:

* Building end-to-end data pipelines on **Azure Databricks**
* Integrating **REST APIs** with data engineering pipelines
* Processing complex and nested **JSON data**
* Flattening JSON into structured tabular datasets
* Implementing **Medallion Architecture**
* Working with **Delta Lake**
* Using **ADLS Gen2** for cloud data storage
* Designing **Star Schema** data models
* Creating fact and dimension tables
* Orchestrating pipelines using **Databricks Workflows**
* Managing data engineering code using **Git**

## 👨‍💻 Author

**Adhyatm Mishra**

This repository contains the complete implementation of the project, including the Databricks notebooks, transformation logic, and pipeline workflow configuration.
# api_data_pipeline
