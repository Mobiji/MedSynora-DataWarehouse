**DATA DICTIONARY FOR THE GOLD LAYER**

**Overview**

- The gold layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of multiple fact and dimension tables for various business metrics.

**1. dim_allergy**

*8Content:** Stores the various allergy names that patients have. 

|     Column Name    |     Data Type      |     Description                                                  |
|--------------------|--------------------|------------------------------------------------------------------|
|     patient_id     |     varchar(20)    |     Contains keys that uniquely identifies each patient.         |
|     first_name     |     varchar(50)    |     Has patients’ first names.                                   |
|     last_name      |     varchar(50)    |     Has patients’ last names.                                    |
|     allergy        |     varchar(50)    |     Has names of the all the allergies that each patient has.    |


**2. dim_chronic_disease**

**Content:** Stores the various chronic disease names that patients have. 

|     Column Name        |     Data Type       |     Description                                                         |
|------------------------|---------------------|-------------------------------------------------------------------------|
|     patient_id         |     varchar(20)     |     Contains keys that uniquely identifies each patient.                |
|     first_name         |     varchar(50)     |     Has patients’ first names.                                          |
|     last_name          |     varchar(50)     |     Has patients’ last names.                                           |
|     chronic_disease    |     varchar(100)    |     Has names of the all the chronic diseases that each patient has.    |


**3. dim_disease**

**Content:** Stores the information about the diseases that are usually encountered at the medical centre.

|     Column Name            |     Data Type       |     Description                                          |
|----------------------------|---------------------|----------------------------------------------------------|
|     disease_id             |     integer         |     A unique key that identifies each disease.           |
|     admission_diagnosis    |     varchar(150)    |     Contains disease names.                              |
|     disease_type           |     varchar(50)     |     Type of the disease.                                 |
|     medical_unit           |     varchar(50)     |     The medical unit that addresses the disease.         |
|     disease_severity       |     integer         |     An integer depicting the severity of the disease.    |


**4. dim_doctor**

**Content:** Stores information on the doctors that serve at the medical centre.

|     Column Name         |     Data Type      |     Description                                                       |
|-------------------------|--------------------|-----------------------------------------------------------------------|
|     doctor_id           |     integer        |     A unique key that identifies a doctor.                            |
|     title               |     varchar(30)    |     Contains the title of the doctor. i.e. 'Surgeon Dr.' or ‘Prof’    |
|     first_name          |     varchar(50)    |     Has patients’ first names.                                        |
|     surname             |     varchar(50)    |     Has patients’ surnames.                                           |
|     nationality         |     varchar(30)    |     Contains the nationalities where each doctor comes from.          |
|     medical_unit        |     varchar(50)    |     Contains the medical unit to which a doctor belongs.              |
|     patients_treated    |     integer        |     Indicated the number of patients the doctor has attended to       |


**5. dim_encounter_additional_service**

**Content:** Stores information on the additional services that each patient received at the centre.

|     Column Name     |     Data Type      |     Description                                                               |
|---------------------|--------------------|-------------------------------------------------------------------------------|
|     encounter_id    |     integer        |     A unique identifier that represents a patient’s visit to the centre.      |
|     service_name    |     varchar(50)    |     Name of the additional service a patient received.                        |


**6. dim_insurance_details**

**Content:** Stores information on the different insurance packages that patients were covered with.

|     Column Name           |     Data Type       |     Description                                                                                                      |
|---------------------------|---------------------|----------------------------------------------------------------------------------------------------------------------|
|     insurance_id          |     integer         |     An id that uniquely represents an insurance package.                                                             |
|     Insurance_type        |     varchar(30)     |     Name of the insurance package.                                                                                   |
|     extent_of_coverage    |     Decimal(4,2)    |     A decimal representing how much the insurance package partially covers in terms of conditions (illnesses).       |
|     deductible            |     integer         |     An integer value that is deducted from patients that have subscribed to the package.                             |


**7. dim_insurance_packages**

**Content:** Stores information on the conditions that are partially covered by the various insurance packages.

|     Column Name                     |     Data Type       |     Description                                                                                                                                                          |
|-------------------------------------|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     conditions_partially_covered    |     varchar(200)    |     Name of the condition that is partially covered.                                                                                                                     |
|     basic                           |     varchar(50)     |     Low cardinality type column containing either ‘yes’, ‘no’ or ‘info absent’. It indicates whether or not the condition is being covered by the insurance type.        |
|     standard                        |     varchar(50)     |     Low cardinality type column containing either ‘yes’, ‘no’ or ‘info absent’. It indicates whether or not the condition is being covered by the insurance type.        |
|     premium                         |     varchar(50)     |     Low cardinality type column containing either ‘yes’, ‘no’ or ‘info absent’. It indicates whether or not the condition is being covered by the insurance type.        |


**8. dim_patient**

**Content:** Stores personal information about the patients that visited the centre.

|     Column Name       |     Data Type      |     Description                                            |
|-----------------------|--------------------|------------------------------------------------------------|
|     patient_id        |     varchar(20)    |     A unique identifier for each patient.                  |
|     first_name        |     varchar(50)    |     Contains first names of the patients.                  |
|     last_name         |     varchar(50)    |     Contains last names of the patients.                   |
|     nationality       |     varchar(50)    |     Indicates the country which the patient comes from.    |
|     gender            |     varchar(20)    |     Low cardinality type column indicating the gender.     |
|     birth_date        |     date           |     Indicates the date which each patient was born.        |
|     weight            |     integer        |     Indicates how much a patient weighs in kilograms.      |
|     height            |     integer        |     Indicates how tall a patient is.                       |
|     marital_status    |     varchar(10)    |     Indicates the marital status of a patient              |
|     blood_type        |     varchar(10)    |     Indicates the blood group of a patient.                |


**9. dim_room**

**Content:** Stores information on the different rooms provided to the patients at the centre.

|     Column Name    |     Data Type      |     Description                                                                      |
|--------------------|--------------------|--------------------------------------------------------------------------------------|
|     room_id        |     integer        |     A unique identifier for a type of room.                                          |
|     care_level     |     varchar(30)    |     Indicates the level of care a patient receives while staying at the centre.      |
|     room_type      |     varchar(50)    |     Indicates the type of room a patient receives while staying at the centre.       |


**10. fact_cost**

**Content:** Stores information about the various costs patients incurred at the centre.

|     Column Name                     |     Data Type        |     Description                                                                                                    |
|-------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------------|
|     encounter_id                    |     integer          |     A unique identifier that represents a patient’s visit to the centre.                                           |
|     drug_cost                       |     decimal(9,0)     |     The cost for drugs that a patient incurred.                                                                    |
|     surgery_cost                    |     decimal(9,0)     |     The cost a patient incurred for surgery.                                                                       |
|     post_surgery_care_cost          |     decimal(9,0)     |     The cost a patient incurred for the post-surgery care they received.                                           |
|     education_rehab_cost            |     decimal(9,0)     |     The cost a patient incurred for receiving rehabilitation services.                                             |
|     psychological_support_cost      |     decimal(9,0)     |     The cost a patient incurred for psychological support.                                                         |
|     room_cost                       |     decimal(9,0)     |     The cost for the room that a patient stayed in.                                                                |
|     companion_accommodation_cost    |     decimal(9,0)     |     The cost a patient incurred due to having their companion stay with them during their stay at the centre.      |
|     nutrition_cost                  |     decimal(9,0)     |     The cost a patient incurred for nutrition.                                                                     |
|     radiology_cost                  |     decimal(9,0)     |     The cost that a patient incurred for radiology services.                                                       |
|     endoscopy_cost                  |     decimal(9,0)     |     The cost that a patient incurred for endoscopy services.                                                       |
|     cbc_cost                        |     decimal(9,0)     |     The cost that a patient incurred for the complete blood count test.                                            |
|     chem_cost                       |     decimal(9,0)     |     The cost that a patient incurred for the chemical tests.                                                       |
|     lipid_cost                      |     decimal(9,0)     |     The cost that a patient incurred for the lipids tests.                                                         |
|     additional_insurance_fees       |     decimal(9,0)     |     Additional cost a patient was charged by their insurance.                                                      |
|     total_cost                      |     decimal(22,0)    |     The sum cost for all the costs incurred                                                                        |
|     insurance_coverage              |     decimal(9,0)     |     The amount the insurance cover paid for the patient.                                                           |
|     out_of_pocket_cost              |     decimal(23,0)    |     The amount that a patient paid from their own pocket.                                                          |


**11. fact_encounter**

**Content:** Stores information about each encounter between a patient and the centre.

|     Column Name                  |     Data Type        |     Description                                                                          |
|----------------------------------|----------------------|------------------------------------------------------------------------------------------|
|     encounter_id                 |     integer          |     A unique identifier that represents a patient’s visit to the centre.                 |
|     patient_id                   |     varchar(30)      |     A unique identifier for each patient.                                                |
|     disease_id                   |     integer          |     A unique key that identifies each disease.                                           |
|     doctor_responsible_id        |     integer          |     A unique key that identifies a doctor.                                               |
|     insurance_id                 |     integer          |     An id that uniquely represents an insurance package.                                 |
|     room_id                      |     integer          |     A unique identifier for a type of room.                                              |
|     date_of_checkin              |     date             |     The date which a patient checked in to the centre.                                   |
|     time_of_checkin              |     time             |     The exact time when a patient checked in to the centre.                              |
|     date_of_checkout             |     date             |     The date which a patient checked out of the centre.                                  |
|     time_of_checkout             |     time             |     The exact time when a patient checked out of the centre.                             |
|     patient_severity_score       |     decimal(6, 2)    |     An integer that indicates how severe a patient was based on their illnesses.         |
|     radiology_type               |     varchar(30)      |     The type of radiology that a patient underwent.                                      |
|     radiology_procedure_count    |     Integer          |     The count of radiology procedures a patient underwent.                               |
|     endoscopy_type               |     varchar(50)      |     The type of endoscopy that a patient underwent.                                      |
|     endoscopy_procedure_count    |     integer          |     The count of endoscopy procedures a patient underwent.                               |
|     CompanionPresent             |     varchar(3)       |     Indicates if a patient had a companion present during their stay at the centre.      |


**12. fact_lab_tests**

**Content:** Stores information on the lab tests that were conducted on patients.

*(cbc)* – means ‘total blood count’ test

*(chem)* – means chemical test

*(lipids)* – means lipids test 

|     Column Name                        |     Data Type          |     Description                                                                                                                                                                                                            |
|----------------------------------------|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     encounter_id                       |     integer            |     A unique identifier that represents a patient’s visit to the centre.                                                                                                                                                   |
|     patient_id                         |     varchar(30)        |     A unique identifier for each patient.                                                                                                                                                                                  |
|     phase                              |     varchar(50)        |     The stage at which the test was conducted.                                                                                                                                                                             |
|     red_blood_cells_count              |     decimal(5,   2)    |     A decimal that expresses the number of red blood cells in millions per microliter of blood.                                                                                                                            |
|     hemoglobin_count                   |     decimal(5,   1)    |     A decimal that expresses the amount of hemoglobin protein in blood, expressed in grams per deciliter.                                                                                                                  |
|     hematocrit_count                   |     decimal(5,   1)    |     A decimal that expresses the percentage of red blood cells in a person's total blood volume                                                                                                                            |
|     haemoglobin_protein_count          |     decimal(5,   1)    |     A decimal that shows the average amount of hemoglobin in red blood cells (pg/cell), typically ranging from 27–33 pg                                                                                                    |
|     haemoglobin_concentration          |     decimal(5,   1)    |     A decimal that indicates the average concentration of hemoglobin inside the red blood cells.                                                                                                                           |
|     red_blood_cell_variation           |     decimal(5,   1)    |     A decimal that expresses the percentage of the variation in size and volume of red blood cells.                                                                                                                        |
|     platelets_count                    |     integer            |     An integer that shows the number of platelets in a microliter of blood. Expressed in thousands per microliter.                                                                                                         |
|     leukocytes_count                   |     decimal(5,   2)    |     A decimal that indicates the number of leukocytes in blood expressed in thousands per microliter.                                                                                                                      |
|     neutrophil_count                   |     decimal(5,   2)    |     A decimal that indicates of the number of neutrophil white blood cells in blood expressed in thousands per microliter.                                                                                                 |
|     lymphocytes_count                  |     decimal(5,   2)    |     A decimal that indicates the actual number of lymphocytes (a type of white blood cell) in a microliter of blood expressed in thousands per microliter.                                                                 |
|     monocytes_count                    |     decimal(5,   2)    |     A decimal that indicates the exact number of monocytes (a type of white blood cell) in blood expressed in thousands per microliter.                                                                                    |
|     eosinophils_count                  |     decimal(5,   2)    |     A decimal that indicates the number of eosinophils(a type of white blood cell) in blood expressed in thousands per microliter.                                                                                         |
|     basophils_count                    |     decimal(5,   2)    |     A decimal that indicates the specific number of white blood cells in a blood expressed in thousands per microliter.                                                                                                    |
|     blood_sugar_concentration          |     decimal(5,   1)    |     A decimal that indicates the concentration of sugar in blood express in milligrams per deciliter.                                                                                                                      |
|     urea_nitrogen_concentration        |     decimal(5,   1)    |     A decimal that indicates the amount of urea nitrogen in blood expressed milligrams per deciliter.                                                                                                                      |
|     creatinine_levels                  |     decimal(5,   2)    |     A decimal that indicates the level of creatinine, a waste product from muscle metabolism, in the blood (serum) or urine expressed milligrams per deciliter.                                                            |
|     kidney_filtering_capability        |     decimal(5,   2)    |     A decimal that indicates how well your kidneys are filtering waste products from blood expressed in milliliters per minute per an area of 1.73 meters squared.                                                         |
|     sodium_ions_count                  |     decimal(5,   1)    |     A decimal that indicates the amount of sodium (Na+) ions in blood expressed as milliequivalents per liter.                                                                                                             |
|     potassium_ions_count               |     decimal(5,   1)    |     A decimal that indicates the amount of potassium in the liquid portion (serum or plasma) of blood expressed as milliequivalents per liter.                                                                             |
|     chloride_ions_count                |     decimal(5,   1)    |     A decimal that indicates the level of chloride in the serum portion of blood expressed as milliequivalents per liter.                                                                                                  |
|     total_protein_amount               |     decimal(5,   2)    |     A decimal that indicates the total amount of albumin and globulins in blood expressed in grams per deciliter.                                                                                                          |
|     albumin_amount                     |     decimal(5,   2)    |     A decimal that indicates the main protein (albumin) produced by the liver expressed in grams per deciliter.                                                                                                            |
|     uric_acid_amount                   |     decimal(5,   2)    |     A decimal that indicates the amount of uric acid in the blood expressed in milligrams per deciliter.                                                                                                                   |
|     alanine_aminotransferase           |     decimal(5,   1)    |     A decimal that indicates the level of alanine aminotransferase enzyme in blood expressed in units per liter.                                                                                                           |
|     aspartate_aminotransferase         |     decimal(5,   1)    |     A decimal that indicates measures the amount of the enzyme Aspartate aminotransferase in blood expressed   in units per liter.                                                                                         |
|     alkaline_phosphatase               |     decimal(5,   1)    |     A decimal that indicates the amount of the enzyme Alkaline Phosphatase in blood expressed in units per liter.                                                                                                          |
|     gamma-glutamyl_transferase         |     decimal(5,   1)    |     A decimal that indicates the amount of the gamma-glutamyl transferase enzyme in blood expressed in units per liter.                                                                                                    |
|     bilirubin_amount                   |     decimal(5,   2)    |     A decimal that indicates the total amount of bilirubin in the bloodstream expressed in milligrams per deciliter.                                                                                                       |
|     cholesterol_amount                 |     decimal(5,   1)    |     A decimal that indicates the amount of cholesterol and triglycerides (fatty substances) in blood expressed in milligrams per deciliter.                                                                                |
|     low_density_lipoprotein_amount     |     decimal(5,   1)    |     A decimal that indicates fats (low-density lipoprotein) in blood expressed in milligrams per deciliter.                                                                                                                |
|     high_density_lipoprotein_amount    |     decimal(5,   1)    |     A decimal that indicates fats (high-density lipoprotein) in blood expressed in milligrams per deciliter.                                                                                                               |
|     triglycerides_amount               |     decimal(5,   1)    |     A decimal that indicates the amount of triglycerides in blood expressed in milligrams per deciliter.                                                                                                                   |
|     apolipoprotein_B-100_amount        |     decimal(5,   1)    |     A decimal that indicates the amount of a specific protein (Apolipoprotein B-100) in your blood that carries "bad" cholesterol (LDL, VLDL, and IDL) throughout your body expressed in milligrams per deciliter.         |
|     inflammation_levels                |     decimal(5,   1)    |     A decimal that indicates inflammation levels caused by infection, injury, or chronic diseases like arthritis expressed in milligrams per liter.                                                                        |


**13. fact_special_tests**

**Content:** Stores information on the special tests that were conducted on patients.

|     Column Name        |     Data Type           |     Description                                                                                                |
|------------------------|-------------------------|----------------------------------------------------------------------------------------------------------------|
|     encounter_id       |     integer             |     A unique identifier that represents a patient’s visit to the centre.                                       |
|     special_test_id    |     integer             |     A key that represents a special test phase.                                                                |
|     stage              |     varchar(30)         |     The stage at which the special tests were conducted on a patient. (i.e. at admission or at discharge)      |
|     test_name          |     varchar(150)        |     Name of the special test conducted.                                                                        |
|     result             |     decimal(10,   2)    |     An integer that indicates the result of the special test.                                                  |


**14. fact_treatment**

**Content:** Stores information on the treatments that patients received at the centre.

|     Column Name                |     Data Type       |     Description                                                                                            |
|--------------------------------|---------------------|------------------------------------------------------------------------------------------------------------|
|     encounter_id               |     integer         |     A unique identifier that represents a patient’s visit to the centre.                                   |
|     treatment_type             |     varchar(50)     |     The type of treatment that a patient received.                                                         |
|     treatment_name             |     varchar(100)    |     The name of the treatment that a patient received.                                                     |
|     follow_up                  |     varchar(100)    |     Indicates whether there was a follow up after the treatment.                                           |
|     complications              |     varchar(50)     |     Indicates if a patient had any complications post-treatment.                                           |
|     therapy_sessions           |     integer         |     An integer indicating the number of therapy sessions a patient went through.                           |
|     drug_boxes_used            |     integer         |     An integer indicating the number of drug boxes a patient received for their respective treatment.      |
|     hospital_drug_quantity     |     integer         |     An integer indicating the number of drugs that a patient used at the centre.                           |
|     discharge_drug_quantity    |     integer         |     An integer indicating the number of drugs a patient was prescribed with at discharge.                  |
|     total_drug_quantity        |     bigint          |     An integer indicating the total number of drugs a patient was prescribed with.                         |


**15. fact_vitals**

**Content:** Stores information on the vitals of patients.

|     Column Name                 |     Data Type        |     Description                                                                                     |
|---------------------------------|----------------------|-----------------------------------------------------------------------------------------------------|
|     encounter_id                |     integer          |     A unique identifier that represents a patient’s visit to the centre.                            |
|     patient_id                  |     varchar(20)      |     A unique identifier for each patient.                                                           |
|     stage                       |     varchar(40)      |     The stage at which the test was conducted.                                                      |
|     heart_rate                  |     decimal(4, 1)    |     A decimal indicating the heart rate of each patient in beats per minute.                        |
|     temperature                 |     decimal(4, 1)    |     A decimal indicating the body temperature of a patient in degrees Celsius.                      |
|     systolic_blood_pressure     |     integer          |     An integer indicating the systolic blood pressure of a patient in millimeters of mercury.       |
|     diastolic_blood_pressure    |     integer          |     An integer indicating the diastolic blood pressure of a patient in millimeters of mercury.      |
|     respiratory_rate            |     integer          |     An integer indicating the respiratory rate of a patient in breaths per minute.                  |
|     oxygen_saturation           |     decimal(4, 1)    |     A percentage indicating the concentration of oxygen in blood.                                   |
