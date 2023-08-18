# SQL Commands and Functions

**Table of Contents**
- [Database Creation](#database-creation)
- [Table Creation](#table-creation)
- [Data Manipulation](#data-manipulation)
- [Data Querying](#data-querying)
- [Sorting](#sorting)
- [Filtering](#filtering)
- [Joining](#joining)
- [Grouping](#grouping)
- [Aggregation](#aggregation)
- [Subqueries](#subqueries)
- [Alias](#alias)
- [Distinct](#distinct)
- [Union](#union)
- [Intersection](#intersection)
- [Difference](#difference)
- [Math Functions](#math-functions)
- [String Functions](#string-functions)
- [Date Functions](#date-functions)
- [Logical Operators](#logical-operators)
- [CASE Statement](#case-statement)
- [NULL Handling](#null-handling)
- [Indexing](#indexing)
- [Constraints](#constraints)
- [Transactions](#transactions)
- [Backup & Restore](#backup--restore)
- [Permissions](#permissions)
- [User Management](#user-management)
- [Schema](#schema)
- [Alter Table](#alter-table)
- [Deletion](#deletion)

## Database Creation

- `CREATE DATABASE zoo;`
  - Creates a new database called "zoo".
  - Example: `CREATE DATABASE zoo;`

## Table Creation

- `CREATE TABLE animals (id INT, name VARCHAR(50));`
  - Creates a table named "animals" with "id" and "name" columns.
  - Example: `CREATE TABLE animals (id INT, name VARCHAR(50));`
 
    **[⬆ Back to Top](#table-of-contents)**

## Data Manipulation

- `INSERT INTO animals VALUES (1, 'Lion');`
  - Adds a new row into the "animals" table with values 1 for "id" and 'Lion' for "name".
  - Example: `INSERT INTO animals VALUES (1, 'Lion');`
- `UPDATE animals SET name = 'Tiger' WHERE id = 1;`
  - Modifies the "name" of the animal with "id" 1 to 'Tiger'.
  - Example: `UPDATE animals SET name = 'Tiger' WHERE id = 1;`
- `DELETE FROM animals WHERE name = 'Lion';`
  - Removes rows with "name" value 'Lion' from the "animals" table.
  - Example: `DELETE FROM animals WHERE name = 'Lion';`
 
   **[⬆ Back to Top](#table-of-contents)**

## Data Querying

- `SELECT name FROM animals WHERE id = 1;`
  - Retrieves the "name" of the animal with "id" 1 from the "animals" table.
  - Example: `SELECT name FROM animals WHERE id = 1;`
 
    **[⬆ Back to Top](#table-of-contents)**

## Sorting

- `SELECT name FROM animals ORDER BY name ASC;`
  - Retrieves animal names from the "animals" table in ascending alphabetical order.
  - Example: `SELECT name FROM animals ORDER BY name ASC;`
 
   **[⬆ Back to Top](#table-of-contents)**

## Filtering

- `SELECT name FROM animals WHERE name = 'Tiger';`
  - Retrieves animal names from the "animals" table where "name" is 'Tiger'.
  - Example: `SELECT name FROM animals WHERE name = 'Tiger';`
 
    **[⬆ Back to Top](#table-of-contents)**

## Joining

- `SELECT a.name, c.class FROM animals a JOIN classes c ON a.id = c.animal_id;`
  - Combines "animals" and "classes" tables based on "id" and "animal_id" columns.
  - Example: `SELECT a.name, c.class FROM animals a JOIN classes c ON a.id = c.animal_id;`
 
  - **[⬆ Back to Top](#table-of-contents)**

## Grouping

- `SELECT class, COUNT(*) FROM classes GROUP BY class;`
  - Groups classes from the "classes" table and counts occurrences of each class.
  - Example: `SELECT class, COUNT(*) FROM classes GROUP BY class;`
 
    
  **[⬆ Back to Top](#table-of-contents)**

## Aggregation

- `SELECT COUNT(*) FROM animals;`
  - Counts the total number of animals in the "animals" table.
  - Example: `SELECT COUNT(*) FROM animals;`
 
    **[⬆ Back to Top](#table-of-contents)**

## Subqueries

- `SELECT name FROM animals WHERE id IN (SELECT animal_id FROM classes WHERE class = 'Mammal');`
  - Retrieves animal names with "class" 'Mammal' from the "animals" and "classes" tables.
  - Example: `SELECT name FROM animals WHERE id IN (SELECT animal_id FROM classes WHERE class = 'Mammal');`

**[⬆ Back to Top](#table-of-contents)**

## Alias

- `SELECT name AS animal_name FROM animals;`
  - Retrieves animal names and aliases the "name" column as "animal_name".
  - Example: `SELECT name AS animal_name FROM animals;`

**[⬆ Back to Top](#table-of-contents)**

## Distinct

- `SELECT DISTINCT class FROM classes;`
  - Retrieves unique class names from the "classes" table.
  - Example: `SELECT DISTINCT class FROM classes;`

**[⬆ Back to Top](#table-of-contents)**

## Union

- `SELECT name FROM mammals UNION SELECT name FROM reptiles;`
  - Combines unique names from "mammals" and "reptiles" tables.
  - Example: `SELECT name FROM mammals UNION SELECT name FROM reptiles;`

**[⬆ Back to Top](#table-of-contents)**

## Intersection

- `SELECT name FROM herbivores INTERSECT SELECT name FROM mammals;`
  - Retrieves common animal names from "herbivores" and "mammals" tables.
  - Example: `SELECT name FROM herbivores INTERSECT SELECT name FROM mammals;`

**[⬆ Back to Top](#table-of-contents)**

## Difference

- `SELECT name FROM mammals EXCEPT SELECT name FROM predators;`
  - Retrieves animal names from "mammals" that are not in the "predators" table.
  - Example: `SELECT name FROM mammals EXCEPT SELECT name FROM predators;`

**[⬆ Back to Top](#table-of-contents)**

## Math Functions

- `SELECT ABS(-5);`
  - Computes the absolute value of -5.
  - Example: `SELECT ABS(-5);`
- `SELECT ROUND(3.14159, 2);`
  - Rounds 3.14159 to 2 decimal places.
  - Example: `SELECT ROUND(3.14159, 2);`

**[⬆ Back to Top](#table-of-contents)**

## String Functions

- `SELECT CONCAT(column1, column2);`
  - Concatenates two columns or strings.
  - Example: `SELECT CONCAT(first_name, last_name) AS full_name FROM employees;`

**[⬆ Back to Top](#table-of-contents)**

## Date Functions

- `SELECT YEAR(date_column);`
  - Extracts the year from a date or timestamp column.
  - Example: `SELECT YEAR(birthdate) FROM employees;`

**[⬆ Back to Top](#table-of-contents)**

## Logical Operators

- `SELECT name FROM animals WHERE class = 'Mammal' AND age > 5;`
  - Retrieves animal names that are mammals and older than 5 years.
  - Example: `SELECT name FROM animals WHERE class = 'Mammal' AND age > 5;`

**[⬆ Back to Top](#table-of-contents)**

## CASE Statement

- `SELECT name, CASE WHEN age > 5 THEN 'Adult' ELSE 'Young' END AS age_category FROM animals;`
  - Performs conditional logic to categorize animals as 'Adult' or 'Young' based on age.
  - Example: `SELECT name, CASE WHEN age > 5 THEN 'Adult' ELSE 'Young' END AS age_category FROM animals;`

**[⬆ Back to Top](#table-of-contents)**

## NULL Handling

- `SELECT name FROM animals WHERE weight IS NULL;`
  - Retrieves animal names with unknown weight from the "animals" table.
  - Example: `SELECT name FROM animals WHERE weight IS NULL;`

**[⬆ Back to Top](#table-of-contents)**

## Indexing

- `CREATE INDEX idx_name ON animals (name);`
  - Creates an index on the "name" column of the "animals" table.
  - Example: `CREATE INDEX idx_name ON animals (name);`

**[⬆ Back to Top](#table-of-contents)**

## Constraints

- `CREATE TABLE students (id INT PRIMARY KEY, name VARCHAR(50) NOT NULL, age INT CHECK (age >= 18));`
  - Creates a table "students" with a primary key constraint on "id" and a check constraint on "age".
  - Example: `CREATE TABLE students (id INT PRIMARY KEY, name VARCHAR(50) NOT NULL, age INT CHECK (age >= 18));`

**[⬆ Back to Top](#table-of-contents)**

## Transactions

- `BEGIN;`
  - Begins a transaction.
  - Example: `BEGIN;`
- `COMMIT;`
  - Commits a transaction.
  - Example: `COMMIT;`
- `ROLLBACK;`
  - Rolls back a transaction.
  - Example: `ROLLBACK;`

**[⬆ Back to Top](#table-of-contents)**

## Backup & Restore

- `BACKUP DATABASE zoo TO disk/location;`
  - Creates a backup of the "zoo" database.
  - Example: `BACKUP DATABASE zoo TO disk/location;`
- `RESTORE DATABASE zoo FROM disk/location;`
  - Restores the "zoo" database from a backup.
  - Example: `RESTORE DATABASE zoo FROM disk/location;`

**[⬆ Back to Top](#table-of-contents)**

## Permissions

- `GRANT SELECT ON animals TO user;`
  - Grants SELECT permission on the "animals" table to a user.
  - Example: `GRANT SELECT ON animals TO user;`

**[⬆ Back to Top](#table-of-contents)**

## User Management

- `CREATE USER new_user WITH PASSWORD 'password';`
  - Creates a new user "new_user" with the specified password.
  - Example: `CREATE USER new_user WITH PASSWORD 'password';`
- `ALTER USER existing_user WITH PASSWORD 'new_password';`
  - Changes the password of an existing user.
  - Example: `ALTER USER existing_user WITH PASSWORD 'new_password';`

**[⬆ Back to Top](#table-of-contents)**

## Schema

- `CREATE SCHEMA department;`
  - Creates a new schema named "department".
  - Example: `CREATE SCHEMA department;`

**[⬆ Back to Top](#table-of-contents)**

## Alter Table

- `ALTER TABLE animals ADD COLUMN color VARCHAR(20);`
  - Adds a new "color" column to the "animals" table.
  - Example: `ALTER TABLE animals ADD COLUMN color VARCHAR(20);`

**[⬆ Back to Top](#table-of-contents)**

## Deletion

- `DROP DATABASE zoo;`
  - Deletes the "zoo" database and all its contents.
  - Example: `DROP DATABASE zoo;`
- `DROP TABLE animals;`
  - Deletes the "animals" table and its data.
  - Example: `DROP TABLE animals;`

**[⬆ Back to Top](#table-of-contents)**
