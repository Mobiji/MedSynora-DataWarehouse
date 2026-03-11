# **MedSynora Data Warehouse**
### Project Overview

The MedSynora Data Warehouse project demonstrates the design and implementation of an end-to-end data warehousing solution for healthcare analytics.

The objective of the project is to transform raw operational healthcare data into a structured analytical data warehouse that supports business intelligence and data-driven decision making.

The system integrates data from multiple operational datasets, performs transformation and cleaning processes, and loads the results into a dimensional data warehouse model optimized for analytical queries.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Business Problem

Healthcare organizations generate large volumes of operational data that are often stored across multiple systems. This data is difficult to analyze directly for strategic decision-making.

This project addresses this challenge by:

- Integrating multiple healthcare datasets

- Cleaning and standardizing raw data

- Designing a dimensional data warehouse

- Enabling analytical insights for reporting and decision support

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### 🏗️ Project Architecture

<img width="821" height="491" alt="Data Architecture" src="https://github.com/user-attachments/assets/8d1d95c9-4d71-418b-bfbc-6cde4a0fff83" />

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Data Warehouse Design

The warehouse follows a **star schema** architecture.

**Fact Tables**

Contain measurable business metrics.

Example:

- Patient treatments

- Medical transactions

- Healthcare services

**Dimension Tables**

Provide descriptive attributes for analysis.

Examples:

- Patient dimension

- Doctor dimension

- Insurance dimension

- Room dimension

- Disease dimension 

This structure enables efficient analytical queries.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### ETL Pipeline

The ETL process consists of the following stages:

**1. Extract**

Raw healthcare datasets are imported into the bronze layer (staging environment).

**2. Transform**

Data cleaning and transformations are applied:

- Handling of missing values

- Standardizing categorical values

- Data normalization

- Data enrichment

**3. Load**

Cleaned data is loaded into the dimensional warehouse tables.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Repository Structure


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Technologies Used

- SQL

- MySQL

- Data Warehousing

- Dimensional Modeling

- ETL Pipelines

- Git & GitHub

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Key Skills Demonstrated

This project demonstrates the following data engineering and analytics skills:

- Data warehouse design

- Star schema modeling

- SQL data transformations

- ETL pipeline development

- Data cleaning and standardization

- Analytical data preparation

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Future Improvements

Possible future enhancements include:

- Integration with BI tools such as Tableau or Power BI

- Automated ETL pipelines

- Data quality monitoring

- Data warehouse performance optimization

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 🌟 Author

#### Djiby Amadou

I am a professional transitioning from a background in pharmaceutical manufacturing into the data field, with a focus on data analytics and data engineering.

Through hands-on projects such as the MedSynora Data Warehouse, I am developing practical skills in:

- Data Warehousing

- SQL & Data Transformation

- ETL Pipeline Development

- Data Modeling (Star Schema)

- Analytical Data Preparation

My goal is to leverage my industry experience in pharmaceutical manufacturing operations together with data engineering and analytics skills to build data-driven solutions that support business intelligence and operational decision-making.

**Career Focus**

- Data Analyst

- Data Engineer (long-term goal)

**☕ Connect With Me**

GitHub: https://github.com/Mobiji


LinkedIn:  [![LinkedIn](https://img.shields.io/badge/github-repo-blue?logo=github)](https://www.linkedin.com/in/djiby-amadou-b917a2231/)

https://img.shields.io/badge/github-repo-blue?logo=github

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/djiby-amadou-b917a2231/)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
