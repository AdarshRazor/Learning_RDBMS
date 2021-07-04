# DML (Data Manipulation Language)

Deals with data manipulation and includes most common SQL statements, and it is used to store, modify, retrieve, delete and update data in database.
- Insert
- Update
- Delete
- Select

<br>

## Insert Statement

Insert command is used to **Insert data / record** into the database table.
Inserting values for the specific columns in the table. ( Always include the columns which are not null ).

Earlier table:

|emp_id|**first_name**|**last_name**|salary|
|-|-|-|-|
|1|Random|Name|50000|
|2|John|Doe|45000|
|3|Sue|Taylor|55000|

<br>

```SQL
Insert Into table_name (column1, column2) Values (value1, value2);
```

```SQL
USE Test1

insert into emp (emp_id, first_name, last_name)
values (1, 'Random', 'Name');
```
> 💡 Order of naming convention and the value should be same. Otherwise it will throw an error as the data type might not match for the values.

<br>
Inserting the value from another table

<br>

```SQL
Insert into <table_name> (column_name)
(Select old_column_name from old_table_name);
```

```SQL
Use Test1

Insert into emp_new (new_empid, new_firstname, new_lastname)
(Select * from emp);

OR

Insert into emp_new (new_empid, new_firstname, new_lastname)
(Select * from emp Where emp_id > 5);   # can put condition

OR

Insert into emp_new (new_firstname, new_lastname)
(Select first_name, last_name from emp);
```
<br>

## Update Statements

Update statement **updates / modufy** the existing data in the tables. Using these statements we can update the value of a single column or multiple columns in a single statement.

Earlier table:

|emp_id|**first_name**|**last_name**|salary|
|-|-|-|-|
|1|Random|Name|50000|
|2|John|Doe|45000|
|3|Sue|Taylor|55000|

```SQL
UPDATE <table_name> Set <column_name> = <val> Where <condition>
```

> 💡 Without **where** clause all the rows will get update. While updating more than one column, the column must be seperated by comma operator. 

<br>

```SQL
Update emp set last_name = 'Name1' where emp_id=1;

OR

Update emp set first_name = 'Random2', last_name = 'Name2' where emp_id=1;
```