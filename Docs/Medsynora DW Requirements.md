## **MEDSYNORA DATA WAREHOUSE**

Business Requirements, Goals & Acceptance Criteria
________________________________________

### **1. Executive Summary**

MedSynora operates a multi-department healthcare facility that provides inpatient and outpatient medical services. MedSynora seeks to design and implement a centralized Enterprise Data Warehouse (EDW) in MySQL to consolidate clinical and operational healthcare data currently stored across multiple flat-file sources. The objective is to enable reliable, scalable, and performant analytical reporting to support clinical decision-making, operational optimization, and executive oversight.
The Data Warehouse will serve as the **single source of truth** for historical healthcare analytics and will be optimized for BI and advanced analytical workloads.
________________________________________

### **2. Business Goals**

**2.1 Strategic Goals**

The Data Warehouse's initiative is to:
1.	Enable data-driven clinical and operational decisions
2.	Improve visibility into patient encounters, diagnoses, and services
3.	Support trend, seasonal, and historical analysis
4.	Reduce dependency on raw CSV-based analysis
5.	Establish a scalable foundation for future analytics and reporting
________________________________________

**2.2 Operational Goals**

  •	Standardize metrics and definitions across departments
  
  •	Improve reporting performance and usability
  
  •	Enable consistent time-based analysis
  
  •	Support self-service analytics for analysts and BI users
________________________________________

### **3. Project Scope**

**3.1 In-Scope**

•	Integration of all provided MedSynora CSV data sources

•	Design and implementation of a dimensional data warehouse

•	Creation of fact and dimension tables

•	Support for historical data analysis

•	Analytical reporting and dashboard enablement

**3.2 Out of Scope**

•	Real-time or streaming data ingestion
________________________________________

### **4. Stakeholders**

**4.1 Business Stakeholders**

•	Hospital Executive Management

•	Clinical Leadership

•	Department Heads

•	Finance and Operations Teams

**4.2 Technical Stakeholders**

•	Data Engineering Team

•	BI & Analytics Team

•	Data Science Team (future)
________________________________________

### **5. Business Processes Supported**

The Data Warehouse must support analytical insight across the following healthcare processes:
1.	Patient encounters and admissions
2.	Disease diagnosis and classification
3.	Chronic condition and allergy tracking
4.	Doctor assignment and workload
5.	Additional medical service utilization
6.	Time-based operational trends
________________________________________

### **6. Analytical Objectives & Key Questions**

The EDW must enable analysis to answer questions such as:

- Clinical & Patient Analytics

  •	Encounter volumes by disease, chronic condition, and allergy
  
  •	Average length of stay by diagnosis and department
  
  •	Disease prevalence and trend analysis

- Staffing & Resource Analytics
  
  •	Doctor workload distribution
  
  •	Encounters handled per specialty
  
  •	Staffing trends over time

- Service Utilization Analytics
  
  •	Frequency of additional services
  
  •	Service usage by disease and doctor
  
  •	High-utilization service identification

- Time-Based Analytics
  
  •	Daily, monthly, quarterly, and annual trends
  
  •	Seasonal disease patterns
  
  •	Growth and decline in operational metrics
________________________________________

### **7. Data Architecture Requirements**

**7.1 Data Modeling Approach**

•	The Data Warehouse must follow a dimensional (star schema) design

•	Fact tables must represent measurable business events

•	Dimension tables must provide descriptive context
________________________________________

**7.2 Grain Definition**

FactEncounter Grain Definition:
- One record per patient encounter
- This grain must be strictly enforced to ensure aggregation accuracy and metric consistency.
________________________________________

### **8. Functional Requirements**

**8.1 Fact Tables**

FactEncounter must:

-	Represent patient encounters

-	Contain foreign keys to all related dimensions

-	Include measurable metrics such as:

 - 	Encounter count
  
 - 	Length of stay
  
 - 	Severity indicators (if available)
________________________________________

**8.2 Dimension Tables**

- Required Dimensions
  •	Patient

  •	Doctor
  
  •	Disease
  
  •	Chronic Disease
  
  •	Allergy
  
  •	Additional Service
  
  •	Date

- Each dimension must:
  •	Use surrogate keys
  
  •	Support descriptive analytics
  
  •	Be conformed across all fact tables
________________________________________

**8.3 Bridge Tables**

- Bridge tables must:
  •	Resolve many-to-many relationships
  
  •	Prevent double counting
  
  •	Support correct aggregation logic

- Examples:
  •	Encounter–Doctor
  
  •	Encounter–Additional Service
________________________________________

### **9. Non-Functional Requirements**

**9.1 Performance**
•	Standard BI queries must return results within 5–10 seconds

•	The warehouse must support analytical workloads at scale

**9.2 Scalability**
•	The solution must support multi-year historical data

•	Schema design must allow addition of new dimensions and facts

**9.3 Data Refresh**
•	Daily batch refresh is required

•	Full and incremental loads must be supported

**9.4 Security & Privacy**
•	Patient data must be anonymized or masked

•	Access must be role-based where applicable
________________________________________


### **10. Data Quality & Governance Requirements**

The Data Warehouse must enforce:
•	Referential integrity across all tables

•	Valid date logic (e.g., admission date ≤ discharge date)

•	Deduplication of encounters

•	Standardized categorical values

•	Defined handling of null and missing values
________________________________________

### **11. Reporting & Analytics Enablement**

The EDW must support:
**a. Standard Analytical Outputs**
  •	Executive overview dashboards
  
  •	Clinical performance dashboards
  
  •	Doctor workload dashboards
  
  •	Service utilization dashboards
  
  •	Time-series trend analysis
  
**b. BI Tool Compatibility**

  •	SQL-based access
  
  •	Compatibility with Tableau, Power BI, or equivalent tools
________________________________________

### **12. Acceptance Criteria**

The Data Warehouse solution will be considered successfully delivered when:
1.	All source CSV data is integrated into the EDW
2.	Fact and dimension tables align with defined business processes
3.	Metrics are consistent across all reports
4.	Historical analysis across multiple years is possible
5.	BI dashboards can be built without referencing raw CSV files
6.	Query performance meets defined thresholds
7.	Data quality rules are enforced and validated
________________________________________

### **13. Success Metrics**
•	Reduction in time spent preparing analytical datasets

•	Increased consistency in reported metrics

•	Improved stakeholder confidence in data

•	Ability to answer business questions previously not feasible
________________________________________

### **14. Assumptions & Constraints**
•	Data is synthetic and used for analytical purposes only

•	The warehouse is analytical, not operational

•	Star schema is the preferred modeling approach

•	No real-time SLAs are required

