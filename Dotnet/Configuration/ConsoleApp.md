## Configure console apps

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