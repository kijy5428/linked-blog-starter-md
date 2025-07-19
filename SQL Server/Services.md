Here’s a concise summary of the final module for your notes:

---

### 🧩 Additional SQL Server Services

SQL Server includes more than just the core database engine. Key additional services:

#### 1. **SQL Server Analysis Services (SSAS)**
- Used for **data modeling and analytics**.
- Two modes:
  - **Multidimensional** (uses MDX, introduced in SQL Server 2005)
  - **Tabular** (uses DAX, introduced in SQL Server 2012, in-memory engine)
- Common use case: powering BI tools like Excel or Power BI.
- Data typically comes from SQL Server (acts as a data warehouse).
- Requires **Visual Studio with Data Tools** and SSAS extension for development.

#### 2. **SQL Server Integration Services (SSIS)**
- Used for **ETL (Extract, Transform, Load)** processes.
- Helps move and transform data between systems.

#### 3. **SQL Server Reporting Services (SSRS)**
- Used to create, manage, and deliver **reports**.

#### 4. **Hybrid Features**
- Newer features that integrate SQL Server with cloud services or other platforms.

---

### 🧱 Building a Cube with SSAS (Tabular or Multidimensional)

1. **Setup**:
   - Install Visual Studio Community + Data Tools + SSAS extension.
   - Use Chocolatey for easy installation.

2. **Create Analysis Services Database**:
   - Use Visual Studio to connect to localhost and create a new SSAS database (e.g., `AW_SSAS`).

3. **Define Data Source**:
   - Connect to `AdventureWorks2019` using OLE DB and Windows Authentication.

4. **Create Data Source View**:
   - Select relevant tables/views (e.g., `SalesOrderHeader`, `SalesPerson`, `Customers`).
   - Define relationships (e.g., foreign keys).

5. **Create Dimensions**:
   - Example: `Customer` dimension using `CustomerID` and `AccountNumber`.
   - Example: `SalesPerson` dimension with `BusinessEntityID`, `LastName`, `JobTitle`, `CountryRegionName`.

6. **Process Dimensions**:
   - Required before browsing or using them in cubes.

7. **Create Cube**:
   - Use `SalesOrderHeader` as fact table.
   - Select measures like `SubTotal`, `TaxAmt`, `Freight`, `TotalDue`.
   - Add related dimensions.

8. **Process Cube**:
   - Automatically processes any unprocessed dimensions.
   - Enables browsing and querying.

9. **Browse Cube**:
   - Use built-in browser to explore data (e.g., SubTotal by Country or Job Title).
   - Supports slicing and dicing for analytics.

---

### 🧠 Key Takeaways

- SSAS enables **fast, reusable, and structured analytics**.
- Dimensions and cubes help organize and aggregate data efficiently.
- Visual Studio is the main development environment for SSAS projects.
- Processed cubes can be queried directly or consumed by BI tools.

---

Let me know if you’d like this exported as a study guide or visualized in a diagram!