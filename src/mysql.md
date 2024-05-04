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


* ## What is the database transaction log?

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

