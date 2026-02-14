# FMCG Post-Merger Data Consolidation using Databricks Lakehouse

## 📌 Project Overview
This project implements an **end-to-end data engineering pipeline** for a real-world **FMCG post-merger use case**, where a large retail company acquires a smaller one and needs to **consolidate data from both organizations into a unified analytics platform**.

The solution is built using a **Databricks Lakehouse architecture** with the **Medallion (Bronze–Silver–Gold) design pattern**, supporting **incremental processing, orchestration, and BI analytics**.

---

## 🏗️ Architecture Overview
The project follows a **Lakehouse architecture** implemented on Databricks, using **Amazon S3 + Delta Lake** for scalable storage and processing.

**Key architectural components:**
- Multi-source ingestion (Parent & Child company data)
- Medallion layers (Bronze, Silver, Gold)
- Delta Lake tables with ACID guarantees
- Unity Catalog for governance
- Databricks Jobs for orchestration
- BI dashboards and Genie for consumption

![Lakehouse Architecture](resources/project_architecture.png)

---

## 🧱 Medallion Architecture

### 🔹 Bronze Layer (Raw Data)
- Raw data ingested from Amazon S3
- Stores structured and semi-structured data as Delta tables
- Supports both **full loads and incremental loads**
- Acts as the immutable source of truth

### 🔹 Silver Layer (Cleansed & Enriched)
- Data cleansing, deduplication, and standardization
- Business logic applied using Spark transformations
- Dimension tables created (customers, products, pricing, dates)
- Ready for analytical joins

### 🔹 Gold Layer (Business-Ready Analytics)
- Aggregated fact tables and denormalized views
- Optimized for BI queries and reporting
- Unified post-merger analytics across both companies
- Directly consumed by dashboards and Genie

---

## 🔄 Data Processing & Orchestration
- Spark-based ETL pipelines built using **PySpark and SQL**
- Separate notebooks for:
  - Dimension processing
  - Fact processing
  - Full and incremental loads
- **Databricks Jobs** used for orchestration
- Tasks executed in dependency order (Dimensions → Facts)
- Pipelines scheduled to run **daily** for incremental updates

![Lakehouse Architecture](resources/orchestration.png)

---

## 📊 Analytics & BI
- Gold-layer Delta tables power an interactive **Databricks BI dashboard**
- Dashboard provides:
  - Revenue, quantity, and customer KPIs
  - Monthly revenue trends
  - Product and variant performance
  - Channel-wise revenue analysis
- Used to validate data quality and business usability

![Dashboard](2_dashboarding/fmcg_dashboard.png)

---

## 🛠️ Tech Stack
- Databricks
- Apache Spark (PySpark)
- Delta Lake
- Amazon S3
- Python
- SQL
- Medallion Architecture
- Databricks Jobs
- Databricks BI & Genie

## 🎯 Key Learnings
- Designing scalable **Lakehouse architectures**
- Implementing **incremental ETL pipelines**
- Applying **Medallion design patterns**
- Orchestrating production pipelines with **Databricks Jobs**
- Building analytics-ready **Gold layers**
- Connecting data engineering outputs to BI consumption

---

## 🚀 Future Enhancements
- Add data quality checks and validations
- Implement Slowly Changing Dimensions (SCD)
- Enable streaming ingestion
- Integrate monitoring and alerting
- Expand analytics use cases

---

## 📌 Conclusion
This project demonstrates a **production-style data engineering workflow** using Databricks — from ingestion and transformation to orchestration and analytics — closely resembling real enterprise FMCG data platforms.

