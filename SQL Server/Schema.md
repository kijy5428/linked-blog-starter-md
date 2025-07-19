- **Schemas** organize database objects (tables, views, etc.).
    
    - Default schemas: `sys` (system) and `dbo` (database owner).
    - You can create custom schemas for organization (e.g., by department or use case).

### `dbo` Schema (Database Owner)

- **Default schema** for most users and objects.
- Stands for **Database Owner**.
- When you create a table without specifying a schema, it usually goes into the `dbo` schema.
- Example: `dbo.Customers` means the `Customers` table is in the `dbo` schema.

### `sys` Schema (System)

- Contains **system-level objects** used by SQL Server.
- Includes metadata views, system tables, and internal functions.
- You typically **query** objects in `sys` (e.g., `sys.tables`, `sys.columns`) but **don’t modify** them.
- Example: `SELECT * FROM sys.tables` returns a list of all user-defined tables in the database.

---

### Summary Table

|Schema|Purpose|Common Use|
|---|---|---|
|`dbo`|Default for user objects|Tables, views, procedures, etc.|
|`sys`|System metadata and objects|Querying database structure/details|

Let me know if you’d like a visual diagram or example queries using these schemas!


### Why `[dbo]` Keeps Showing Up

- `[dbo]` is the **default schema** for most objects in SQL Server.
- SQL Server displays the **fully qualified name** of objects as `[schema].[object]` to avoid confusion—especially when multiple schemas exist.
- So `[dbo].[Customers]` means the `Customers` table is in the `dbo` schema.

### Can You Hide or Simplify It?

Unfortunately, **you can't hide the schema prefix** in the object explorer views. It's shown by design to help distinguish objects across schemas.

However, here are a few tips to make it less annoying:

#### 1. **Use Aliases or Shortcuts in Queries**

Instead of typing `[dbo].[Customers]`, you can just use `Customers` in your queries—SQL Server will assume `dbo` if no schema is specified.

#### 2. **Organize Your Objects**

If you create your own schema (e.g., `sales`, `hr`, etc.), the schema prefix becomes more meaningful and helps with organization.

#### 3. **Filter Object Explorer**

You can filter the object explorer to show only certain tables or views, which might reduce visual clutter.

---

Would you like help creating a custom schema or organizing your tables to make things cleaner?