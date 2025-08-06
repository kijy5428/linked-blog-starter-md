
# ⚙️ Entity Framework Core (EF Core) Features

EF Core is a modern, lightweight, and cross-platform ORM for .NET. It provides powerful tools for data access and management.

## 🌍 Cross-Platform

- Runs on **Windows**, **Linux**, and **macOS**.

## 🪶 Lightweight

- Smaller footprint and fewer dependencies compared to the full Entity Framework.

## 🧪 Code-First Approach

- Define your database schema using C# classes.
- Enables **agile** and **test-driven development** workflows.

## 🔍 LINQ Support

- Write expressive and readable queries using **C#** or **VB.NET**.
- Fully integrated with the language for compile-time checking.

## 🗄️ Multi-Database Support

- Compatible with:
    - SQL Server
    - MySQL
    - MariaDB
    - SQLite
    - PostgreSQL

## 🔄 Migrations

- Built-in support for managing schema changes over time.
- Enables version control of database structure.

## 🚀 Performance

- Optimized for handling **large datasets** efficiently.

## 🧩 Modeling Capabilities

- Support for:
    - **Complex Types**
    - **Owned Types**

## 🔗 Relationships

- Supports:
    - One-to-One
    - One-to-Many
    - Many-to-Many

## 🧬 Inheritance Mapping

- Supports:
    - TPC (Table per Concrete Class)
    - TPH (Table per Hierarchy)
    - TPT (Table per Type)

## 🧠 Advanced Features

- **Client Evaluation**
- **Lazy Loading**
- **Explicit Loading**
- **Change Tracking**
- **Caching**

---

# 🔒 Strong Typing in EF Core

EF Core promotes **strongly-typed** data access, improving reliability and maintainability.

## 🧱 Entity Definition

Entities are defined using C# classes:

```CSharp
public class Product
{
    int ProductId { get; set; }
    string ProductName { get; set; }
}
```

Accessing data is straightforward and type-safe:

```CSharp
int productId = myProduct.ProductId;
string productName = myProduct.ProductName;
```

## ✅ Benefits of Strong Typing

- **Compile-time error checking**
- **Improved readability**
- **Easier refactoring**
- **Type safety**

## 🛠️ ORM Automation

EF Core automates many tasks:

- Maps domain models to database tables
- Creates and maintains database schema
- Generates and executes SQL
- Manages transactions
- Tracks retrieved objects

---

Would you like a visual diagram or cheat sheet summarizing EF Core architecture or workflow?