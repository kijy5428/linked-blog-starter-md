## Use Swagger UI for local ad-hoc testing

By default, the `Microsoft.AspNetCore.OpenApi` package doesn't ship with built-in support for visualizing or interacting with the OpenAPI document. Popular tools for visualizing or interacting with the OpenAPI document include [Swagger UI](https://swagger.io/tools/swaggerhub/) and [ReDoc](https://github.com/Redocly/redoc). Swagger UI and ReDoc can be integrated in an app in several ways. Editors such as Visual Studio and VS Code offer extensions and built-in experiences for testing against an OpenAPI document.

The `Swashbuckle.AspNetCore.SwaggerUi` package provides a bundle of Swagger UI's web assets for use in apps. This package can be used to render a UI for the generated document. To configure this:

- Install the `Swashbuckle.AspNetCore.SwaggerUi` package.
- Enable the swagger-ui middleware with a reference to the [OpenAPI route registered earlier](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-9.0#customize-the-openapi-endpoint-route).

C#Copy

```
using Microsoft.AspNetCore.Authentication;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.OpenApi;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.OpenApi.Models;

var builder = WebApplication.CreateBuilder();

builder.Services.AddOpenApi();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();

    app.UseSwaggerUI(options =>
    {
        options.SwaggerEndpoint("/openapi/v1.json", "v1");
    });

}

app.MapGet("/", () => "Hello world!");

app.Run();
```

As a security best practice on limiting information disclosure, _**OpenAPI user interfaces (Swagger UI, ReDoc, Scalar) should only be enabled in development environments.**_ For example, see [Swagger OAuth 2.0 configuration](https://swagger.io/docs/open-source-tools/swagger-ui/usage/oauth2/).

Launch the app and navigate to `https://localhost:<port>/swagger` to view the Swagger UI.

To automatically launch the app at the Swagger UI URL using the `https` profile of `Properties/launchSettings.json`:

- Confirm that `launchBrowser` is enabled (`true`).
- Set the `launchUrl` to `swagger`.

JSONCopy

```
"launchBrowser": true,
"launchUrl": "swagger",
```