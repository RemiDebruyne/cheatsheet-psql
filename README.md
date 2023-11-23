# PSQL cheat sheet

## Server
- `sudo systemctl start postgresql` : start psql server
- `sudo systemctl stop postgresql` : stop psql server
- `sudo systemctl status postgresql` : check if psql server is running

## Open PGCLI
`pgcli [database] [username]` : open a database in pgcli

## See infos
- `\l` : list all database 
- `\du` : list all user
- `\dt` : list tables
- `\dn` : list schema 

## Basic command
### Data Definition Language (DDL)
- `CREATE DATABASE database_name;` : Creates a new database.
- `CREATE TABLE table_name (...);` : Creates a new table.
- `ALTER TABLE table_name ...;` : Modifies an existing table.
- `DROP TABLE table_name;` : Deletes a table.
- `DROP DATABASE database_name;` : Deletes a database.
- `CREATE SCHEMA schema_name;` : create a schema
- `SET search_path TO schema_name;` : Set the default schema to a defined schema


### Data Manipulation Language (DML)
- `INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);` : Inserts new data into a table.
- `UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE c:ndition;` : Updates existing data in a table.
- `DELETE FROM table_name WHERE condition;` : Deletes data from a table.

### Data Query Language (DQL)
- `SELECT column1, column2, ... FROM table_name;` : Selects data from a table.
- `SELECT DISTINCT column1, column2, ... FROM table_name;` : Selects distinct values from a table.
- `GROUP BY` : Used with aggregate functions to group the result of a query based on one or more columns.
- `HAVING` : Similar to WHERE, but used after GROUP BY to filter records.

## Advanced Commands

### Join Operations
- `INNER JOIN` - Selects records with matching values in both tables.
- `LEFT (OUTER) JOIN` - Selects all records from the left table and matched records from the right table.
- `RIGHT (OUTER) JOIN` - Selects all records from the right table and matched records from the left table.
- `FULL (OUTER) JOIN` - Selects all records when there is a match in either left or right table.

### Aggregation Functions
- `COUNT(column_name)` - Counts the number of rows.
- `SUM(column_name)` - Sums up the numerical values.
- `AVG(column_name)` - Calculates the average value.
- `MAX(column_name)` - Finds the maximum value.
- `MIN(column_name)` - Finds the minimum value.

