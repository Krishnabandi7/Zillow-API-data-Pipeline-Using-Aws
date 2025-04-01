# Zillow-API-data-Pipeline-Using-Aws
Project Overview
This project focuses on developing a comprehensive data engineering pipeline to automate the extraction, transformation, and loading (ETL) of real estate data from Zillow. Utilizing AWS services such as IAM, S3, EC2, Lambda, and Redshift, along with Apache Airflow, the pipeline efficiently processes and stores data for analysis. To enhance insights, Amazon QuickSight was used to create interactive dashboards and visualizations, transforming raw data into actionable intelligence.
![Zillow-DE-Project](https://github.com/user-attachments/assets/f087f642-dec2-4205-a3a2-0018a058d9d4)
Architecture Overview
1. Data Extraction (Airflow + RapidAPI)
A Python script within Apache Airflow extracts real estate data from Zillow via RapidAPI.

Extracted data is stored in a raw data bucket in Amazon S3 for further processing.

2. Data Storage (AWS S3)
The raw JSON data is first stored in an S3 bucket.

A Lambda function (copyRawJsonFile-lambdaFunction) automatically copies the raw data to another S3 bucket, ensuring a backup and preparing it for the next processing stage.

3. Data Transformation (AWS Lambda + Pandas)
Another Lambda function (transformation-convert-to-csv-lambdaFunction) processes raw JSON data.

Using Pandas, the data is transformed into a structured CSV format and stored in a transformed data bucket in S3.

4. Data Loading (Airflow + Redshift)
Airflow’s S3KeySensor monitors the transformed data bucket for new CSV files.

Once detected, data is loaded into Amazon Redshift using S3ToRedshiftOperator.

A Zillow data table was created in Redshift for structured storage and analysis.

5. Data Visualization (Amazon QuickSight)
Amazon QuickSight was connected to Redshift to create interactive dashboards and visualizations.

These dashboards provide insights into real estate trends and market analytics.
![Data-to-warehouse](https://github.com/user-attachments/assets/d3ba7d9a-93f9-48a4-ab03-ca35f0563874)

Key Learning Outcomes:
Cloud Service Integration:
Integrated AWS services like IAM, S3, EC2, Lambda, Redshift, and QuickSight with Apache Airflow for a scalable and automated pipeline.
Data Transformation & ETL:
Gained hands-on experience in handling raw JSON data, performing data transformations using Pandas, and converting it into an analysis-ready format.
Orchestration with Apache Airflow:
Learned to orchestrate tasks, manage dependencies, and ensure smooth data flow using Airflow DAGs.
 Data Visualization & Insights:
Created interactive visualizations using Amazon QuickSight, helping to translate raw data into actionable insights.
Error Handling & Robustness:
Implemented S3KeySensor and Lambda functions to enhance the robustness and reliability of the pipeline
![DAG-view](https://github.com/user-attachments/assets/863af9da-92d9-403d-85f7-80df59758350)
![Data-to-warehouse (1)](https://github.com/user-attachments/assets/f0802db0-b685-471a-a51e-08697de7bcf4)
![Quicksights-analytics](https://github.com/user-attachments/assets/a788808a-0f18-4f17-b6e6-e60985697a32)

This project represents a full-scale implementation of an automated data engineering pipeline, from data extraction to visualization. By integrating multiple AWS services and modern data engineering practices, the project delivers a scalable and efficient solution for real estate data processing.
The addition of Amazon QuickSight further enhances the project, allowing for meaningful insights from data through interactive dashboards. The skills gained—ETL processes, cloud computing, data visualization, and workflow automation—are invaluable for tackling real-world data challenges.
