
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

###   Create your database and schema

At this point you can have EF create your database and create your schema from the migration. This can be done via the following:

- [.NET Core CLI](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_2_dotnet-core-cli)
- [Visual Studio](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_2_vs)

.NET CLICopy

```
dotnet ef database update
```

That's all there is to it - your application is ready to run on your new database, and you didn't need to write a single line of SQL. Note that this way of applying migrations is ideal for local development, but is less suitable for production environments - see the [Applying Migrations page](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/applying) for more info.

[](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#evolving-your-model)

### Evolving your model

A few days have passed, and you're asked to add a creation timestamp to your blogs. You've done the necessary changes to your application, and your model now looks like this:

C#Copy

```
public class Blog
{
    public int Id { get; set; }
    public string Name { get; set; }
    public DateTime CreatedTimestamp { get; set; }
}
```

Your model and your production database are now out of sync - we must add a new column to your database schema. Let's create a new migration for this:

- [.NET Core CLI](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_3_dotnet-core-cli)
- [Visual Studio](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_3_vs)

.NET CLICopy

```
dotnet ef migrations add AddBlogCreatedTimestamp
```

Note that we give migrations a descriptive name, to make it easier to understand the project history later.

Since this isn't the project's first migration, EF Core now compares your updated model against a snapshot of the old model, before the column was added; the model snapshot is one of the files generated by EF Core when you add a migration, and is checked into source control. Based on that comparison, EF Core detects that a column has been added, and adds the appropriate migration.

You can now apply your migration as before:

- [.NET Core CLI](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_4_dotnet-core-cli)
- [Visual Studio](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#tabpanel_4_vs)

.NET CLICopy

```
dotnet ef database update
```

Note that this time, EF detects that the database already exists. In addition, when our first migration was applied above, this fact was recorded in a special migrations history table in your database; this allows EF to automatically apply only the new migration.

[](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli#excluding-parts-of-your-model)

### Excluding parts of your model

Sometimes you may want to reference types from another DbContext. This can lead to migration conflicts. To prevent this, exclude the type from the migrations of one of the DbContexts.

C#Copy

```
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.Entity<IdentityUser>()
        .ToTable("AspNetUsers", t => t.ExcludeFromMigrations());
}
```