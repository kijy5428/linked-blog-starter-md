- Using the fixed connection string in OnConfiguring method
- ```csharp
using Microsoft.EntityFrameworkCore;

public class MyDbContext : DbContext

{

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)

    {

        if (!optionsBuilder.IsConfigured)

        {

            // Fixed connection string

            optionsBuilder.UseSqlServer("Server=your_server_name;Database=your_database_name;User Id=your_user;Password=your_password;");

        }

    }

    // Define your DbSets here

    public DbSet MyEntities { get; set; }

}
  ```