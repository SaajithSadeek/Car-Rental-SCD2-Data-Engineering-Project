# Car Rental Data Batch Ingestion with SCD2 Merge in Snowflake
## Overview

This project demonstrates a car rental data pipeline that ingests and processes data in batches. The pipeline uses **Slowly Changing Dimension (SCD2)** to merge customer data into a Snowflake data warehouse and transform data using **PySpark on GCP Dataproc**. The data pipeline is orchestrated with **Airflow**, and various static and dynamic dimension tables are maintained in **Snowflake**.

## Tech Stack

- **Python:** The primary programming language for data transformations and orchestrating workflows.
- **PySpark:** For big data processing and transformations.
- **GCP Dataproc:** Managed Apache Spark and Hadoop for running PySpark jobs at scale.
- **GCP Composer(Airflow):** To schedule and manage workflows (DAGs).
- **Snowflake:** Cloud data warehouse for storing and managing data.

## Project Components

**1. Snowflake Static Tables:**
- location_dim: Stores the static data related to car rental locations.
- date_dim: Contains dates and time-related dimensions.
- car_dim: Stores static information about cars (e.g., make, model, year).

**2. Snowflake Dynamic Tables:**
- customer_dim: A Slowly Changing Dimension (SCD2) table that tracks customer information over time. SCD2 logic ensures that changes to customer records (e.g., address changes) are captured and historical data is preserved.
- rentals_fact: A fact table storing car rental transactions, linking to customer_dim, car_dim, and location_dim.

**3. PySpark Data Processing:**
- PySpark code is used to read the static dimensions (location_dim, date_dim, car_dim) and the fact table (rentals_fact) from Snowflake.
- Data is transformed and processed to ensure consistency and accuracy.
- The transformed data is then appended back into the rentals_fact table in Snowflake.

**4. Airflow DAG:**
- Airflow DAGs are used to automate the entire pipeline:
  - Read daily car rental and customer data from Google Cloud Storage buckets.
  - Perform the SCD2 merge on the customer_dim table in Snowflake.
  - Trigger PySpark jobs on GCP Dataproc cluster to process the data and load it into Snowflake.

## Data Pipeline Flow

**1. Extract:** Raw car rental and customer data is stored daily in Google Cloud Storage.

**2. Transform:**
- Data is loaded into Snowflake dimensions and fact tables.
- The customer_dim table uses SCD2 logic to ensure historical changes to customer information are captured.
- Data transformations are performed using **PySpark** to clean and structure the data for analytics.

**3. Load:** Transformed data is loaded back into Snowflake’s fact tables (rentals_fact).

## Usage

**1. Running the DAG:** Once everything is set up, you can manually trigger or schedule the DAG in Airflow to run automatically at specific intervals.

**2. Monitoring:** Monitor the status of the pipeline from the **Airflow UI** to check for any failures or bottlenecks.

**3.Querying Data:** After running the pipeline, the processed data will be available in **Snowflake** for further analysis.

