Configuration in .NET is performed using one or more [configuration providers](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration#configuration-providers). Configuration providers read configuration data from key-value pairs using various configuration sources:

- Settings files, such as _appsettings.json_
- Environment variables
- [Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/overview)
- [Azure App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/overview)
- Command-line arguments
- Custom providers, installed or created
- Directory files
- In-memory .NET objects
- Third-party providers

--- 

## Concepts and abstractions

Given one or more configuration sources, the [IConfiguration](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfiguration) type provides a unified view of the configuration data. Configuration is read-only, and the configuration pattern isn't designed to be programmatically writable. The `IConfiguration` interface is a single representation of all the configuration sources, as shown in the following diagram:

[![The `IConfiguration` interface is a single representation of all the configuration sources.](https://learn.microsoft.com/en-us/dotnet/core/extensions/media/configuration-sources.svg)](https://learn.microsoft.com/en-us/dotnet/core/extensions/media/configuration-sources.svg#lightbox)