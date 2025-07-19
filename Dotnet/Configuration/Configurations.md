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

---

## Binding

One of the key advantages of using the .NET configuration abstractions is the ability to bind configuration values to instances of .NET objects. For example, the JSON configuration provider can be used to map _appsettings.json_ files to .NET objects and is used with [dependency injection](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection). This enables the [options pattern](https://learn.microsoft.com/en-us/dotnet/core/extensions/options), which uses classes to provide strongly typed access to groups of related settings. The default binder is reflection-based, but there's a [source generator alternative](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-generator) that's easy to enable.

.NET configuration provides various abstractions. Consider the following interfaces:

- [IConfiguration](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfiguration): Represents a set of key/value application configuration properties.
- [IConfigurationRoot](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfigurationroot): Represents the root of an `IConfiguration` hierarchy.
- [IConfigurationSection](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfigurationsection): Represents a section of application configuration values.

These abstractions are agnostic to their underlying configuration provider (IConfigurationProvider). In other words, you can use an IConfiguration instance to access any configuration value from multiple providers.

The binder can use different approaches to process configuration values:

Direct deserialization (using built-in converters) for primitive types.
The TypeConverter for a complex type when the type has one.
Reflection for a complex type that has properties.
 Note

The binder has a few limitations:

Properties are ignored if they have private setters or their type can't be converted.
Properties without corresponding configuration keys are ignored.

--- 

#### Binding hierarchies

Configuration values can contain hierarchical data. Hierarchical objects are represented with the use of the `:` delimiter in the configuration keys. To access a configuration value, use the `:` character to delimit a hierarchy. For example, consider the following configuration values:

JSONCopy

```
{
  "Parent": {
    "FavoriteNumber": 7,
    "Child": {
      "Name": "Example",
      "GrandChild": {
        "Age": 3
      }
    }
  }
}
```

The following table represents example keys and their corresponding values for the preceding example JSON:

|Key|Value|
|---|---|
|`"Parent:FavoriteNumber"`|`7`|
|`"Parent:Child:Name"`|`"Example"`|
|`"Parent:Child:GrandChild:Age"`|`3`|

---


## Options pattern
