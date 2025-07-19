

### SQL Server Table Creation


- **Creating Tables with T-SQL**:
    
    - Use `CREATE TABLE` (a DDL statement).
    - Specify schema name, table name, columns, data types, and nullability.
    - Modify tables with:
    - `ALTER TABLE` to add/drop columns.
    - `DROP TABLE` to remove the entire table.

---

### Importance of Data Types

- SQL Server supports various data types:
    
    - **Numeric** (e.g., `INT`, `BIGINT`, `DECIMAL`)
    - **Date/Time** (e.g., `DATE`, `DATETIME`)
    - **Character** (e.g., `CHAR`, `VARCHAR`, `NVARCHAR`)
    - **Binary** (e.g., `BINARY`, `VARBINARY`)
- **Why Data Types Matter**:
    
    - **Storage efficiency**: e.g., `BIT` uses 1 byte vs. `BIGINT` uses 8 bytes.
    - **Performance**: Smaller types can improve query speed and reduce storage.
    - **Function compatibility**: SQL functions work only with appropriate types.
    - Example: `EOMONTH()` works with date types, not text.
    - **Query accuracy**: Filtering and ordering require correct types (e.g., comparing dates).

---

![](attachments/Pasted%20image%2020250719160901.png)

![](attachments/Pasted%20image%2020250719160927.png)