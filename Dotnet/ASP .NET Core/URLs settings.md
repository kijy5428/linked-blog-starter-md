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

## References

https://andrewlock.net/8-ways-to-set-the-urls-for-an-aspnetcore-app/