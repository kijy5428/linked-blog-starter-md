## Basics
- [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [postman website](https://blog.postman.com/what-is-openapi/)
- [dev-proxy tool](ttps://github.com/dotnet/dev-proxy)
- [Youtube](https://www.youtube.com/watch?v=PenvYHJ9Koc)

## Microsoft Learn
- [Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-9.0)
- [Generate OpenAPI documentations](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-9.0&tabs=visual-studio%2Cvisual-studio-code)
- 
- `AddOpenApi` registers services required for OpenAPI document generation into the application's DI container.
- `MapOpenApi` adds an endpoint into the application for viewing the OpenAPI document serialized into JSON. The OpenAPI endpoint is restricted to the development environment to minimize the risk of exposing sensitive information and reduce the vulnerabilities in production.


## API v. API operation v. API endpoint

The following sections explain the differences between an API, an API endpoint, and an API operation in the context of ASP.NET Core and OpenAPI documentation.

### API (Application Programming Interface)

An API is a set of rules and protocols for building and interacting with software applications. It defines how different software components should communicate. In general web development, "API" typically refers to a web service that exposes functionality over HTTP.

In ASP.NET Core, an API is usually built using controllers or minimal APIs, which handle incoming HTTP requests and return responses.

ASP.NET Core's internal naming conventions sometimes use "API" differently. For instance, in [API Explorer](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.mvc.apiexplorer), an "ApiDescription" actually represents an [API Operation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-9.0#api-operation) rather than the full API service. This distinction reflects internal naming conventions and sometimes differ from the broader definition used here.

See [Introduction to the ApiExplorer in ASP.NET Core](https://andrewlock.net/introduction-to-the-apiexplorer-in-asp-net-core/) for more information on API Explorer.


### API Operation

An API operation represents a specific action or capability that an API provides. In ASP.NET Core, this corresponds to:

- Controller action methods in MVC-style APIs
- Route handlers in Minimal APIs

Each operation is defined by its HTTP method (`GET`, `POST`, `PUT`, etc.), path, parameters, and responses.

[](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-9.0#api-endpoint)

### API Endpoint

An API endpoint is a specific URL:

- That represents a specific resource or functionality exposed by the API.
- Provides the exact address that a client needs to send an HTTP request to in order to interact with a particular API operation.

An endpoint is a combination of the API's base URL and a specific path to the desired resource, along with the supported HTTP methods:

- For controller-based APIs, endpoints combine the route template with controller and action.
- For Minimal APIs, endpoints are explicitly defined with `app.MapGet()`, `app.MapPost()`, etc.

For example, the `api/products/{id}` endpoint that supports the following operations:

- `GET /api/products/{id}`
- `PUT /api/products/{id}`
- `PATCH /api/products/{id}`
- `Delete /api/products/{id}`
- `HEAD /api/products/{id}`

Endpoints often include query parameters, for example, `GET /api/products?category=electronics&sort=price`

[](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-9.0#openapi-documentation)

### OpenAPI Documentation

In the context of OpenAPI, the documentation describes the API as a whole, including all its endpoints and operations. OpenAPI provides a structured way to document APIs, making it easier for developers to understand how to interact with them.

API Operations are the primary focus of OpenAPI documentation. The [OpenAPI specification](https://spec.openapis.org/oas/latest.html) organizes documentation by operations, which are grouped by paths (endpoints). Each operation is described with details such as parameters, request bodies, responses, and more. This structured format allows tools to generate client libraries, server stubs, and interactive documentation automatically.

In an OpenAPI document:

- The entire document describes the API as a whole
- Each path item (like `/api/products/{id}`) represents an endpoint
- Under each path, the HTTP methods (`GET`, `POST`, `PUT`, etc.) define the operations
- Each operation contains details about parameters, request body, responses, etc.

Example in OpenAPI JSON format:

JSONCopy

```
json{
  "paths": {
    "/api/products/{id}": {  // This is the endpoint
      "get": {  // This is the operation
        "summary": "Get a product by ID",
        "parameters": [...],
        "responses": {...}
      },
      "put": {  // Another operation on the same endpoint
        "summary": "Update a product",
        "parameters": [...],
        "responses": {...}
      }
    }
  }
}
```

[](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-9.0#api-api-operation-and-api-endpoint-comparison)

## API, API operation, and API endpoint comparison

The following table summarizes the differences between an API, an API operation, and an API endpoint:

|Concept|API Operation|API Endpoint|
|---|---|---|
|**Definition**|A logical description of an API action: method + path + behavior|The actual configured HTTP route that listens for requests|
|**Level**|Conceptual, what action can happen|Concrete, what URL and method are matched|
|**Tied to**|OpenAPI API design/specification|ASP.NET Core routing at runtime|
|**Describes**|What the API does for example, "create product"|Where and how to call it, for example, `POST https://localhost:7099/api/products`, `POST https://contoso.com/api/products`|
|**In ASP.NET Core**|Controller actions or Minimal API methods, before routing resolves|Endpoint objects resolved at runtime|
- [Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-9.0)
- 

## Dotnet Core support
The [`Microsoft.AspNetCore.OpenApi`](https://www.nuget.org/packages/Microsoft.AspNetCore.OpenApi/) package provides the following features:

- Support for generating OpenAPI documents at run time and accessing them via an endpoint on the application.
- Support for "transformer" APIs that allow modifying the generated document.

To use the `Microsoft.AspNetCore.OpenApi` package, add it as a PackageReference to a project file:
- [Nuget Package](https://www.nuget.org/packages/Microsoft.AspNetCore.OpenApi/)
- 