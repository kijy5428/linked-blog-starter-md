### SQL Server Functions

- **Three main types**:
    
    1. **Scalar Functions**: Return a single value (e.g., `EOMONTH(date)` returns the last day of the month).
    2. **Table-Valued Functions**: Return a table (e.g., `SELECT * FROM BDayToday`).
    3. **Aggregate Functions**: Perform calculations on sets of rows (e.g., `COUNT`, `SUM`, `AVG`).
- SQL Server supports:
    
    - **Built-in functions**
    - **User-defined functions** (custom logic)

---

### Stored Procedures

- Precompiled collections of SQL statements.
- Benefits:
    - Reusable and modular
    - Often better performance than ad hoc queries
    - Enhanced security (grant access to procedure without exposing tables)
    - Support for transactions and version control

---

### System Tables

- Provide metadata about the database.
- Common examples:
    - `sys.tables` – list of user tables
    - `sys.columns` – column details
    - `sys.types` – data types
- Can be joined to explore schema details.
- Full list available in SQL Server documentation.

---

### Views

- A **view** stores a query for reuse.
- Created with `CREATE VIEW` followed by a `SELECT` statement.
- Acts like a virtual table: `SELECT * FROM ViewA`
- Automatically reflects changes in underlying tables (no need to update the view when data changes).

---

Let me know if you'd like this added to a full study guide or exported!