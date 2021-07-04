# DDL ( Data Definitions Language)



Deal with database schemas and description of how the data should reside in the database.
- Create
- Alter
- Drop

<br>

## Create Database Objects



The **CREATE DATABASE** statement is ised to create a new SQL database.

```SQL
CREATE DATABASE <database_name>
```
```SQL
CREATE DATABASE Test1
```
<br>

## Create Table Statements



The **CREATE TABLES** statement is used to create a ew table in selected database.

```SQL
Use <database_name>

CREATE TABLE <table_name> (
    columnA datatype,
    columnB datatype
);
```
```SQL
Use Test1       # select the database before creating table

CREATE TABLE employee (
    emp_id INT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL
);
```
|emp_id|first_name|last_name|
|-|-|-|
<br>

## Alter Table Statements



Alter table is used to:
- Add, Delete, Modify columns from existing table
- Add/Drop constraints on an existing table

```SQL
ALTER TABLE <table_name> ADD <column_name> <datatype>
ALTER TABLE <table_name> DROP column <column_name>
ALTER TABLE <table_name> ALTER COLUMN <column_name> <datatype>
```
```SQL
ALTER TABLE employee ADD Age INT;
ALTER TABLE employee ADD Random INT;
ALTER TABLE employee DROP column Random;     #Delete the column
ALTER TABLE employee ALTER COLUMN emp_id Char(10);
```
<br>

## Drop Table Statements



The DROP TABLE Statement is used to drop a table from selected database.

```SQL
DROP TABLE <table_name>;
```
```SQL
DROP TABLE employee;    # delete the entire table
```
<br>

<br>

## Various Constraints



- Constraints rules on the table whenever rows are inserted, updated and deleted from the table.
- Define the constraints at column or table level.
- Constraints can be applied during creation of table or after table creation by using alter command.

|Constraints|Description|
|--|--|
|NOT NULL|Column must have some value|
|UNIQUE|Column must have unique value|
|PRIMARY KEY|Column or set of columns that uniquely identifies a row.|
|FOREIGN KEY|references a column(s) of a table|
|CHECK|Condition that must be satisfied by all the rows in a table.|


<br>

## Primary Key 

It is a key which help us to find a unique row in a table. Most of the time it is a single column, sometimes more than one column can be combined to create a primary key.

Here are the few ways to define primary key 

```SQL
CREATE TABLE emp(
    emp_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
);
```


If there are 2 primary key in a table then we can use the following way to define it.

```SQL
CREATE TABLE emp(
    emp_id INT NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    salary MONEY,
    CONSTRAINT emp_pk PRIMARY KEY (first_name, last_name)
);
```

|emp_id|**first_name**|**last_name**|salary|
|-|-|-|-|

<br>

To add the primary key after the cretion of table ( In case you missed to declare ).

```SQL
ALTER TABLE emp
ADD CONSTRAINT emp_pk PRIMARY KEY (emp_id);
```

<br>

## Foreign Key

It is a column that refers to the **primary key / unique key** of the other table. So it demonstrates relationship between tables and act as cross reference amon them.

> 💡 First we have to make the parent table from where we want to take the refernce of the foreign key.

Here is the way to define the foreign key. 

```SQL
CREATE TABLE product(
    prod_id INT PRIMARY KEY,
    prod_name VARCHAR(50) NOT NULL,
    category VARCHAR(25)
);

CREATE TABLE Orders(
    order_id INT PRIMARY KEY,
    prod_id1 INT NOT NULL,
    quality INT,

    CONSTRAINT fk_product_id
        FOREIGN KEY (prod_id1)          # FOREIGN KEY <current column>
        REFERENCES product (prod_id)    # REFERENCES <table_name> <column>
);
```
Or we can add the foreign key after creating the table.

```SQL
ALTER TABLE Orders
ADD CONSTRAINT fk_product_id
    FOREIGN KEY (prod_id1)        
    REFERENCES product (prod_id); 
```
<br>

> 💡 Now if you want to delete the **prod_id** from the table *product*. It will show an error, because that column is in use as foreign key in another table. 
<br>
There might be time where you need to delete the column then you can use the following command. This will delete the column from that particular table as well where it is defined.

<br>

```SQL
ON Delete Cascade
``` 