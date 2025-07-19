## Configure console apps
### Configuration Builder approach

.NET console applications created using the [dotnet new](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new) command template or Visual Studio by default _don't_ expose configuration capabilities. To add configuration in a new .NET console application, [add a package reference](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-package-add) to [Microsoft.Extensions.Configuration](https://www.nuget.org/packages/Microsoft.Extensions.Configuration). This package is the foundation for configuration in .NET apps. It provides the [ConfigurationBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.configurationbuilder) and related types.

C#Copy

```
using Microsoft.Extensions.Configuration;

var configuration = new ConfigurationBuilder()
    .AddInMemoryCollection(new Dictionary<string, string?>()
    {
        ["SomeKey"] = "SomeValue"
    })
    .Build();

Console.WriteLine(configuration["SomeKey"]);

// Outputs:
//   SomeValue
```

The preceding code:

- Creates a new [ConfigurationBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.configurationbuilder) instance.
- Adds an in-memory collection of key-value pairs to the configuration builder.
- Calls the [Build()](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.configurationbuilder.build#microsoft-extensions-configuration-configurationbuilder-build) method to create an [IConfiguration](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfiguration) instance.
- Writes the value of the `SomeKey` key to the console.

While this example uses an in-memory configuration, there are many configuration providers available, exposing functionality for file-based, environment variables, command line arguments, and other configuration sources. For more information, see [Configuration providers in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers).

See also: [[ConfigurationBuilder]]


### Alternative hosting approach

Commonly, your apps will do more than just read configuration. They'll likely use dependency injection, logging, and other services. The [.NET Generic Host](https://learn.microsoft.com/en-us/dotnet/core/extensions/generic-host) approach is recommended for apps that use these services. Instead, consider [adding a package reference](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-package-add) to [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting). Modify the _Program.cs_ file to match the following code:

C#Copy

```
using Microsoft.Extensions.Hosting;

using IHost host = Host.CreateApplicationBuilder(args).Build();

// Application code should start here.

await host.RunAsync();
```

The [Host.CreateApplicationBuilder(String[])](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.host.createapplicationbuilder#microsoft-extensions-hosting-host-createapplicationbuilder\(system-string\(\)\)) method provides default configuration for the app in the following order, from highest to lowest priority:

1. Command-line arguments using the [Command-line configuration provider](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers#command-line-configuration-provider).
2. Environment variables using the [Environment Variables configuration provider](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers#environment-variable-configuration-provider).
3. [App secrets](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) when the app runs in the `Development` environment.
4. _appsettings.json_ using the [JSON configuration provider](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers#file-configuration-provider).
5. _appsettings._`Environment`_.json_ using the [JSON configuration provider](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers#file-configuration-provider). For example, _appsettings_._**Production**_._json_ and _appsettings_._**Development**_._json_.
6. [ChainedConfigurationProvider](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.chainedconfigurationsource) : Adds an existing `IConfiguration` as a source.

Adding a configuration provider overrides previous configuration values. For example, the [Command-line configuration provider](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers#command-line-configuration-provider) overrides all values from other providers because it's added last. If `SomeKey` is set in both _appsettings.json_ and the environment, the environment value is used because it was added after _appsettings.json_.