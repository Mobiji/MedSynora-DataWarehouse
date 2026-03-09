** Data dictionary for the gold layer **

* Overview

The gold layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of multiple fact and dimension tables for various business metrics.


|     Column Name    |     Data Type      |     Description                                                  |
|--------------------|--------------------|------------------------------------------------------------------|
|     patient_id     |     varchar(20)    |     Contains keys that uniquely identifies each patient.         |
|     first_name     |     varchar(50)    |     Has patients’ first names.                                   |
|     last_name      |     varchar(50)    |     Has patients’ last names.                                    |
|     allergy        |     varchar(50)    |     Has names of the all the allergies that each patient has.    |
