Here’s a concise summary of the module for your notes:

---

### Introduction to T-SQL

- **T-SQL (Transact-SQL)** is the primary language used to interact with SQL Server.
- It includes:
    - **DML (Data Manipulation Language)**: Used to `SELECT`, `INSERT`, `UPDATE`, and `DELETE` data.
    - **DDL (Data Definition Language)**: Used to `CREATE`, `ALTER`, and `DROP` database objects like tables.

---

### Key Features of T-SQL

- Supports:
    - Flow control (e.g., `IF`, `WHILE`)
    - Error handling (`TRY...CATCH`)
    - Variables
    - Transactions (including reversible ones)
    - Reusable procedures and functions
- Feature availability may vary by **SQL Server version** and **edition**.

---

### Working with Data

- **SELECT**: Retrieve data from tables.
    - `SELECT * FROM TableA` – all columns and rows.
    - `SELECT FirstName, LastName` – specific columns.
    - Combine columns: `FirstName + ' ' + LastName AS FullName`
    - Filter rows: `WHERE` clause.
- **JOINs**:
    - `INNER JOIN`: Only matching rows from both tables.
    - `LEFT JOIN`: All rows from left table + matches from right (null if no match).
    - `RIGHT JOIN`: All rows from right table + matches from left.
    - `FULL OUTER JOIN`: All rows from both tables, with nulls where no match.
    - `CROSS JOIN`: Cartesian product (all combinations).

---

### Modifying Data

- **INSERT INTO**:
    - Add static values or insert from another table.
    - Example: `INSERT INTO TableA SELECT * FROM TableB`
- **UPDATE**:
    - Modify existing data.
    - Example: `UPDATE TableA SET Country = 'DE' WHERE Country = 'GER'`
- **DELETE**:
    - Remove data based on conditions.
    - Example: `DELETE FROM TableA WHERE DateOfBirth <= '1970-01-01'`

---

Let me know if you'd like this added to a larger study guide or exported as a file!