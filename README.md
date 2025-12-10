# NYC Taxi Data Engineering Pipeline (ADF + Databricks + Delta Lake)

## 📌 Overview
This project is a full end-to-end data engineering pipeline built on Azure.  
It dynamically fetches NYC Taxi data through an HTTP API, processes it using Databricks (Bronze → Silver → Gold layers), stores curated data in Delta Lake, runs SQL analytics on top of Delta tables, and visualizes final outputs in Power BI.

---

## 🚀 Features
- **Dynamic data ingestion using Azure Data Factory (HTTP API connector)**
- **Multi-layered data lake architecture:**
  - Bronze (Raw ingestion)
  - Silver (Cleansed & standardized)
  - Gold (Aggregated & analytics-ready)
- **PySpark transformations for large-scale processing**
- **Delta Lake for:**
  - Time travel  
  - ACID transactions  
  - Schema evolution  
  - High-performance storage  
- **SQL analytics executed directly on Delta tables**
- **Power BI integration for final visualizations**
- **Parameter-driven orchestration for monthly/weekly loads**

---

## 🏗️ Architecture

### 🔹 **Azure Data Factory (Ingestion Layer)**
- Fetches NYC taxi trip data using an HTTP API  
- Stores raw ingested data into Azure Data Lake (Bronze)  
- Supports scheduled + on-demand trigger patterns  

### 🔹 **Azure Databricks (Processing Layer)**
**Bronze Layer**
- Stores raw API response  
- Enforces schema & file format normalization  

**Silver Layer**
- Cleans missing values  
- Standardizes timestamps, geolocation fields, and trip attributes  
- Removes duplicates  
- Applies business logic & derived fields  

**Gold Layer**
- Aggregations for analysis  
- Trip distance metrics  
- Fare analysis  
- Passenger count insights  
- Stores curated Delta tables with time-travel enabled  

### 🔹 **Delta Lake (Storage Layer)**
- Optimized storage for analytics  
- Time travel for versioned datasets  
- Z-Ordering & OPTIMIZE operations for performance  

### 🔹 **Power BI (Analytics Layer)**
- Connected directly to Gold Delta tables  
- Visual dashboards for trip statistics, peak hours, revenue patterns, etc.

---

## ⚙️ Tech Stack
- **Azure Data Factory**
- **Azure Databricks**
- **PySpark**
- **Delta Lake**
- **Azure Data Lake Storage**
- **Power BI**
- **SQL (Databricks SQL / Spark SQL)**

---

## 🔄 Pipeline Workflow
1. **ADF** calls HTTP API to fetch fresh NYC taxi data.  
2. Raw data is saved to **Bronze** layer in ADLS.  
3. Databricks transforms Bronze → Silver (clean data).  
4. Databricks further refines Silver → Gold (analytics-ready).  
5. Gold data is stored in **Delta tables** with time-travel features.  
6. SQL analytics run on Gold tables.  
7. Power BI consumes curated Delta tables for dashboards.  

---

## 🧪 Example SQL Queries Executed
- Top pickup locations  
- Average trip duration  
- Revenue per payment type  
- Peak hour traffic analysis  
- Fare distribution per borough  

---

## 📊 Sample Visualizations (Power BI)
- Hourly ride demand  
- Revenue heatmaps  
- Pickup vs drop-off geospatial patterns  
- Passenger count distributions  
- Trip distance vs fare scatter plots  

---

## 🔧 How to Run the Project

### **1. Azure Data Factory**
- Import pipeline JSON (if included)  
- Configure Linked Services  
- Add API endpoint URL  
- Trigger pipeline  

### **2. Databricks Notebooks**
Run them in this order:
1. `01_ingestion_bronze`  
2. `02_transformation_silver`  
3. `03_curated_gold`  
4. `04_sql_queries`  

### **3. Power BI**
- Connect to Databricks SQL Endpoint  
- Import Gold tables  
- Build dashboards  

---

## 📈 Future Enhancements
- Add unit tests (pytest + Databricks)  
- Implement data quality checks with expectations  
- Incremental Processing (CDC / watermarking)  
- Add orchestration using Azure Data Factory Dataflows or Airflow  
- Deploy CI/CD pipeline using Azure DevOps  

---

