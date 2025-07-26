# 🚗 Car Sales Data Engineering Project (End-to-End) | Azure ADF + Databricks + Spark

This is a complete **end-to-end data engineering solution** built on the Azure cloud. It simulates a real-world car sales pipeline that processes structured data from a database and APIs, applies complex transformations in **Databricks using Spark**, and outputs the final results into a **Star Schema** for analytics.

---

## 🧰 Tools & Technologies Used

| Tool / Tech           | Purpose                                |
|-----------------------|----------------------------------------|
| 🏭 Azure Data Factory | Data orchestration & scheduling        |
| 🧠 Azure Databricks   | Spark-based data transformation        |
| ⚙️ Apache Spark       | Scalable processing of big data        |
| 📦 Azure Data Lake    | Layered data storage (Bronze → Gold)   |
| 🌐 REST API           | External data source integration       |
| ⭐ Star Schema        | Dimensional modeling for reporting     |
| 🐙 GitHub             | Version control and project showcase   |

---

## 📌 Project Highlights

✅ Ingests data from **SQL source + REST API**  
✅ Handles **initial and incremental loads**  
✅ Implements **Bronze, Silver, and Gold layers**  
✅ Built 4 **Dimension Tables** and 1 **Fact Table** using Spark  
✅ All logic handled within **Databricks notebooks**  
✅ Reusable **ADF pipelines** for orchestration  

---

## 🧱 Architecture Overview

![Main Pipeline Architecture](architecture/Main_Path.png.png)

This architecture follows the **medallion pattern**:

- **Bronze Layer**: Raw data ingestion
- **Silver Layer**: Cleaned and enriched datasets
- **Gold Layer**: Final star schema tables

---

## 📊 Star Schema Design

![Star Schema](architecture/Star_Schema.png)

### 🔹 Fact Table:
- `fact_sales`: Sales metrics such as revenue, units sold, etc.

### 🔸 Dimension Tables:
- `dim_model`  
- `dim_branch`  
- `dim_dealer`  
- `dim_date`

---

## 📂 Folder Structure

```bash
Car_Sales_Data_Engineering_Project_End_to_End/
├── architecture/              # Diagrams & execution screenshots
│   ├── Star_Schema.png
│   ├── Main_Path.png.png
│   ├── Bronze_Files_SS.png
│   ├── Silver_Files_SS.png
│   ├── Gold_files.png
│   ├── Cluster_Configuration.png
│   ├── Incremental_Pipeline.png
│   ├── Jobs_Execution.png
│   ├── Copy_pipeline.png
│   └── Fetching_FactTable.png
├── datasets/                  # Raw and incremental source data
│   ├── SalesData.csv
│   └── IncrementalSales.csv
├── pipeline/                  # ADF pipelines
│   ├── copy_data_pipeline/
│   │   ├── linked_services.json
│   │   └── datasets.json
│   └── incremental_pipeline/
│       ├── linked_services.json
│       └── datasets.json
├── databricks_notebook/      # Transformation logic
│   ├── silver_transformed_notebook.scala
│   ├── dimension_tables_data.scala
│   └── fact_table_data.scala
└── README.md
