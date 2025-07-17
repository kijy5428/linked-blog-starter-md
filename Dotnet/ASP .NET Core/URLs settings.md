## [Environment variables for the URL](https://andrewlock.net/8-ways-to-set-the-urls-for-an-aspnetcore-app/#environment-variables-for-the-url)


ASP.NET Core has [an advanced, extensible, configuration system](https://livebook.manning.com/book/asp-net-core-in-action-third-edition/chapter-10/) that can load values from multiple configuration sources. By default, the `ConfigurationManager` used in .NET 8 loads values from the following locations:

- _appsettings.json_ JSON file
- Optional environment-specific JSON file, _appsettings.ENVIRONMENT.json_
- [User Secrets](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets)
- Environment variables
- Command-line arguments

You can add additional providers to load from other locations, but these are the ones added by default. You can use this system to load settings and customise your application, but ASP.NET Core also uses it to configure its internals.

ASP.NET Core adds all the following to the configuration system:

- All environment variables are added directly to configuration.
- Environment variables that have the prefix `DOTNET_` have the prefix removed and are added to the collection.
- For ASP.NET Core apps, environment variables that have the prefix `ASPNETCORE_` have the prefix removed and are added to the collection These aren't added if you are creating a generic-host-based worker service (using `HostApplicationBuilder`).

If you don't override them manually with `UseUrls()`, then ASP.NET Core will use the value of the `URLS` key from the configuration system. Based on the description above you can set the URLS using any of the following environment variables (casing doesn't matter):

- `URLS`
- `ASPNETCORE_URLS`
- `DOTNET_URLS`

> The order above **also describes the order of precedence if you set _all_ these environment variables, with `URLS` having the highest precedence,**


You can set environment variables in the usual way based on your environment. For example, using the command line:

```powershell
setx ASPNETCORE_URLS "http://localhost:5001"
```

using powershell

```powershell
$Env:ASPNETCORE_URLS="http://localhost:5001"
```

or using bash:

```bash
export ASPNETCORE_URLS="http://localhost:5001;https://localhost:5002"
```

As you can see above, you can also pass multiple addresses to listen on (using HTTP or HTTPS) by separating them with a semicolon.

---

## [Environment variables for the ports](https://andrewlock.net/8-ways-to-set-the-urls-for-an-aspnetcore-app/#environment-variables-for-the-ports)

The `ASPNETCORE_URLS` and similar environment variables can be used to set the URLs using the formats shown at the start of this post, for example:

- `ASPNETCORE_URLS="http://localhost:5001"`—listen to port 5001 on the loopback (`localhost` address).
- `ASPNETCORE_URLS="http://192.168.8.31:5001"`—listen to port 5001 on the specified IP address.
- `ASPNETCORE_URLS="http://*:5001"`—listen to port 5001 on any IP address

One thing that's always bugged me a little is the name of this variable. It implies (to me) that you can use things like `http://example.com:5000` and your app will listen on that DNS name. That's not the case. The above URL is treated exactly the same as `http://*:5000`, i.e. it configures the app to listen to port `5000` on _any_ IP address.

.NET 8 added new configuration keys to be more explicit about this. Instead of specifying "URLs" you specify `HTTP_PORTS` and `HTTPS_PORTS`, and these are used to bind any IP address. You can specify multiple ports using a semicolon separator. For example, if you set the following environment variables:

- `ASPNETCORE_HTTP_PORTS=5001;5002`
- `ASPNETCORE_HTTPS_PORTS=5003`

These are expanded to the following URLs:

- `http://*:5001`
- `http://*:5002`
- `https://*:5003`

Just like other configuration keys, you can use `ASPNETCORE_`, `DOTNET_`, or "no prefix" to specify the values:

- `HTTP_PORTS` (and `HTTPS_PORTS`)
- `ASPNETCORE_HTTP_PORTS` (and `ASPNETCORE_HTTPS_PORTS`)
- `DOTNET_HTTP_PORTS` (or `DOTNET_HTTPS_PORTS`)

Note that if you specify one of these _and_ `ASPNETCORE_URLS` (for example) then the `ASPNETCORE_URLS` value takes precedence, and a warning is logged to the output:

```bash
warn: Microsoft.AspNetCore.Hosting.Diagnostics[15]
      Overriding HTTP_PORTS '5002' and HTTPS_PORTS ''. Binding to values defined by URLS instead 'http://*:5003'.
```

> In .NET 8, [the `ASPNETCORE_HTTP_PORTS` variable is set to `8080` by default in the .NET 8 docker images](https://andrewlock.net/exploring-the-dotnet-8-preview-updates-to-docker-images-in-dotnet-8/#asp-net-core-apps-now-use-port-8080-by-default) (whereas `ASPNETCORE_URLS` was set in previous version docker images). You can override this default value by setting `ASPNETCORE_HTTP_PORTS` _or_ `ASPNETCORE_URLS` (among other ways).

Environment variables are just one way to add values to configuration; command line arguments are another.

---

## [_appsettings.json_](https://andrewlock.net/8-ways-to-set-the-urls-for-an-aspnetcore-app/#appsettings-json)

_appsettings.json_, and the environment-specific _appsettings.Development.json_ files are included in virtually every modern .NET app template, and provide an easy way to add values to the ASP.NET Core configuration system.

Hopefully it's no surprise that you can use these files to specify the URLs your app listens on using the same `urls`, `http_ports` and `https_ports` keys you've seen already. The following adds the `urls` key to the default template:

```json
{
  "urls": "http://*:5003", // 👈 Specify the URL
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```

This version adds the `http_ports` and `https_ports` keys:

```json
{
  "http_ports": "5001;5002", // 👈 Expands to http://*:5001 and http://*:5002
  "https_ports": "5003", // 👈 Expands to http2://*:5003
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```

If you want to use different ports in development and production you can use the _appsettings.json_ file for production, and the _appsettings.Development.json_ for development. Or whatever pattern works for you.

Alternatively, you can rely on a different JSON file, _launchSettings.json_.


---

## [launchSettings.json](https://andrewlock.net/8-ways-to-set-the-urls-for-an-aspnetcore-app/#launchsettings-json)

In addition to the _appsettings.json_ file, most .NET project templates also include a _launchSettings.json_ file in the _Properties_ folder. This file doesn't add directly to your configuration; instead it contains various profiles for launching your ASP.NET Core application in development using `dotnet run`.

A typical file contains one or more definitions for launching the profile directly from the command line and one definition for launching the profile using IIS Express. This file drives the Debug drop-down in Visual Studio:

![The launchsettings.json drives the Visual Studio Debug view](https://andrewlock.net/content/images/2020/launchsettings.png)

_launchSettings.json_ provides an easy way to set the application URLs via the `applicationUrl` property - you can see one under the `iisSettings` for IIS express, and one under each of the `http` and `https` profiles:

```json
{
  "$schema": "http://json.schemastore.org/launchsettings.json",
  "iisSettings": {
    "windowsAuthentication": false,
    "anonymousAuthentication": true,
    "iisExpress": {
      "applicationUrl": "http://localhost:49412", // 👈 URL to use with IIS Express profile
      "sslPort": 44381
    }
  },
  "profiles": {
    "http": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "http://localhost:5005", // 👈 HTTP-only profile
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "https": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:7045;http://localhost:5005", // 👈 HTTP & HTTPS profile
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "IIS Express": {
      "commandName": "IISExpress",
      "launchBrowser": true,
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

You don't need to do anything special to use this file—`dotnet run` will pick it up automatically.

> launchSettings.json also provides an easy way to set additional environment variables using the `environmentVariables`, as you can see from the file above.

When you run your app from the command line with `dotnet run`, your app will use the `applicationUrl` properties in the "Project" command: `http://localhost:5005` in the `http` profile above. When you run the app using the "IISExpress" command, your app will use the `applicationUrl` from the `iisSettings.iisExpress` node: `http://localhost:49412`.

This file is the easiest way to configure your environment when developing locally. In fact, you have to go out of your way to _not_ use the _launchSettings.json_:

```bash
dotnet run --no-launch-profile
```

This will skip over the _launchSettings.json_ file and fall back to configuration to determine the URLs instead.

All of the approaches shown so far set the URLs for Kestrel indirectly, but you can also set them _directly_.

## References

https://andrewlock.net/8-ways-to-set-the-urls-for-an-aspnetcore-app/