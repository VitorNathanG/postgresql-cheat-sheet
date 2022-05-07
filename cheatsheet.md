# PSQL

    \l - lists all available databases

    \c \<database> - connects to a different database

    \d [pattern] - lists things in the current database that match the pattern

    \i path/to/file - execute commands from file

> Note on [pattern]: it's possible to use **\*** to match any number of characters, or **?** to match a singla character

# OPERATIONS

## Database Operations
```sql
CREATE DATABASE <database> - creates a database with the given name
DROP DATABASE <database> - deletes the database with the given name
```
## Table Operations

### Create table
```sql
CREATE TABLE <table> (
    [<column> <type> [constrains...],
    <column> <type> [constraints...] ...]
);
```
### Insert tuples
```sql
INSERT INTO <table> [(column_1, column_2, column_3, ...)] VALUES
(column_1_value, column_2_value, column_3_value, ...),
[(column_1_value, column_2_value, column_3_value, ...), ...];
```
### Select tuples
```sql
SELECT <column_1>, [column_2, ...] FROM <table>;
SELECT <column_1>, [column_2, ...] FROM <table> WHERE <condition>;
SELECT <column_1>, [column_2, ...] FROM <table> WHERE <column> IN (value, [value, ...]);
SELECT <column_1>, [column_2, ...] FROM <table> WHERE <column> BETWEEN <value> AND <value>;
SELECT <column_1>, [column_2, ...] FROM <table> WHERE <column_text> LIKE '[%]<value>[%]';
SELECT <column_1>, [column_2, ...] FROM <table> WHERE <column_text> ILIKE '[%]<value>[%]'; -- ILIKE ignores case
SELECT <column>, COUNT(<column>) FROM <table> GROUP BY <column>;
SELECT <column>, COUNT(<column>) FROM <table> GROUP BY <column> HAVING <aggregation condition>;
SELECT <column_1>, [column_2, ...] FROM <table> ORDER BY <column> [ASC|DESC];
SELECT <column_1>, [column_2, ...] FROM <table> LIMIT <max number of results> OFFSET <tuple offset count>;
SELECT <column_1>, [column_2, ...] FROM <table> FETCH FIRST <count>;
```

### Add column to an existing table 
```sql
ALTER TABLE <table> ADD COLUMN <column> <type> [constraints...];
```
## Constraints
```sql 
NOT NULL - Defines a column that cannot have null values 
PRIMARY KEY - Defines the column as a participant of the table's primary key
```
## Functions
```sql
CREATE FUNCTION <function> ([[<param1>] <type>, [<param2>] <type>, ...)
RETURNS <type> AS
$$
    --SQL body
$$
LANGUAGE <language>;
```
## Comparators

    = - Equality operator
    > - Greater than 
    >= - Greater than or equal to 
    < - Less than 
    <= - Less than or equal to
    <> - Different

## Arithmetic
    
    + - Addition
    - - Subtraction
    / - Division
    * - Multiplication
    ^ - Exponentiation
    ! - Factorial
    % - Modulo