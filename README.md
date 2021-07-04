# RDBMS

In relational database the relationship between the data files is relational. They are connected by a common key field. 

There are some properties which we need to follow in relational databses.
* It's values are Atomic
* In Each row is alone
* Column values are of same type
* Each column has a column name
* columns are undistinguished
* Sequence of Rows is Insignificant.

> 💡 When we store the data in databses, we need to sure that the data will be organised properly. So, we applu the concept of **Normalization**.

Normalization - Normalization is teh process of organising data to avoid duplication and redundancy.
* To minimize duplcicate data.
* To minimize or avoid data modification issues.
* To simplify queries.

Normalization rules are divided into following normal form.
1. First Normal Form String
2. Second Normal Form String
3. Third Normal Form String
4. Boyce and Codd Normal Form (BCNF)

----

## 1. First Normal Form

As per first normal form:

* Each set of column must have a **unique value**, such that multiple columns cannot be used to fetch the same row.
* Each table should be organized into two, and each row should have a **primary key.**

**Primary Key** - It is a key which help us to find a unique row in a table. Most of the time it is a single column, sometimes more than one column can be combined to create a primary key.

> 💡 We cannot put **Student** as the primary key as, 2 row cannot match each other. But we can concatenate 2 columns to make a primary key, and in this case we use **{Student, Course}** as a primary key.

|Student|Age|Course|    
|-------|---|------|
|Adam|15|CR001,CR005|
|Alex|14|CR005|
|Stuart|17|CR005|

|Student|Age|Course|    
|-------|---|------|
|Adam|15|CR001|
|Adam|15|CR005|
|Alex|14|CR005|
|Stuart|17|CR005|


> Using the first normal form, data redundancy increases, as there will be many columns with same data in multiple rows but each row as a whole will be unique.


----

## 2. Second Normal Form

As per second normal form:

* It should satisfy the **first normal form.**
* **No partial dependent** of any column on primary key ( column fully depend upon primary key )
* If column is **not part of primary key** then it must depend upon the entire concatenated key for its existence.
* If any column depends **only on one part of the concatenated key,** then the table *fails second normal form.*

> 💡 The age of student only depends on student column, which is incorrect as per second normal form. ( Student is partial primary key )


|Student|Age|
|-------|---|
|Adam|15|
|Adam|15|
|Alex|14|
|Stuart|17|

|Student|Course|    
|-------|------|
|Adam|CR001|
|Adam|CR005|
|Alex|CR005|
|Stuart|CR005|


> In Subject table the candidate key will be {Student, Course} column. Now both teh above tables qualifies for Second Normal Form and will never suffer from Update Anomalies.

-----

## 3. Third Normal Form

As per third normal form:

* It applies that every non-primary attribute should be dependent on one primary key. We can say that, there should not be 2 primary key in one table.

Example:

|Student_id|Student_name|DOB|Street|City|State|Zip|
|-|-|-|-|-|-|-|

> 💡 **Student_id** is the primary key in this case. But as we can see that the street, city and the state will be dependent on **Zip** as, it is failing in third normal form.

|Student_id|Student_name|DOB|Zip|
|-|-|-|-|

|Zip|Street|City|State|
|-|-|-|-|

<br>

> Now as we divid the table into 2 so we can make Student_id as the primary key in table1 and Zip in table2.


----

# Data Types in SQL

A data type is an attribute that specifies the type of data that the onject can hold.
* Integer data
* Character data
* Monetary data
* Date and time data
* Binary string, etc

## o Character String Data Type

|Data Type|Description|Use Case|
|-|-|-|
|char(n)|Stores *n* characters|
|nchar(n)|Stores *n* Unicode characters|stores non english words|
|varchar(n)|Stores approximately *n* characters|
|varchar(max)|Stores up to 231-1 characters|
|nvarchar(n)|Stores approximately *n* characters|stores non english words
|nvarchar(max)|Stores up to ((231-1)/2)-2 characters|

## o Numeric Data Type

|Data Type|
|-|
|int|
|tinyint|
|smallint|
|bigint|
|money|
|smallmoney|
|decimal(p,s)|
|numeric(p,s)|
|float(n)|
|real|

## o Date and Time Data Type

|Data Type|
|-|
|date|
|datetime|
|datetime2|
|datetimeoffset|
|smalldatetime|
|time|

## o Binary Data Type

|Data Type|
|-|
|bit|
|binary(n)|
|varbinary(n)|
|varbinary(max)|

# Basic SQL Statements

## DDL ( Data Definitions Language) Commands

Deal with database schemas and description of how the data should reside in the database.
- Create
- Alter
- Drop

## DML (Data Manipulation Language) Commands

Deals with data manipulation and includes most common SQL statements, and it is used to store, modify, retrieve, delete and update data in database.
- Select
- Insert
- Update
- Delete

## DCL (Data Control Language) Commands

Includes commands such as GRANT, and mostly concerned with rights, permissions and other controls of the database system.
- GRANT
- Revoke

## TCL (Transaction Control Language) Commands

Deals with transaction within a database.
- Commit
- Rollback
- Savepoint