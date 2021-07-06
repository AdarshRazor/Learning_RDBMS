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
```
OR
```SQL
Update emp set first_name = 'Random2', last_name = 'Name2' where emp_id=1;
```

<br>

## Delete Statements

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

## Select Statement

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

Example Table:

|dept_no|dept_name|LOC|
|-|-|-|
|10|accounts|Delhi|
|20|HR|Chennai|
|30|IT|Hyderabad|
|40|Marketing|Bangalore|

```SQL
Select * from emp_new Order by dept_no desc

Select top(2) * from emp_new

Select top(2) * from emp_new Order by dept_no desc
```

## o Filtering: Logical Operators

### Logical Operators ( AND, OR and NOT )
Used in where conditions to join more than two queries. Used to combine the results of two or more conditions to produce single result.

- AND Logical Operator:

    Used to combine two conditions and it fetches the result which satisfy both the conditions.

    Example:

    |emp_id|**first_name**|**last_name**|salary|
    |-|-|-|-|
    |1|Random|Name|50000|
    |2|John|Doe|45000|
    |3|Sue|Taylor|55000|

    

    ```SQL
    Select first_name, last_name from emp where first_name="Random" and last_name="Name";
    ```
    |**first_name**|**last_name**|
    |-|-|
    |Random|Name|

    ```SQL
    Select first_name, last_name from emp where salary > 48000 and salary > 56000;
    ```

    |**first_name**|**last_name**|
    |-|-|
    |Random|Name|
    |Sue|Taylor|

<br>

- OR Logical Operator:

    OR Operators is ised to combine two or more confitions and it fetches the result with satisfy any one of the condition in OR statements

    Example:
    
    |emp_id|**first_name**|**last_name**|salary|
    |-|-|-|-|
    |1|Random|Name|50000|
    |2|John|Doe|45000|
    |3|Sue|Taylor|55000|

    ```SQL
    Select first_name, last_name from emp where first_name="Random" or last_name="Doe";
    ```

    |**first_name**|**last_name**|
    |-|-|
    |Random|Name|
    |John|Doe|

    <br>

- NOT Logical Operator:

    NOT Operator is used to negate the conditions and it fetches opposite of the result with satisfy the condition. It is used in combination with other keywords like NOT IN, NOT between etc.

    Example:
    
    |emp_id|**first_name**|**last_name**|salary|
    |-|-|-|-|
    |1|Random|Name|50000|
    |2|John|Doe|45000|
    |3|Sue|Taylor|55000|

    ```SQL
    Select first_name, last_name from emp where first_name not in ('Random','Sue');
    ```

    |**first_name**|**last_name**|
    |-|-|
    |John|Doe|

## o Filtering: Comparison Operator

Comparison operators (=, !=, <>, >=, <=, LIKE, BETWEEN, IN): Comparison operators are used in where condition to fetch results from table.

- Between Operator:

    The Between operator is used to search for values that are within a set of values.

    ```SQL
    Select first_name, emp_id, from emp where salary between 40000 and 46000;
    ```
    |emp_id|**first_name**|
    |-|-|
    |2|John|

<br>

- IN Operator:

    Fetches values from a set of literals. It is used to test whether or not a value is "in" the list of values provided after the keyword IN. 
    
    > 💡 The IN condition can be used with any data type in SQL.

    ```SQL
    Select first_name, emp_id from employee where salary in 50000;
    ```

    |emp_id|**first_name**|
    |-|-|
    |1|Random|

    <br>

- Comparison Operator: `>, =, <, >=`

    These are the same operator which we use in mathematics.
    Some of the example are as follows:

    ```SQL
    Select first_name, emp, salary from emp where salary > 50000;
    ```

    |emp_id|**first_name**|salary|
    |-|-|-|
    |1|Random|50000|
    |2|John|45000|
    |3|Sue|55000|

<br>

## o Comparison Operator: LIKE Condition

Like condition to person wild card searches of valid search string values. Seach conditions can contain etiher characters or numbers. `**%**` denotes zero or many characters. `**_**` denotes one character.

```SQL
Select emp_id, salary from emp where first_name like 'j%';
```
|emp_id|salary|
|-|-|
|2|45000|


```SQL
Select emp_id, salary from emp where first_name like 'Tay_ _ _';
```

|emp_id|salary|
|-|-|
|3|55000|

<br>

----
<br>

## Case Expression

Used as a type of **IF-THEN-ELSE** statement. `CASE` is used to provide if-then-else type of logic to SQL.

Example:
```SQL
CASE column_name
WHEN condition1 THEN result1
WHEN condition2 THEN result2
ELSE result
END
```

New table: 

|emp_id|**first_name**|**last_name**|LOC|
|-|-|-|-|
|1|Random|Name|Chennai|
|2|John|Doe|Delhi|
|3|Sue|Taylor|Bangalore|

```SQL
Select CASE (LOC)
WHEN 'Chennai' Then 'TamilNaud'
When 'Bangalore' Then 'Karnataka'
ELSE 'No Idea'
END
from emp
```

|(no column name)|
|-|
|TamilNadu|
|No Idea|
|Karnataka|