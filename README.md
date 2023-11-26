# PSQL cheat sheet

## Server
- `sudo systemctl start postgresql` : start psql server
- `sudo systemctl stop postgresql` : stop psql server
- `sudo systemctl status postgresql` : check if psql server is running

## Open PGCLI
`pgcli [database] [username]` : open a database in pgcli

### See infos
- `\l` : list all database 
- `\du` : list all user
- `\dt` : list tables
- `\dn` : list schema 




## Basic command
### Data Definition Language (DDL)
- `CREATE DATABASE database_name;` : Creates a new database.
- `CREATE TABLE table_name (...);` : Creates a new table.
- `ALTER TABLE table_name ...;` : Modifies an existing table.
    - `ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL` : Add constraint NOT NULL to the column
    - `ALTER TABLE table_name ALTER COLUMN column_name ADD [options CHECK || UNIQUE || FOREIGN KEY]` : Add a constraint to the column
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

### Saving and restoring
- `pg_dump [connection option] [option] [database name]` : Create a save file of your database
    - `-f` : Redirect the output of the save to the target file
    - `-F` : Format of the output
        - `p` : SQL script file (default value)
        - `c` : Personnalized archive, usable by `pg_restore` and most flexible format
        - `d` : Create a directory usable by `pg_restore`. One directory with a file is create per tables
    - `-a` : Only save data (data tables, large objects and sequence values) not schema
    - `-n` : Save schema and its data
    - `-s` : Only save schema, not any data related to it 
    - `-U` : Define the user used to connect to the data base

For more info on `pg_dump` : https://docs.postgresql.fr/15/app-pgdump.html

- `psql [database] < [save file]` : Save file is the output file of `pg_dump`. Database must be created prior to the use of this command using `createdb -T template0 [database name]`
- `pg_restore [connection option] [option] [file name]`

For more info on `pg_restore`: https://docs.postgresql.fr/9.6/app-pgrestore.html

