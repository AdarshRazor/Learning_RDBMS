# DML (Data Manipulation Language)

Deals with data manipulation and includes most common SQL statements, and it is used to store, modify, retrieve, delete and update data in database.
- Insert
- Update
- Delete
- Select

<br>

## o Insert Statement

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
```
OR
```SQL
Insert into emp_new (new_empid, new_firstname, new_lastname)
(Select * from emp Where emp_id > 5);   # can put condition
```
OR
```SQL
Insert into emp_new (new_firstname, new_lastname)
(Select first_name, last_name from emp);
```
<br>

## o Update Statements

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
```
OR
```SQL
Update emp set first_name = 'Random2', last_name = 'Name2' where emp_id=1;
```

<br>

## o Delete Statements

Delete commands help to delte **rows / record** from database table. Delete statements can be executed with or without where conditions.

```SQL
Delete from <table_name> [where <condition>];
```
> 💡 Execution of delete commands without where condition will remove all the records / rows from the table.

<br>

```SQL
Delete from emp where emp_id=2;
```
|emp_id|**first_name**|**last_name**|salary|
|-|-|-|-|
|1|Random|Name|50000|
|3|Sue|Taylor|55000|

<br>

## o Select Statement

These statements help us to retrieve records from data table. Where condition is optional in select statements. Various operators can be used in where conditions for data retrieval.

For this we make a new table, which is as follows:

**Table Name: emp_new**

|dept_no|dept_name|LOC|
|-|-|-|
|10|accounts|Delhi|
|20|HR|Chennai|
|30|IT|Hyderabad|
|40|Marketing|Bangalore|

```SQL
Select <column_name> from <table_name> where <condition>;
```
```SQL
Select * from emp_new   # display the whole emp_new table

Select top(3) * from emp_new    # display the top 3 values

Select top(2) dept_no, dept_name from emp_new   # display dept_no and dept_name
```

<br>

## o Ordering Result

Display the specific column in ascending or descending order ( default is ascending order ).

```SQL
Select |distinct| <column_name> from <table_name> where <condition> order by <column_name> <asc|desc>
```