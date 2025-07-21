The page discusses the migrations feature in EF Core, which allows developers to incrementally update the database schema to align with changes in the application’s data model while preserving existing data. It outlines the process of adding a migration when a data model change occurs, using EF Core tools to generate migration source files, and applying these migrations to the database.

Key steps include:

1. **Installing Tools**: Developers can use .NET Core CLI tools or Visual Studio’s Package Manager Console tools.
2. **Creating Migrations**: Developers can create a migration using commands like `dotnet ef migrations add InitialCreate` or `Add-Migration InitialCreate`.
3. **Updating the Database**: The database can be created and updated using commands like `dotnet ef database update` or `Update-Database`.
4. **Evolving the Model**: When changes are made to the model, a new migration can be created to reflect these changes.
5. **Excluding Parts of the Model**: Developers can exclude certain types from migrations to avoid conflicts.

The page serves as a beginner’s guide to using migrations and encourages consulting additional documentation for more detailed information on managing and applying migrations.

https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli
