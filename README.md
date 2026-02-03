# HPDM206Z - Assessment 1

## Project Aim
The aim of this project is to use MySQL to create a relational database (assigned as Module1_Assessment1),  where specific information relating to hospitals, doctors, patients and prescriptions can be extracted using MySQL Queries. 

## Built With
+ OpenStack
+ MySQL
+ Git 
+ GitHub 

## Dataset

Within the database four tables were constructed: hospitals, doctors, patients and prescriptions. Information used to populate these tables were obtained from four pre-populated files: hospitals.csv, doctors.csv, patients.csv and prescriptions.csv.

|     File      |    Details    |   Table       |
| ------------- | ------------- | ------------- |
| hospitals.csv  |Contains records of hospitals, with details on hospital_id, name, address, size, type, accreditation_status| hospitals  |
| doctors.csv | Contains records of doctors, with details on person_id, name, date_of_birth, address, role, hospital_id  | doctors   |
| patients.csv  | Contains records of patients, with details on person_id, name, date_of_birth, address, role, doctor_id  | patients  |
| prescriptions.csv  | Contains records of prescriptions, with details on: prescription_id, patient_id, doctor_id, medication, prescription_date  | prescriptions  |


## Creating the Database

!!!INSERT ERD!!! 

Prior to constructing the database, an entity relationship diagram was created to outline the structure of the tables and illustrate the relationships that will be used to link them. Tables were created and populated using the skeleton MySQL codes below, with each table assigned the appropriate primary key to ensure unique record identification:


```SQL
CREATE TABLE `table_name`
(`column1` DATATYPE NOT NULL,
`column2` DATATYPE NOT NULL,
`column3` DATATYPE NOT NULL,
`column4` DATATYPE NOT NULL,
`column5` DATATYPE  NOT NULL,
`column6` DATATYPE NOT NULL,
PRIMARY KEY (`column_name`)
);

LOAD DATA LOCAL INFILE ‘filepath.csv’ 
INTO TABLE `table_name`
FIELDS TERMINATED BY ',’
OPTIONALLY ENCLOSED BY '"'
IGNORE 1 LINES
(`column1`, `column2`, `column3`, `column4`, `column5`, `column6`);
```

The relationships between the tables were then established usings constraints and foreign keys, as shown in the skeleton code used below:

```SQL
ALTER TABLE table_name
ADD CONSTRAINT fk_table_names
FOREIGN KEY (column_name)
REFERENCES reference_table(reference_column);
```
The full codes used for construction and linkage of the tables can be found in the *[Codes.txt](Codes.txt)* file.

## SQL Query Scripts

### Pseudocodes 
For each query, pseudocodes were initially constructed to guide the creation of the final codes. These pseudocodes depict the underlying algorithms used in code construction and can be found in the *[pseudocodes.txt](pseudocodes.txt)* file.

### Final MySQL Queries

The full codes for each MySQL Query can be found in *[Codes.txt](Codes.txt)* file.

<ins>**QUERY1:</ins> List of All Doctors at a Given Hospital**

Purpose: Returns a full list of the doctors based at a specified hospital.

Notes:
  -	The query uses ‘?’ as a placeholder for the hospital_id which is the primary key in the hospitals table
  -	Only  doctors linked to the specified hospital_id will be returned, with all columns from the doctors table included in the output.
  -	The hospital_id and hospital_name from the hospitals table are also included in the output to confirm the correct hospital has been filtered.

<ins>**QUERY2:</ins> All Prescriptions for a Patient, Ordered by Prescription Date**

Purpose: Returns a full list of prescriptions for a specified patient, ordered by ascending prescription date.

Notes:
-	The query uses ‘?’ as a placeholder for the patient_id (the foreign key referencing person_id in the patients table).
-	Only prescriptions linked to the specified patient_id will be returned, with all columns from the prescriptions table returned 
-	The person_id, name, date_of_birth and doctor_id from the patients table are also included in the output to confirm the correct patient has been filtered.

<ins>**QUERY3:</ins> All Prescriptions By Specified Doctor**

Purpose: Returns a full list of prescriptions prescribed by a specified doctor

Notes:
-	The query uses ‘?’ as a placeholder for the doctor_id (the foreign key referencing doctor_id in the doctors table)
-	Only prescriptions linked to the specified doctor_id will be returned, with all columns from prescriptions table included in the output
-	The person_id, name and hospital_id from the doctors table are also included in the output to confirm the correct doctor has been filtered.

<ins>**QUERY4:</ins> Add New Patient Registered with a Doctor**

Purpose: Adds a new patient to the database and links them with an existing doctor. 

Notes:
-	The query uses ‘?’ as placeholders for the following columns in the patients table: person_id, name, date_of_birth, address, role, doctor_id. Values must be inputted in correct order and format. 
-	The patients table uses doctor_id as a foreign key referencing to the personal_id in the doctors table. 
-	If entry has non-existent doctor_id, query will fail due to foreign key constraint.

!!!QUERY 5 PENDING!!!

<ins>**QUERY6:</ins> All Doctors in the Hospital with Largest Capacity**

Purpose: Lists all the doctors based at the hospital which has been identified to have the largest capacity (i.e. the hospital with the highest ‘size’ equating to highest number of beds)

Notes:
-	In this query, the hospital with the maximum number of beds (i.e. highest size) is identified. 
-	The doctors table and the hospitals table are joined, with hospital_id being the reference key. Only doctors based at the identified hospital will be returned, with all columns from the doctors table included in the output.
-	The hospital_name and hospital_id from the hospitals table are also included in the output to confirm that all listed doctors are based from the same hospital.
