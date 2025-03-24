# SQL Core Concepts - The 20% That Delivers 80% Understanding

## 1. What is SQL?

SQL (Structured Query Language) is a standardized programming language used for managing and manipulating relational databases. It allows you to create, retrieve, update, and delete data, as well as manage database structures.

## 2. Database Structure Basics

A relational database consists of:
- **Tables**: Collections of related data organized in rows and columns
- **Columns/Fields**: Define the type of data (e.g., text, numbers, dates)
- **Rows/Records**: Contain the actual data
- **Primary Keys**: Uniquely identify each row in a table
- **Foreign Keys**: Connect tables together by referencing primary keys in other tables

## 3. Creating Database Objects

```sql
-- Create a database
CREATE DATABASE company;

-- Create a table
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    hire_date DATE,
    salary DECIMAL(10,2),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);

-- Modify a table
ALTER TABLE employees ADD email VARCHAR(100);
ALTER TABLE employees DROP COLUMN phone;
ALTER TABLE employees MODIFY salary DECIMAL(12,2);

-- Delete a table
DROP TABLE employees;
```

## 4. Basic Data Manipulation (CRUD Operations)

```sql
-- Create: Insert data
INSERT INTO employees (employee_id, first_name, last_name, hire_date, salary, department_id)
VALUES (1, 'John', 'Smith', '2022-01-15', 50000.00, 3);

-- Read: Query data
SELECT first_name, last_name, salary FROM employees;

-- Update: Modify data
UPDATE employees
SET salary = 55000.00
WHERE employee_id = 1;

-- Delete: Remove data
DELETE FROM employees
WHERE employee_id = 1;
```

## 5. SELECT Query Fundamentals

```sql
-- Basic structure of a SELECT query
SELECT column1, column2, ...     -- What columns to retrieve
FROM table_name                   -- From which table(s)
WHERE condition                   -- Filter which rows
GROUP BY column                   -- Group rows by column values
HAVING group_condition            -- Filter which groups
ORDER BY column [ASC|DESC]        -- Sort the results
LIMIT count;                      -- Limit number of results

-- Example
SELECT department_id, AVG(salary) as avg_salary
FROM employees
WHERE hire_date > '2020-01-01'
GROUP BY department_id
HAVING AVG(salary) > 50000
ORDER BY avg_salary DESC
LIMIT 5;
```

## 6. WHERE Clause and Operators

```sql
-- Comparison operators
SELECT * FROM employees WHERE salary > 50000;
SELECT * FROM employees WHERE department_id = 3;
SELECT * FROM employees WHERE hire_date <= '2022-01-01';

-- Logical operators
SELECT * FROM employees WHERE department_id = 3 AND salary > 60000;
SELECT * FROM employees WHERE department_id = 3 OR department_id = 5;
SELECT * FROM employees WHERE NOT department_id = 3;

-- Pattern matching
SELECT * FROM employees WHERE last_name LIKE 'S%';    -- Starts with S
SELECT * FROM employees WHERE email LIKE '%@gmail.com';  -- Ends with @gmail.com
SELECT * FROM employees WHERE first_name LIKE '_a%';   -- Second letter is 'a'

-- Range
SELECT * FROM employees WHERE salary BETWEEN 40000 AND 60000;
SELECT * FROM employees WHERE hire_date BETWEEN '2021-01-01' AND '2021-12-31';

-- Lists
SELECT * FROM employees WHERE department_id IN (3, 5, 7);
```

## 7. JOIN Operations

```sql
-- INNER JOIN: Returns only matching rows in both tables
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.department_id;

-- LEFT JOIN: Returns all rows from the left table, and matching rows from right table
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id;

-- RIGHT JOIN: Returns all rows from the right table, and matching rows from left table
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
RIGHT JOIN departments d ON e.department_id = d.department_id;

-- FULL JOIN: Returns all rows when there's a match in either table
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
FULL JOIN departments d ON e.department_id = d.department_id;
```

## 8. Aggregate Functions

```sql
-- COUNT: Counts rows
SELECT COUNT(*) FROM employees;
SELECT department_id, COUNT(*) FROM employees GROUP BY department_id;

-- SUM: Adds values
SELECT SUM(salary) FROM employees;
SELECT department_id, SUM(salary) FROM employees GROUP BY department_id;

-- AVG: Calculates average
SELECT AVG(salary) FROM employees;

-- MIN/MAX: Finds minimum/maximum values
SELECT MIN(salary), MAX(salary) FROM employees;

-- GROUP BY: Groups rows with the same values
SELECT department_id, AVG(salary), COUNT(*)
FROM employees
GROUP BY department_id;

-- HAVING: Filters groups (like WHERE but for grouped data)
SELECT department_id, AVG(salary)
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 50000;
```

## 9. Subqueries

```sql
-- Subquery in WHERE
SELECT first_name, last_name
FROM employees
WHERE department_id IN (SELECT department_id FROM departments WHERE location = 'New York');

-- Subquery in SELECT
SELECT e.first_name, 
       e.salary,
       (SELECT AVG(salary) FROM employees) as company_avg
FROM employees e;

-- Subquery in FROM
SELECT dept.department_id, dept.avg_salary
FROM (
    SELECT department_id, AVG(salary) as avg_salary
    FROM employees
    GROUP BY department_id
) as dept
WHERE dept.avg_salary > 50000;
```

## 10. Indexes and Performance

```sql
-- Create an index on a column
CREATE INDEX idx_lastname ON employees(last_name);

-- Create a unique index
CREATE UNIQUE INDEX idx_email ON employees(email);

-- Delete an index
DROP INDEX idx_lastname;
```

## Bonus: Common Database Management Tasks

```sql
-- Transaction control
BEGIN TRANSACTION;
-- SQL statements
COMMIT;  -- or ROLLBACK to undo

-- View management
CREATE VIEW employee_details AS
SELECT e.employee_id, e.first_name, e.last_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;

-- User management (varies by database system)
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT, INSERT ON company.employees TO 'username'@'localhost';
REVOKE INSERT ON company.employees FROM 'username'@'localhost';
```
