ASP.NET Core has [an advanced, extensible, configuration system](https://livebook.manning.com/book/asp-net-core-in-action-third-edition/chapter-10/) that can load values from multiple configuration sources. By default, the `ConfigurationManager` used in .NET 8 loads values from the following locations:

- _appsettings.json_ JSON file
- Optional environment-specific JSON file, _appsettings.ENVIRONMENT.json_
- [User Secrets](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets)
- Environment variables
- Command-line arguments

---

## Applicatoin Configuration

[WebApplication.CreateBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.builder.webapplication.createbuilder) initializes a new instance of the [WebApplicationBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.builder.webapplicationbuilder) class with preconfigured defaults. The initialized `WebApplicationBuilder` (`builder`) provides default configuration for the app in the following order, from highest to lowest priority:

1. Command-line arguments using the [Command-line configuration provider](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#command-line).
2. Non-prefixed environment variables using the [Non-prefixed environment variables configuration provider](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#evcp).
3. [User secrets](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-9.0) when the app runs in the `Development` environment.
4. `appsettings.{Environment}.json` using the [JSON configuration provider](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#jcp). For example, `appsettings.Production.json` and `appsettings.Development.json`.
5. [appsettings.json](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#appsettingsjson) using the [JSON configuration provider](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#jcp).
6. A fallback to the host configuration described in the [next section](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#host).

Note: `WebApplication.CreateBuilder(args)` should only be called once in apps relying on IIS in-process hosting.
---

## Host Configuration

The following list contains the default host configuration sources from highest to lowest priority for [WebApplicationBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.builder.webapplicationbuilder):

1. Command-line arguments using the [Command-line configuration provider](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#command-line)
2. `DOTNET_`-prefixed environment variables using the [Environment variables configuration provider](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.environmentvariables.environmentvariablesconfigurationprovider).
3. `ASPNETCORE_`-prefixed environment variables using the [Environment variables configuration provider](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.environmentvariables.environmentvariablesconfigurationprovider).

For the [.NET Generic Host](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/generic-host?view=aspnetcore-9.0) and [Web Host](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/web-host?view=aspnetcore-9.0), the default host configuration sources from highest to lowest priority is:

1. `ASPNETCORE_`-prefixed environment variables using the [Environment variables configuration provider](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.environmentvariables.environmentvariablesconfigurationprovider).
2. Command-line arguments using the [Command-line configuration provider](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-9.0#command-line)
3. `DOTNET_`-prefixed environment variables using the [Environment variables configuration provider](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.environmentvariables.environmentvariablesconfigurationprovider).

---

When a configuration value is set in host and application configuration, the application configuration is used.
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


### Hierarchical Environment variables
We need to use __ instead of : when specifcifying environment variables to create hiearchy