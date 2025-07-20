
ASP.NET Core apps provide built-in support for generating information about endpoints in an app via the `Microsoft.AspNetCore.OpenApi` package.
- `AddOpenApi` registers services required for OpenAPI document generation into the application's DI container.
- `MapOpenApi` adds an endpoint into the application for viewing the OpenAPI document serialized into JSON. The OpenAPI endpoint is restricted to the development environment to minimize the risk of exposing sensitive information and reduce the vulnerabilities in production.

## `Microsoft.AspNetCore.OpenApi` NuGet package
The [`Microsoft.AspNetCore.OpenApi`](https://www.nuget.org/packages/Microsoft.AspNetCore.OpenApi/) package provides the following features:
- Support for generating OpenAPI documents at run time and accessing them via an endpoint on the application.
- Support for "transformer" APIs that allow modifying the generated document.

To use the `Microsoft.AspNetCore.OpenApi` package, add it as a PackageReference to a project file:
- [Nuget Package](https://www.nuget.org/packages/Microsoft.AspNetCore.OpenApi/)

---
## Configure OpenAPI document generation

The following code:

- Adds OpenAPI services using the [AddOpenApi](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.dependencyinjection.openapiservicecollectionextensions.addopenapi) extension method on the app builder's service collection.
- Maps an endpoint for viewing the OpenAPI document in JSON format with the [MapOpenApi](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.builder.openapiendpointroutebuilderextensions.mapopenapi) extension method on the app.

C#Copy

```
var builder = WebApplication.CreateBuilder();

builder.Services.AddOpenApi();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();
}

app.MapGet("/", () => "Hello world!");

app.Run();
```

Launch the app and navigate to `https://localhost:<port>/openapi/v1.json` to view the generated OpenAPI document.

[](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-9.0&tabs=visual-studio%2Cvisual-studio-code#options-to-customize-openapi-document-generation)

## Options to Customize OpenAPI document generation

The following sections demonstrate how to customize OpenAPI document generation.

[](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-9.0&tabs=visual-studio%2Cvisual-studio-code#customize-the-openapi-document-name)

### Customize the OpenAPI document name

Each OpenAPI document in an app has a unique name. **The default document name that is registered is `v1`.**

C#Copy

```
builder.Services.AddOpenApi(); // Document name is v1
```

The document name can be modified by passing the name as a parameter to the [AddOpenApi](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.dependencyinjection.openapiservicecollectionextensions.addopenapi) call.

C#Copy

```
builder.Services.AddOpenApi("internal"); // Document name is internal
```

The document name surfaces in several places in the OpenAPI implementation.

When fetching the generated OpenAPI document, the document name is provided as the `documentName` parameter argument in the request. The following requests resolve the `v1` and `internal` documents.

BashCopy

```
GET http://localhost:5000/openapi/v1.json
GET http://localhost:5000/openapi/internal.json
```