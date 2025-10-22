# Comprehensive SQL (MySQL) Cheat Sheet

This repository contains a single, comprehensive SQL script (`database_queries.sql`) that serves as a cheat sheet and reference guide for a wide range of SQL commands, with a focus on the MySQL dialect. It is designed for developers, DBAs, and students who need a quick reference for common and advanced SQL operations.

## 📖 Overview

The script is organized into logical sections, covering everything from basic database and table creation to advanced topics like window functions, CTEs, and transactions. Each section provides clear examples of how to use different SQL statements.

## 🚀 How to Use

### 1. Get the Code
Clone the repository to your local machine using the following command:

```bash
git clone https://github.com/TejaNaik15/sql-complete-guide-.git
```

### 2. Explore the Script

**Important:** This script is intended as a reference, not to be executed in its entirety at once. Running the whole file will likely result in errors as it creates and drops the same objects sequentially.

1.  **Open the `database_queries.sql` file** in your favorite SQL client or text editor (e.g., MySQL Workbench, DBeaver, VS Code).
2.  **Navigate** to the section you are interested in.
3.  **Execute commands individually or in small, logical blocks** to understand their functionality.

### 3. Setting up a Test Environment

To test the DML (Data Manipulation) and DQL (Data Query) commands, you should first create the necessary database and tables. You can do this by running the commands from the first few sections in order:

```sql
-- 1. Create the database
CREATE DATABASE IF NOT EXISTS company_db;
USE company_db;

-- 2. Create the tables
CREATE TABLE departments (
    dept_id INT PRIMARY KEY AUTO_INCREMENT,
    dept_name VARCHAR(50) NOT NULL,
    location VARCHAR(100)
);

CREATE TABLE employees (
    emp_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    phone VARCHAR(15),
    hire_date DATE,
    salary DECIMAL(10, 2),
    department_id INT,
    manager_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (department_id) REFERENCES departments(dept_id)
);

-- 3. Insert some sample data to query
INSERT INTO departments (dept_name, location) VALUES
('IT', 'New York'),
('Sales', 'London'),
('HR', 'New York');

INSERT INTO employees (first_name, last_name, email, salary, department_id)
VALUES
    ('John', 'Doe', 'john.doe@email.com', 50000, 1),
    ('Jane', 'Smith', 'jane.smith@email.com', 60000, 2),
    ('Bob', 'Johnson', 'bob.johnson@email.com', 55000, 1),
    ('Alice', 'Williams', 'alice.williams@email.com', 65000, 3);
```

Once the schema and data are in place, you can run the queries from the `SELECT`, `JOINS`, `AGGREGATE FUNCTIONS`, and other sections.

## 📚 Topics Covered

The script is divided into the following sections:

1.  **Database Operations**: `CREATE`, `DROP`, `USE`
2.  **Table Operations (DDL)**: `CREATE`, `ALTER`, `DROP`, `RENAME`, `TRUNCATE`
3.  **Data Manipulation (DML)**: `INSERT`, `UPDATE`, `DELETE`
4.  **Data Query (DQL)**: `SELECT` with `WHERE`, `LIKE`, `IN`, `ORDER BY`, `LIMIT`
5.  **Aggregate Functions**: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
6.  **Grouping**: `GROUP BY`, `HAVING`
7.  **Joins**: `INNER`, `LEFT`, `RIGHT`, `FULL OUTER` (emulation), `CROSS`, `SELF`
8.  **Subqueries**: Scalar, multi-row, and correlated subqueries
9.  **Set Operations**: `UNION`, `UNION ALL`, `INTERSECT`, `EXCEPT`
10. **Views**: `CREATE`, `REPLACE`, `DROP`
11. **Indexes**: `CREATE`, `DROP`
12. **Constraints**: `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`, `DEFAULT`
13. **String Functions**: `CONCAT`, `SUBSTRING`, `REPLACE`, etc.
14. **Numeric Functions**: `ROUND`, `CEIL`, `FLOOR`, `RAND`, etc.
15. **Date & Time Functions**: `NOW`, `DATEDIFF`, `DATE_ADD`, `DATE_FORMAT`, etc.
16. **Conditional Functions**: `CASE`, `IF`, `COALESCE`, `IFNULL`
17. **Window Functions** (MySQL 8.0+): `ROW_NUMBER`, `RANK`, `LEAD`, `LAG`
18. **Common Table Expressions (CTE)**: Simple and recursive
19. **Transactions**: `COMMIT`, `ROLLBACK`, `SAVEPOINT`
20. **Stored Procedures**: `CREATE`, `CALL`, `DROP` with `IN` and `OUT` parameters
21. **User-Defined Functions (UDF)**: `CREATE`, `DROP`
22. **Triggers**: `BEFORE`/`AFTER` on `INSERT`/`UPDATE`
23. **User Management**: `CREATE USER`, `GRANT`, `REVOKE`
24. **Performance Optimization**: `EXPLAIN`, `ANALYZE`, `OPTIMIZE`
25. **Advanced Queries**: Nth highest salary, finding duplicates, etc.
26. **JSON Operations** (MySQL 5.7+): `JSON_EXTRACT`, `JSON_SET`
27. **Regular Expressions**: `REGEXP` / `RLIKE`
28. **Backup & Restore**: `mysqldump` command-line examples
29. **Miscellaneous**: `SHOW`, `VERSION`, `USER`, `KILL`
30. **Best Practices**: A summary of important guidelines for writing good SQL.

---

Designed by **Teja Naik**.

*This cheat sheet is a living document. Feel free to contribute by fixing errors or adding more examples.*