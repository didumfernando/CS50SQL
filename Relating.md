# Relating
## Normalisation
In practical contexts, it would be impractical to have one table showcasing all the data as this could result in repeated data and data anomalies and redundancies when CRUD operations take place. Hence Normalisation needs to be performed on the database.

Normalisation: The process of splitting up data into different forms/ groups to present

## Data Redundancies & Anomalies
<img width="743" alt="Screenshot 2023-12-06 at 3 02 36 PM" src="https://github.com/didumfernando/CS50SQL/assets/118650079/36bdb668-ac5e-4873-b365-7adc873c37f6"> 

From this table Olga, the author is repeated, hence this results in data redundancies and anomalies which may occur when CRUD operations take place on the database.

### Data Redundancies
Data redundancy: keeping an duplicate/extra copy of data/information (in the same or different tables)

### Anomalies
Anomalies occur when CRUD operations take place on the database. There are three anomalies:
1. Insertion anomalies: Inability to insert data as there is missing information.
2. Deletion anomalies: Deletion of a piece of data might result in unintentional deletion of others --> data inconsistency --> affect data integrity.
3. Update anomalies: When an update is performed and some instances of update not changed --> data inconsistency --> affect data integrity.

## Relations
After performing normalisation different entities can have various relationships with each other. Three main relationships can be represented via an ER diagram using the crowfoot notation.
1. One-to-One
2. One-to-Many
3. Many-to-Many

### ER Diagrams tricks for 1-many or many-1
If there is a one-to-many or many-to-one the crow-foot should be attached to the table or entity with the ``foreign key.``

## Keys
All examples to explain __primary__, __secondary__, __foreign__, and __composite__ keys will refer to this example.
```
STUDENT (__NRIC__, Name, PhoneNumber, Address)
GRADE (__NRIC*__, __SubjectID*__, Grade)
SUBJECT (__SubjectID__, SubjectName)
```
__Primary key__: A unique identifier in a table or set 
- ``NRIC`` in STUDENT or ``NRIC & SubjectID`` in GRADE
- Represented by an underline in table schema/specification questions.

__Secondary key__: Candidate keys not used as primary keys
- ``PhoneNumber`` in STUDENT

__Foreign key__: Foreign keys are keys that refer to the primary key of another table (establish relationships between tables)
- ``NRIC`` in GRADE (foreign key) references (primary key) ``NRIC`` in STUDENT
- How to identify? : It is the common column --> whichever table does not reflect more info (foreign key) --> represented by ..... in schema/specification questions.

__Composite key__: Candidate key consisting of more than one attribute.
- ``NRIC`` & ``PhoneNumber`` in STUDENT which are the primary and secondary keys.

## Normalisation forms
1. UNF
2. 1NF
3. 2NF
4. 3NF

### UNF
- Repeating groups of attributes
- Nested tables
- Presence of duplicate rows
= Increases the size of the database, reducing efficiency

### 1NF (might have composite keys)
- No duplicate rows / presence of non-atomic values
- No nested tables
- No repeating groups

### 2NF
- 1NF + no partial key dependencies
- A partial key dependency is when a non-key depends on only part of a composite key
- To eliminate partial-key dependency, if one key depends on the part of the key remove all the keys and place it in another table with the partial-key dependency keeping the dependent partial key in the original table as well.

### 3NF
- 2NF + no non-key dependencies
- A non-key dependency is when a non-key is dependent on another non-key.
- To eliminate non-key dependency, take out the entire non-key dependent on another non-key and place it in another table keeping the dependent non-key in the original table as well.
