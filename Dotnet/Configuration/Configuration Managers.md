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

### Environment variables set in generated launchSettings.json

Environment variables set in `launchSettings.json` override those set in the system environment. For example, the ASP.NET Core web templates generate a `launchSettings.json` file that sets the endpoint configuration to:

JSON

```
"applicationUrl": "https://localhost:5001;http://localhost:5000"
```

Configuring the `applicationUrl` sets the `ASPNETCORE_URLS` environment variable and overrides values set in the environment.

[](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#escape-environment-variables-on-linux)

### Escape en


## Refernces
- [ ] need to read
https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0

### environment varaibles
We need to use __ instead of : when specifcifying environment variables to create hiearchy