# Nicolas Chamorro Ferreira — Data Engineering Portfolio


---

## Projects

---

### 1. Foreign Exchange ETL Pipeline
**`/fx-etl-pipeline`**

A production-grade ETL pipeline that extracts foreign exchange rate data from the Bank of Canada API, applies financial transformations, and delivers analytics-ready data through a Medallion architecture.

**The problem:** Raw FX data from a public API needs to be cleaned, enriched with financial metrics, and made available for analytics.

**Tech stack:** Databricks, Delta Lake, PySpark, Python, Bank of Canada API

**Highlights:**
- Retry logic with exponential backoff for resilient API extraction
- Medallion architecture: Bronze (raw) → Silver (cleaned + enriched) → Gold (aggregated)
- Financial metrics: 3-day moving average, 7-day volatility, daily % change
- Data quality scoring framework with categorical classification (Excellent/Good/Fair/Poor)
- Processes USD/CAD, EUR/CAD, GBP/CAD currency pairs

---

### 2. SQL to PySpark Migration
**`/sql-to-pyspark-migration`**

Demonstrates advanced SQL-to-PySpark migration skills by converting complex T-SQL queries with `OUTER APPLY` operators into efficient PySpark code, maintaining identical business logic.

**The problem:** Legacy SQL Server queries using T-SQL-specific operators need to run on Databricks.

**Tech stack:** Databricks, PySpark, Delta Lake, Python

**Highlights:**
- `OUTER APPLY` → LEFT JOIN + Window Function pattern
- `TOP 1 WITH ORDER BY` → `row_number().over(Window)` + filter
- Complex conditional aggregations with time-based period comparisons
- Sales trend calculation with division-by-zero protection
- Fixed reference date implementation for reproducible results

---

### 3. FX Data Analysis & Visualizations
**`/fx-analysis`**

Comprehensive analysis of the foreign exchange data processed in the ETL pipeline, focusing on trends, volatility metrics, data quality, and cross-currency relationships.

**Tech stack:** Python, Pandas, NumPy, Matplotlib, Seaborn, PySpark

**Highlights:**
- FX rate trend visualization across all currency pairs
- Daily percentage change distribution analysis
- Rolling metrics: 3-day moving average + 7-day volatility
- Correlation matrix across currency pairs
- Data quality assessment with quality score visualization
- Executive summary with automated statistical reporting

---

### 4. AWS Serverless Architecture for Databricks Networking
**`/aws-serverless-networking`**

A serverless event-driven AWS architecture that manages Databricks cluster networking dynamically, significantly reducing cloud infrastructure costs.

**The problem:** Databricks clusters required NAT Gateways running 24/7 regardless of cluster activity, driving infrastructure costs significantly over budget.

**Tech stack:** AWS Lambda, Amazon EventBridge, NAT Gateways, Elastic IPs, EC2, Python (boto3)

 How to view: Clone or download this folder and open the .html file in your browser. The file includes diagrams and screenshots of the architecture and implementation.

**Highlights:**
- EventBridge rules listen for EC2 instance state changes from Databricks cluster nodes
- Lambda functions dynamically associate/disassociate Elastic IPs based on cluster state
- Eliminates idle NAT Gateway costs — networking resources only active when clusters are running
- Significant reduction in monthly AWS spend — solution adopted for multiple Databricks projects
- Fully event-driven — no polling, no scheduled jobs, zero idle compute

---
