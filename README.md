#  Azure End-to-End Data Engineering Project

This repository contains an end-to-end Azure Data Engineering project that simulates a real-world batch data pipeline. It is built using **Azure-native services** and **open-source tools** to demonstrate a complete data workflow from ingestion to transformation and final reporting.

##  Tools & Services Used

- **Azure Data Factory (ADF)** – for orchestration and ETL pipelines  
- **Azure Data Lake Storage Gen2 (ADLS)** – storage with Medallion Architecture (Bronze, Silver, Gold)  
- **Azure SQL Database** – for storing raw data and maintaining watermark for incremental loads  
- **Azure Key Vault** – to securely manage secrets and service principal credentials  
- **Azure Active Directory (Azure AD)** – for secure authentication between services  
- **Azure Databricks** – for data cleaning, transformation, Delta Lake optimization  
- **Delta Lake** – for versioned, ACID-compliant data in the lakehouse  
- *(BASIC)* **Power BI** – for dashboard and final reporting layer

## 📌 Project Architecture Overview

                 ┌──────────────────────────────┐
                 │     Source System (CSV, API) │
                 └────────────┬─────────────────┘
                              │
                        (Batch Load via ADF)
                              │
             ┌────────────────▼─────────────────┐
             │     Azure Data Factory (ADF)     │
             │  - Lookup Activity (watermark)   │
             │  - Copy Data + Stored Procedure  │
             └────────────────┬─────────────────┘
                              │
                              ▼
               ┌────────────────────────────┐
               │  Azure SQL Staging Table   │
               │  (Temporary + Watermark)   │
               └────────────┬───────────────┘
                            │
                       Copy to ADLS (Bronze)
                            │
                            ▼
         ┌────────────────────────────────────────┐
         │  Azure Data Lake Gen2 (Bronze Layer)   │
         └────────────────┬───────────────────────┘
                          │
       (Clean & Transform using Azure Databricks)
                          ▼
         ┌────────────────────────────────────────┐
         │  Silver Layer (Filtered, Cleaned Data) │
         └────────────────┬───────────────────────┘
                          │
          (Business Logic & Aggregations)
                          ▼
         ┌──────────────────────────────────────┐
         │  Gold Layer (Aggregated Business Data)│
         └────────────────┬──────────────────────┘
                          │
                     (Optional)
                          ▼
               ┌─────────────────────────┐
               │  Power BI Dashboard     │
               │  (Reporting & Insights) │
               └─────────────────────────┘


