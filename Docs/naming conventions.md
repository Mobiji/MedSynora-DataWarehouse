## **MEDSYNORA DATAWAREHOUSE NAMING CONVENTIONS**

- This document outlines the naming conventions to be used for schemas, tables, views, columns, and other objects in the data warehouse.

## **Table of Contents**
1. General Principles
2. Table Naming Conventions
   - Bronze Rules
   - Silver Rules
   - Gold Rules
3. Column Naming Conventions
   - Surrogate Keys
   - Technical Columns
4. Stored Procedure

### **1. General Principles**
- Naming Conventions: Use snake_case, where an underscore separates 2 words with lowercase letters for all letters.
- Language: Use English for all names.
- Avoid Reserved Words: Do not use SQL reserved words as object names.

### **2. Table Naming Conventions**

*Bronze Rules*
- All names must start with the source system name, and table names must match their original names without renaming.
- <sourcesystem>_<entity> 
  - <sourcesystem>: Name of the source system (e.g., crm, erp).  
  - <entity>: Exact table name from the source system.  
  - Example: `erp_patients` → Patient information from the ERP system.

*Silver Rules*
- All names must start with the source system name, and table names must match their original names without renaming.
- <sourcesystem>_<entity>  
  	- <sourcesystem>: Name of the source system (e.g., crm, erp).  
  	- <entity>: Exact table name from the source system.  
  	- Example: `erp_patients` → Patient information from the ERP system.

*Gold Rules*
- All names must use meaningful, business-aligned names for tables, starting with the category prefix.
- <category>_<entity>
  - <category>: Describes the role of the table, such as `dim` for (dimension), `rep` for (report) or `fact` for (fact table).  
  - <entity>: Descriptive name of the table, aligned with the business domain (e.g., `patients`, `doctors`, `tests`).  
  - Examples:
    - `dim_patients` → Dimension table for patient data.  
    - `fact_tests` → Fact table containing tests record data.  

### **3. Column Naming Conventions**

*Surrogate Keys*

- All primary keys in dimension tables must use the suffix `_key`.
i.e. <table_name>_key
  - <table_name>: Refers to the name of the table or entity the key belongs to.  
  - `_key`: A suffix indicating that this column is a surrogate key.  
  - Example: `patient_key` → Surrogate key in the `dim_patients` table.

*Technical Columns (Metadata Columns)*
- All technical columns must start with the prefix `dwh_`, followed by a descriptive name indicating the column's purpose.
-i.e. dwh_<column_name>
  - `dwh_`: Prefix exclusively for system-generated metadata.  
  - <column_name>: Descriptive name indicating the column's purpose.  
  - Example: `dwh_load_date` → System-generated column used to store the date when a record is loaded.

*Other generated Columns (Other than metadata)*
All columns derived from the original data in a table shall have the prefix ‘der_’ followed by a descriptive name that indicated the column’s purpose.
i.e. der_CheckinTime
	‘der_’: Prefix exclusively for derived data columns
	 ‘CheckinTime’: Descriptive name indicating the column’s purpose.

### **4. Stored Procedure**
- All stored procedures used for creating tables must follow the naming pattern:
- `create_<layer>`
  - <layer>: Represents the layer being created, such as `bronze`, `silver`, or `gold`.
  - Example: 
    - `create_bronze` → Stored procedure for re-defining the Bronze layer.
    - `create_silver` → Stored procedure for re-defining the Silver layer.

- All stored procedures used for loading data must follow the naming pattern:
- `load_<layer>`
  - <layer>: Represents the layer being loaded, such as `bronze`, `silver`, or `gold`.
  - Example: 
    - `load_bronze` → Stored procedure for loading data into the Bronze layer.
    - `load_silver` → Stored procedure for loading data into the Silver layer.
