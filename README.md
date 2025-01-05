# Car Rental Data Batch Ingestion with SCD2 Merge in Snowflake
## Overview

This project demonstrates a car rental data pipeline that ingests and processes data in batches. The pipeline uses **Slowly Changing Dimension (SCD2)** to merge customer data into a Snowflake data warehouse and transform data using **PySpark on GCP Dataproc**. The data pipeline is orchestrated with **Airflow**, and various static and dynamic dimension tables are maintained in **Snowflake**.

## Tech Stack

- **Python:** The primary programming language for data transformations and orchestrating workflows.
- **PySpark:** For big data processing and transformations.
- **GCP Dataproc:** Managed Apache Spark and Hadoop for running PySpark jobs at scale.
- **Airflow:** To schedule and manage workflows (DAGs).
- **Snowflake:** Cloud data warehouse for storing and managing data.
