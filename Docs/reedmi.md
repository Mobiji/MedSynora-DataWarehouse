# **MedSynora Data Warehouse**
### Project Overview

The MedSynora Data Warehouse project demonstrates the design and implementation of an end-to-end data warehousing solution for healthcare analytics.

The objective of the project is to transform raw operational healthcare data into a structured analytical data warehouse that supports business intelligence and data-driven decision making.

The system integrates data from multiple operational datasets, performs transformation and cleaning processes, and loads the results into a dimensional data warehouse model optimized for analytical queries.

### Business Problem

Healthcare organizations generate large volumes of operational data that are often stored across multiple systems. This data is difficult to analyze directly for strategic decision-making.

This project addresses this challenge by:

- Integrating multiple healthcare datasets

- Cleaning and standardizing raw data

- Designing a dimensional data warehouse

- Enabling analytical insights for reporting and decision support

<img width="821" height="491" alt="Data Architecture" src="https://github.com/user-attachments/assets/8d1d95c9-4d71-418b-bfbc-6cde4a0fff83" />

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

- Hospital dimension

- Date dimension

This structure enables efficient analytical queries.
