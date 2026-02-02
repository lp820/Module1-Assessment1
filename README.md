# HPDM206Z - Assessment 1

## Project Aim
The aim of this project is to use mySQL to create a relational database (assigned as Module1_Assessment1),  where specific information relating to hospitals, doctors, patients and prescriptions can be extracted using SQL Queries. 

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

Prior to constructing the database, an entity relationship diagram was created to outline the structure of the tables and illustrate the relationships that will be used to link them. Tables were created and populated using the SQL codes below, with each table assigned the appropriate primary key to ensure unique record identification:


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

The relationships between the tables were then established usings constraints and foreign keys, as shown in the code used below:

```SQL
ALTER TABLE table_name
ADD CONSTRAINT fk_table_names
FOREIGN KEY (column_name)
REFERENCES reference_table(reference_column);
```

## SQL Query Scripts

### Pseudocodes --

### FInal SQL Query Scripts -- purpose!! 
