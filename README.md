# amazon-review-data-pipeline
health and personal care data


# Amazon Review Data Pipeline

## Project Overview

This project is an end-to-end cloud-based Data Engineering pipeline built using Apache Airflow, PySpark, Docker, and AWS services.
The pipeline processes Amazon review data in JSON format, performs data transformation and quality checks using PySpark, stores optimized partitioned parquet files in Amazon S3, catalogs metadata using AWS Glue, queries data using Amazon Athena, and visualizes analytics using Amazon QuickSight.

---

# Architecture

```text
Amazon Review JSON Data
        ↓
PySpark Transformation
        ↓
Data Quality Checks
        ↓
Partitioned Parquet Files
        ↓
Amazon S3 Data Lake
        ↓
AWS Glue Catalog
        ↓
Amazon Athena Queries
        ↓
Amazon QuickSight Dashboard
        ↓
Apache Airflow Orchestration
```

---

# Tech Stack

* Apache Airflow
* Apache Spark (PySpark)
* Docker
* Amazon S3
* AWS Glue
* Amazon Athena
* PowerBI
* Python

---

# Features Implemented

## Data Extraction

* Processed Amazon review dataset in JSON format
* Used PySpark for distributed data processing

## Data Transformation

* Converted raw JSON data into structured parquet format
* Extracted partition columns:

  * year
  * month

## Data Quality Checks

Implemented validation checks for:

* Null values
* Invalid ratings
* Missing important columns
* Duplicate handling

## Partitioned Data Lake

Stored optimized partitioned parquet files in Amazon S3:

```text
parquet/
    year=YYYY/
        month=MM/
```

## AWS Glue Integration

* Used AWS Glue crawler for schema detection
* Created metadata catalog for Athena querying

## Athena Analytics

Performed analytical queries such as:

* Average rating per product
* Most active users
* Low-rated product analysis

## Dashboarding

Built interactive dashboards using PowerBI:

* Ratings distribution
* Product insights
* User activity analysis

## Workflow Orchestration

Used Apache Airflow DAGs to automate:

* Transformation
* Upload to S3
* Pipeline execution

---

# Project Structure

```text
amazon-review-data-pipeline/
│
├── dags/
│   └── amazon_review_pipeline.py
│
├── scripts/
│   ├── transform_reviews.py
│   ├── upload_to_s3.py
│
├── data/
│
├── docker-compose.yaml
├── Dockerfile
├── requirements.txt
├── README.md
│
└── screenshots/
```

---

# Airflow Pipeline Flow

```text
Transform Data
      ↓
Generate Partitioned Parquet
      ↓
Upload To Amazon S3
      ↓
Glue Catalog Update
      ↓
Athena Querying
      ↓
PowerBI Dashboard
```

---

# Sample Athena Queries

## Average Rating Per Product

```sql
SELECT asin,
       AVG(rating) AS avg_rating,
       COUNT(*) AS total_reviews
FROM amazon_reviews_parquet
GROUP BY asin;
```

## Most Active Users

```sql
SELECT user_id,
       COUNT(*) AS total_reviews
FROM amazon_reviews_parquet
GROUP BY user_id
ORDER BY total_reviews DESC
LIMIT 10;
```

---

# Dashboard Insights

The PowerBI dashboard provides:

* Product rating analysis
* Review distribution
* User engagement insights
* Interactive filters for year and month

---

# Key Learnings

Through this project, I gained hands-on experience with:

* Distributed data processing using PySpark
* Workflow orchestration using Airflow
* Cloud storage and partitioning strategies
* AWS analytics services
* Building production-style ETL pipelines
* Dashboarding and data visualization

---

# Author

Nikhileshwar
