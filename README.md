# 🏡 Home Sales Project — SparkSQL & Big Data Optimization

This project explores home sales data using **PySpark** and **SparkSQL**. I completed it as part of a data engineering and analytics module, focusing on querying, caching, partitioning, and performance benchmarking within a big data context.

## ✅ Project Summary

Using PySpark, I analyzed a dataset of home sales to calculate various aggregated metrics and optimize query performance. Key tasks included:

- Creating temporary views for SQL-style analysis
- Writing multiple queries to extract insights from housing data
- Caching data in memory to reduce query times
- Partitioning large datasets by year for performance
- Comparing execution times with and without caching
- Writing and reading Parquet files

## 📁 Repository Contents

- `Home_Sales.ipynb` — Jupyter notebook containing all the code and answers
- `home_sales_revised.csv` — The source dataset, read from an AWS S3 bucket
- `home_sales_partitioned/` — Output Parquet files partitioned by `date_built` (if committed)

## 🔍 What I Did

### 1. Data Loading & Setup
- Loaded the dataset from S3 into a Spark DataFrame
- Registered a temporary view called `home_sales` for SparkSQL queries

### 2. Data Analysis with SQL
I answered the following questions using SparkSQL:

- **Q1:** What is the average price for a four-bedroom house sold each year?
- **Q2:** What is the average price of 3 bed / 3 bath homes per year built?
- **Q3:** What is the average price of 3 bed / 3 bath homes with 2 floors and ≥ 2,000 sqft per year?
- **Q4:** What is the average price per "view" rating for homes with an average price ≥ $350,000? (also measured query runtime)

### 3. Caching & Performance
- Cached the `home_sales` temporary view
- Verified it was cached using `spark.catalog.isCached()`
- Re-ran the Q4 query using cached data and measured performance improvements

### 4. Partitioning & Parquet
- Partitioned the DataFrame by `date_built` and saved it in Parquet format
- Loaded the partitioned data back into Spark
- Created a temp view for the Parquet data and re-ran the analysis

### 5. Cleanup
- Uncached the `home_sales` table
- Verified the table was no longer cached

## ⏱️ Performance Insights

Using `cacheTable()` reduced the runtime of repeated queries significantly. Partitioning by `date_built` also improves performance for queries scoped to specific years, illustrating key Spark optimization strategies.

## 💾 Technologies Used

- Python / PySpark
- SparkSQL
- Jupyter Notebook
- Parquet file format
- AWS S3 (data source)

## 🚀 Final Notes

This project reinforced my understanding of distributed computing and big data querying in Spark. It demonstrates how to blend SQL-style analysis with performance tuning techniques for efficient data workflows.

---

Feel free to fork this repo or use it as a reference if you're learning PySpark or optimizing large datasets. ✨
