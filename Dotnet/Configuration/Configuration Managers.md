ASP.NET Core has [an advanced, extensible, configuration system](https://livebook.manning.com/book/asp-net-core-in-action-third-edition/chapter-10/) that can load values from multiple configuration sources. By default, the `ConfigurationManager` used in .NET 8 loads values from the following locations:

- _appsettings.json_ JSON file
- Optional environment-specific JSON file, _appsettings.ENVIRONMENT.json_
- [User Secrets](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets)
- Environment variables
- Command-line arguments

---

## Applicatoin Configuration

---

## Host Configuration

---
## Refernces
- [ ] need to read
https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0

### environment varaibles
We need to use __ instead of : when specifcifying environment variables to create hiearchy