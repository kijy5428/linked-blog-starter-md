
You're now ready to add your first migration! Instruct EF Core to create a migration named **InitialCreate**:

- [.NET Core CLI](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_1_dotnet-core-cli)
- [Visual Studio](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_1_vs)

.NET CLICopy

```
dotnet ef migrations add InitialCreate
```

EF Core will create a directory called **Migrations** in your project, and generate some files. It's a good idea to inspect what exactly EF Core generated - and possibly amend it - but we'll skip over that for now.

[](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#create-your-database-and-schema)

### Create your database and schema

At this point you can have EF create your database and create your schema from the migration. This can be done via the following:

- [.NET Core CLI](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_2_dotnet-core-cli)
- [Visual Studio](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_2_vs)

.NET CLICopy

```
dotnet ef database update
```

That's all there is to it - your application is ready to run on your new database, and you didn't need to write a single line of SQL. Note that this way of applying migrations is ideal for local development, but is less suitable for production environments - see the [Applying Migrations page](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/applying) for more info.