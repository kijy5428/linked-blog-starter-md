
## Installing the tools

`dotnet ef` can be installed as either a global or local tool. Most developers prefer installing `dotnet ef` as a global tool using the following command:

.NET CLICopy

```
dotnet tool install --global dotnet-ef
```

To use it as a local tool, restore the dependencies of a project that declares it as a tooling dependency using a [tool manifest file](https://learn.microsoft.com/en-us/dotnet/core/tools/global-tools#install-a-local-tool).

Update the tool using the following command:

.NET CLICopy

```
dotnet tool update --global dotnet-ef
```

Before you can use the tools on a specific project, you'll need to add the `Microsoft.EntityFrameworkCore.Design` package to it.

.NET CLICopy

```
dotnet add package Microsoft.EntityFrameworkCore.Design
```

https://learn.microsoft.com/en-us/ef/core/cli/dotnet