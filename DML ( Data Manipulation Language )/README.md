# DML (Data Manipulation Language)

Deals with data manipulation and includes most common SQL statements, and it is used to store, modify, retrieve, delete and update data in database.
- Select
- Insert
- Update
- Delete

<br>

## Insert Statement

Insert command is used to **Insert data / record** into the database table.
Inserting values for the specific columns in the table. ( Always include the columns which are not null ).

Earlier table:

|emp_id|**first_name**|**last_name**|salary|
|-|-|-|-|

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
