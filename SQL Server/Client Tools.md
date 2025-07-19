![](attachments/Pasted%20image%2020250719152052.png)![](attachments/Pasted%20image%2020250719152110.png)![](attachments/Pasted%20image%2020250719152128.png)

---
Got it! Here's a streamlined summary for your notes:

---

### SQL Server Tools Overview

- **sqlcmd**:
    
    - Command-line tool for SQL Server.
    - Legacy version installed by default.
    - New Go-based version available with extra features.
    - Install via Chocolatey, Winget, or GitHub.
- **SQL Server Management Studio (SSMS)**:
    
    - GUI tool for managing SQL Server.
    - Installable via Chocolatey or Microsoft website.
    - Includes advanced features like SQL Server Agent, Replication, Security, and High Availability.
- **Azure Data Studio (ADS)**:
    
    - Lightweight, VS Code-based tool.
    - Supports notebooks, extensions, and multiple database types (SQL Server, MySQL, PostgreSQL).
    - Can connect to local or remote servers.

---

### Demo Highlights

- **Using sqlcmd**:
    
    - Run queries like `SELECT @@version` with `-Q`.
    - Connect to local or remote servers using `-S`.
    - New version supports container deployment with `sqlcmd create mssql`.
- **AdventureWorks2019 Sample Database**:
    
    - Download and restore using `sqlcmd`.
    - Restore involves specifying backup file and logical file paths.
- **Azure Data Studio Usage**:
    
    - Connect using Windows Authentication.
    - View and explore databases, tables, and views.
    - Use notebooks to run and save queries with results.
    - Supports extensions for Azure and other tools.
- **SSMS Usage**:
    
    - Connect via dialog box.
    - Explore databases and objects.
    - Right-click to script objects (tables, views, etc.).
    - **Useful for scripting and recreating databases.**

---

### Feature Comparison

- **SSMS**: Full-featured, includes advanced server tools.
- **ADS**: Lightweight, supports notebooks and extensions.
- Each tool has unique strengths depending on the task.

---

Let me know if you'd like this saved as a file or added to a larger set of notes!