# Car Rental Data Batch Ingestion with SCD2 Merge in Snowflake
## Overview

This project demonstrates a car rental data pipeline that ingests and processes data in batches. The pipeline uses **Slowly Changing Dimension (SCD2)** to merge customer data into a Snowflake data warehouse and transform data using **PySpark on GCP Dataproc**. The data pipeline is orchestrated with **Airflow**, and various static and dynamic dimension tables are maintained in **Snowflake**.
