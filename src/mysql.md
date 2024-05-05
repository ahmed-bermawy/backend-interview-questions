* ## Is the Mysql query case-sensitive?

By default, MySQL queries are not case-sensitive. However, this behavior can be changed by setting the `lower_case_table_names` system variable.

<details>
<summary> Example </summary>

```sql
SELECT VERSION(), CURRENT_DATE;
SeLect version(), current_date;
seleCt vErSiOn(), current_DATE;
```
</details>

* ## What is the difference between CHAR and VARCHAR?
`CHAR` and `VARCHAR` are both used to store string data in MySQL. 

`CHAR` stores fixed-length strings and `VARCHAR` stores variable-length strings.

* ## What are the main differences between InnoDB and MyISAM?
InnoDB supports transactions, foreign keys and relationship constraints, while MyISAM does not.

InnoDB has row-level locking, while MyISAM only supports table-level locking.

InnoDB has better crash recovery capabilities compared to MyISAM.

* ## What is the difference between the LIKE and REGEXP operators?

`LIKE` is used to match patterns using wildcards `%`

while `REGEXP` is used to match patterns using regular expressions `^`.

<details>
<summary> Example </summary>

```sql
SELECT * FROM users WHERE name LIKE 'A%';  // Matches names starting with 'A'

SELECT * FROM users WHERE name REGEXP '^A';  // Matches names starting with 'A'
```
</details>

* ## What is database Normalization?
Database normalization is the process
of organizing the columns and tables of a relational database

to minimize redundancy and dependency
by dividing large tables into smaller tables and defining relationships between them.

* ## What are the TRIGGERS in MySQL?
A trigger is a set of actions that are run automatically when a specified change operation
(SQL INSERT, UPDATE, or DELETE statement) is performed on a specified table

The following TRIGGERS are allowed in MySQL:

    BEFORE INSERT
    AFTER INSERT
    BEFORE UPDATE
    AFTER UPDATE
    BEFORE DELETE
    AFTER DELETE

* ## What is the transaction?
A transaction is a unit of work that you want to treat as "a whole." It has to either happen in full or not at all.


* ## What is the ACID property in a database?
ACID (Atomicity, Consistency, Isolation, Durability)
is a set of properties that guarantee that database transactions are processed reliably.

- **Atomicity:** All changes to data are performed as if they are a single operation. 
- **Consistency:** the change can only happen if the new state of the system is valid; any attempt to commit an invalid change will fail, leaving the system in its previous valid state.
- **Isolation:** Transactions are isolated from each other until they are completed.
- **Durability:** Changes made by completed transactions are saved to disk and are not lost in case of a system failure.

<details>
<summary> Example </summary>

```sql
START TRANSACTION;

INSERT INTO users (name, email) VALUES ('John Doe', 'john_doe@example.com');

COMMIT;
```
</details>

* ## How to represent boolean values in MySQL?
In MySQL, boolean values are represented using a `BOOLEAN` or `BOOL` data type, which are aliases for `TINYINT(1)`.

also you can use `ENUM` instead of `BOOLEAN` to represent boolean values in MySQL

* ## Select from categories that have more than five products?
```sql
SELECT category_id, COUNT(product_id) as total_products
FROM products
GROUP BY category_id
HAVING total_products > 5;
```


* ## What are the database transaction logs?

A database's transaction log is a file or set of files that record all the changes made to the data in the database. It is an essential component of database management systems (DBMS) that ensures data integrity and provides the ability to recover from failures.
The transaction log serves several key purposes:

**Recovery:** The transaction log allows the database to recover to a consistent state in the event of a system failure, such as a power outage or hardware failure. By replaying the transactions recorded in the log, the database can restore the data to its state before the failure occurred.

**Rollback:** The transaction log allows transactions to be rolled back or undone. If a transaction is not completed successfully, the database can use the transaction log to reverse the changes made by the transaction and restore the data to its original state.

**Concurrency Control:** The transaction log is used to support concurrency control mechanisms, such as locking and multiversion concurrency control (MVCC). These mechanisms ensure that multiple transactions can access and modify the same data without conflicting with each other.

**Replication:** In some database systems, the transaction log is used to replicate changes to other databases or servers. By replaying the transactions from the log, the replication process can keep multiple databases in sync.

* ## What is the difference between the delete and truncate command?

`DELETE` is a DML (Data Manipulation Language) statement.
It is used to remove specific rows from a table based on a condition.

When you use DELETE, the operation is logged in the database's transaction log, which means you can use the ROLLBACK command to undo the operation.

DELETE is slower than TRUNCATE, especially for large tables, because it generates a separate entry in the transaction log for each deleted row.
Example:
```sql
DELETE FROM table_name WHERE condition;
```

`TRUNCATE` is a DDL (Data Definition Language) statement.
It is used to remove all rows from a table, but it does not delete the table structure (columns, constraints, indexes, etc.).

TRUNCATE is faster than DELETE, especially for large tables, because it does not generate individual delete entries in the transaction log. Instead, it deallocates the data pages and resets any auto-increment counters.

TRUNCATE cannot be rolled back, and it resets the table's auto-increment counter.
Example:
```sql
TRUNCATE TABLE table_name;
```

* ## Why truncate make the table autoincrement to 1?

This behavior is by design and is intended to ensure
that the auto-increment column starts from the beginning when new rows are inserted into the table after truncation.

* ## What is the difference between Union and Union All?

`UNION` and `UNION ALL` are used to combine the result sets of two or more SELECT statements.

`UNION` removes duplicate rows from the combined result set, while `UNION ALL` includes all rows, including duplicates.

`UNION` is slower than `UNION ALL` because it has to perform an additional step to remove duplicates.

* ## What about stored procedures?

A stored procedure in MySQL is a prepared SQL code that you can save, reuse, and share with others. Stored procedures allow you to group a set of SQL statements into a single unit and execute them whenever needed, without having to rewrite the code each time. Stored procedures can also accept parameters, making them more flexible and reusable.

Here's a basic example of how to create a stored procedure in MySQL:
```sql
CREATE PROCEDURE sp_get_employee(IN employee_id INT)
BEGIN
SELECT * FROM employees WHERE id = employee_id;
END;
```
In this example, sp_get_employee is the name of the stored procedure, and it accepts one input parameter employee_id. The BEGIN and END keywords enclose the body of the stored procedure, which consists of a single SELECT statement that retrieves the employee record with the specified ID.

Once you've created a stored procedure, you can call it like this:

`CALL sp_get_employee(1);`

* ## What about function?

A function in MySQL is a set of SQL statements that can be reused in other SQL statements or stored procedures. Functions can accept parameters, perform calculations or data manipulations, and return a value. Functions are similar to stored procedures, but they are typically used to perform specific calculations or data transformations rather than executing a sequence of SQL statements.

Here's a basic example of how to create a function in MySQL:
```sql
CREATE FUNCTION calculate_tax(amount DECIMAL(10,2)) RETURNS DECIMAL(10,2)
BEGIN
DECLARE tax DECIMAL(10,2);
SET tax = amount * 0.1;
RETURN tax;
END;
```

* ## What is the difference between a stored procedure and a function?

Stored procedures and functions are both reusable blocks of SQL code
that can be called from other SQL statements or applications.
However, there are some key differences between the two:

**Return Value:** Functions must return a value, while stored procedures do not have to return a value.

**Usage:** Functions are typically used to perform calculations or data transformations and return a single value, while stored procedures are used to execute a sequence of SQL statements and perform more complex operations.

**Transaction Control:** Stored procedures can control transactions using COMMIT and ROLLBACK statements, while functions cannot.

**Error Handling:** Stored procedures can handle errors using the DECLARE HANDLER statement, while functions cannot.

**Scope:** Functions can be called from SQL statements, stored procedures, and other functions, while stored procedures can only be called from SQL statements or other stored procedures.


* ## What is the view in the database?

A view in a database is a virtual table that is based on the result set of a SELECT statement. Views allow you to simplify complex queries by storing them as a virtual table that can be queried like a regular table. Views do not store any data themselves; they simply provide a way to present data from one or more tables in a structured format.
Views have several advantages:

**Simplicity:** Views allow you to encapsulate complex queries into a single, easy-to-use object.

**Security:** Views can restrict access to certain columns or rows of a table, allowing you to control the data that users can see.

**Performance:** Views can improve performance by precomputing expensive queries and storing the results.

**Data Integrity:** Views can ensure that certain constraints are always enforced, such as ensuring that only certain rows are visible or that certain calculations are always correct.

<details>

<summary> Example </summary>

```sql
-- To create view
CREATE VIEW high_salary_employees AS
SELECT name
FROM employees
WHERE salary > 50000;

-- Call the view
SELECT * FROM high_salary_employees;

-- Drop view
DROP VIEW view_name;
```

</details>

* ## How to analysis slow query in MySQL?

MySQL provides several tools for analyzing slow queries and optimizing database performance. Some of the most common tools include:

**EXPLAIN:** The EXPLAIN statement can be used to analyze the execution plan of a query and identify potential performance issues, such as missing indexes or inefficient joins.

you can see all indexes in `possible_keys` column 

```sql
EXPLAIN SELECT * FROM employees WHERE salary > 50000;
```

**Partitioning:** Split large tables into smaller. Partitioning can improve query performance by reducing the amount of data that needs to be scanned for each query.

```sql

CREATE TABLE employees (
    id INT,
    name VARCHAR(50),
    salary INT
)
PARTITION BY RANGE (salary) (
    PARTITION p0 VALUES LESS THAN (50000),
    PARTITION p1 VALUES LESS THAN (100000),
    PARTITION p2 VALUES LESS THAN (MAXVALUE)
);
```


**SHOW PROFILE:** The SHOW PROFILE statement can be used to display detailed information about the execution of a query, including the time spent in each stage of the query execution.

```sql
SET profiling = 1;
SELECT * FROM employees WHERE salary > 50000;
SHOW PROFILE;
```

**MySQL Performance Schema:** The Performance Schema is a feature in MySQL that provides detailed performance metrics about the database server, including information about query execution, resource usage, and locking.

```sql
SELECT * FROM performance_schema.events_statements_summary_by_digest;
```

**MySQL Query Analyzer:** The MySQL Query Analyzer is a graphical tool that can be used to analyze slow queries, identify performance bottlenecks, and optimize database performance.

* ## What are the aggregation functions in MySQL?

Aggregation functions in MySQL are functions that operate on a set of values and return a single value as a result.

<details>

<summary>Common aggregation functions in MySQL </summary>

**COUNT:** Returns the number of rows that match a specified condition.

```sql
SELECT COUNT(*) FROM employees;
```

**SUM:** Returns the sum of a set of values.

```sql
SELECT SUM(salary) FROM employees;
```

**AVG:** Returns the average of a set of values.

```sql
SELECT AVG(salary) FROM employees;
```

**MIN:** Returns the minimum value in a set of values.

```sql
SELECT MIN(salary) FROM employees;
```

**MAX:** Returns the maximum value in a set of values.

```sql
SELECT MAX(salary) FROM employees;
```

</details>

* ## If I want to write-only to a database, what is better engine for that?

If you want too write-only to a database, the best storage engine for that purpose is `MyISAM`.

MyISAM is a non-transactional storage engine optimized for write-heavy workloads.
It is designed for high-speed inserts and updates
and is well-suited for applications that require fast write performance

* ## How indexing works in MySQL?

Indexing in MySQL is a way to optimize the performance of queries
by reducing the number of rows that need to be scanned to retrieve the desired data.
An index is a data structure that stores the values of one or more columns in a table in a sorted order,
allowing the database to quickly locate the rows that match a given condition.

* ## Can you add unique index to a column that has duplicate values?

No, you cannot add a unique index to a column that has duplicate values.

A unique index enforces the constraint that all values in the indexed column(s) must be unique,

* ## Can you add a unique index to a column that has data?

Yes, you can add a unique index to a column that already has data.

When you add a unique index to a column that already has data,
the database will check the existing data to ensure that there are no duplicate values in the column.

If the column contains duplicate values,
the database will prevent you from adding the unique index until you resolve the duplicates.

* ## What happens to the existing index on the 'first_name' column when I add a composite index for 'first_name' and 'last_name'?

The existing individual indexes on the columns will still exist,
but they will not be used by the database optimizer when querying both columns together.

The database optimizer will use the new composite index to optimize queries that involve both columns.

* ## should we delete the old index?

It is recommended to do so to avoid confusion and unnecessary overhead.

* ## You have given api, and it has taken extra time around 20 seconds, and you reach to query level how you will speed it up?

There are several ways to speed up a slow API query in MySQL:

**Optimize the Query:** Review the query execution plan using the EXPLAIN statement and identify any potential performance bottlenecks, such as missing indexes or inefficient joins. Make sure that the query is using the appropriate indexes and that the tables are properly optimized.

**Add Indexes:** Add indexes to the columns used in the WHERE, JOIN, and ORDER BY clauses of the query to speed up data retrieval. Be careful not to add too many indexes, as this can slow down write operations.

**Partitioning:** Partition large tables into smaller partitions based on a range of values, such as dates or IDs. Partitioning can improve query performance by reducing the amount of data that needs to be scanned for each query.

**Caching:** Implement caching mechanisms to store the results of frequently executed queries in memory. This can reduce the load on the database server and speed up query execution.

**Query Optimization:** Rewrite the query to use more efficient SQL constructs, such as subqueries, joins, and aggregate functions. Avoid using SELECT * and limit the number of columns returned by the query.

**Database Configuration:** Review the MySQL server configuration settings, such as buffer sizes, cache settings, and thread pool settings. Make sure that the server is properly configured to handle the workload.

**Database Sharding:** If the database is too large to fit on a single server, consider sharding the database into smaller partitions that can be distributed across multiple servers. This can improve query performance by distributing the workload across multiple servers.

* ## What is the issue with this query SELECT * FROM accounts WHERE id IN (SELECT account_id FROM account_data)?

The issue with this query is that it uses a subquery in the WHERE clause, which can be inefficient and slow down query performance.

Instead of using a subquery, you can rewrite the query using a JOIN operation to improve performance.

also using `IN` operator can be slow when the subquery returns a large number of rows.

```sql

SELECT a.*
FROM accounts a
JOIN account_data ad ON a.id = ad.account_id;

```

