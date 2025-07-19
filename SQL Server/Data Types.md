

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

Great question! Here's a clear breakdown of the differences between the SQL Server data types you mentioned:

---

### 🔤 **Character Data Types Overview**

|Data Type|Unicode|Fixed/Variable|Max Length|Notes|
|---|---|---|---|---|
|`CHAR(n)`|❌ No|Fixed|8,000|Pads with spaces if input is shorter than `n`.|
|`NCHAR(n)`|✅ Yes|Fixed|4,000|Stores Unicode (2 bytes per character).|
|`VARCHAR(n)`|❌ No|Variable|8,000 (or `MAX`)|Saves space for shorter strings.|
|`NVARCHAR(n)`|✅ Yes|Variable|4,000 (or `MAX`)|Unicode version of `VARCHAR`.|
|`TEXT`|❌ No|Variable (deprecated)|2GB|For large non-Unicode text. Use `VARCHAR(MAX)` instead.|
|`NTEXT`|✅ Yes|Variable (deprecated)|2GB|For large Unicode text. Use `NVARCHAR(MAX)` instead.|

---

### 🧠 Key Differences

- **Unicode vs Non-Unicode**:
    
    - `NCHAR`, `NVARCHAR`, `NTEXT` store Unicode (e.g., multilingual characters like 中文, عربى).
    - `CHAR`, `VARCHAR`, `TEXT` store non-Unicode (ASCII/ANSI).
- **Fixed vs Variable Length**:
    
    - `CHAR` and `NCHAR` always use the full defined length.
    - `VARCHAR` and `NVARCHAR` only use as much space as needed.
- **Deprecated Types**:
    
    - `TEXT` and `NTEXT` are **deprecated**—avoid using them in new development.
    - Use `VARCHAR(MAX)` or `NVARCHAR(MAX)` instead.

---

### 💡 When to Use What?

- Use `VARCHAR` for general-purpose text (e.g., names, emails).
- Use `NVARCHAR` if you need to support **multiple languages or special characters**.
- Use `CHAR` or `NCHAR` only when the length is **always fixed** (e.g., country codes).
- Avoid `TEXT` and `NTEXT`—they're outdated.

---

### 🔤 `VARCHAR` (Variable Character)

- Stores **non-Unicode** characters (ASCII/ANSI).
- Uses **1 byte per character**.
- Best for **English-only** or Western character sets.
- Example: `'Hello'` stored as 5 bytes.

### 🌐 `NVARCHAR` (Unicode Variable Character)

- Stores **Unicode** characters (UTF-16).
- Uses **2 bytes per character**.
- Supports **multilingual text** (e.g., 中文, عربى, emojis).
- Example: `'Hello'` stored as 10 bytes.

---

### 🧠 Why It Matters

|Feature|`VARCHAR`|`NVARCHAR`|
|---|---|---|
|Unicode support|❌ No|✅ Yes|
|Storage per char|1 byte|2 bytes|
|Max length (`MAX`)|~2GB|~2GB|
|Use case|English text|Multilingual text|

---

### 🔍 Why the `"N"` Prefix?

- In SQL Server, when you write a string like `'Hello'`, it's treated as a **non-Unicode** string (`VARCHAR`).
- If you write `N'Hello'`, it's treated as a **Unicode** string (`NVARCHAR`).

The `"N"` stands for **National language**, indicating that the string supports **Unicode characters**.

---

### 🧠 Example

```sql
-- Non-Unicode string (VARCHAR)
SELECT '中文'  -- May return ??? or error if collation doesn't support it

-- Unicode string (NVARCHAR)
SELECT N'中文'  -- Correctly returns the Chinese characters
```

Without the `N` prefix, SQL Server may not interpret the string correctly if it contains non-ASCII characters.

---

### 🔤 Summary

|Prefix|Data Type|Unicode Support|Use Case|
|---|---|---|---|
|`'text'`|`VARCHAR`|❌ No|English or ASCII-only text|
|`N'text'`|`NVARCHAR`|✅ Yes|Multilingual or special characters|

---

Let me know if you'd like a cheat sheet or a quick demo query to test this!
