https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins?pivots=programming-language-csharp

### **Purpose**

Semantic Kernel allows you to integrate existing APIs as plugins using OpenAPI specifications. This enables AI agents to interact with APIs just like other automation services or front-end applications.

---

### **Key Concepts**

#### **1. What is an OpenAPI Plugin?**

An OpenAPI plugin is a wrapper around an API defined by an OpenAPI (Swagger) specification. It allows Semantic Kernel to understand and interact with the API's endpoints, parameters, and expected responses [[1]](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins).

#### **2. Supported OpenAPI Versions**

Semantic Kernel supports OpenAPI versions **2.0 and 3.0**, and can **downgrade 3.1** specifications to 3.0 for compatibility [[1]](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins).

---

### **How to Add an OpenAPI Plugin**

#### **Using a URL**

```CSharp
await kernel.ImportPluginFromOpenApiAsync(
    pluginName: "lights",
    uri: new Uri("https://example.com/v1/swagger.json"),
    executionParameters: new OpenApiFunctionExecutionParameters {
        EnablePayloadNamespacing = true
    }
);
```

#### **Using a Local File**

```CSharp
KernelPlugin plugin = await OpenApiKernelPluginFactory.CreateFromOpenApiAsync(
    pluginName: "lights",
    filePath: "path/to/lights.json"
);
kernel.Plugins.Add(plugin);
```

These methods use the `ImportPluginFromOpenApiAsync` extension method to create and register the plugin [[2]](https://learn.microsoft.com/en-us/dotnet/api/microsoft.semantickernel.openapikernelextensions.importpluginfromopenapiasync?view=semantic-kernel-dotnet).

---

### **Handling Parameters**

Semantic Kernel extracts metadata (name, type, description) from OpenAPI documents and provides it to the LLM. If multiple parameters share the same name, you can manually assign unique argument names to avoid ambiguity [[1]](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins).

Example:

```CSharp
idPathParameter.ArgumentName = "lightId";
idHeaderParameter.ArgumentName = "sessionId";
```

---

### **Handling Payloads**

For operations like POST or PUT that require payloads, Semantic Kernel supports **dynamic payload construction** based on the schema and arguments provided by the LLM[[1]](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins).

---

### **Best Practices**

- Provide **clear semantic descriptions** in your OpenAPI spec to help the AI understand the function.
- Use **namespacing** to avoid parameter conflicts.
- Consider **reusability** by creating plugins once and sharing across multiple agents or kernels.

---

Tips and Tricks

Since OpenAPI specifications are typically designed for humans, you may need to make some alterations to make them easier for an AI to understand. Here are some tips and tricks to help you do that:

|Recommendation|Description|
|---|---|
|**Version control your API specifications**|Instead of pointing to a live API specification, consider checking-in and versioning your Swagger file. This will allow your AI researchers to test (and alter) the API specification used by the AI agent without affecting the live API and vice versa.|
|**Limit the number of endpoints**|Try to limit the number of endpoints in your API. Consolidate similar functionalities into single endpoints with optional parameters to reduce complexity.|
|**Use descriptive names for endpoints and parameters**|Ensure that the names of your endpoints and parameters are descriptive and self-explanatory. This helps the AI understand their purpose without needing extensive explanations.|
|**Use consistent naming conventions**|Maintain consistent naming conventions throughout your API. This reduces confusion and helps the AI learn and predict the structure of your API more easily.|
|**Simplify your API specifications**|Often, OpenAPI specifications are very detailed and include a lot of information that isn't necessary for the AI agent to help a user. The simpler the API, the fewer tokens you need to spend to describe it, and the fewer tokens the AI needs to send requests to it.|
|**Avoid string parameters**|When possible, avoid using string parameters in your API. Instead, use more specific types like integers, booleans, or enums. This will help the AI understand the API better.|
|**Provide examples in descriptions**|When humans use Swagger files, they typically are able to test the API using the Swagger UI, which includes sample requests and responses. Since the AI agent can't do this, consider providing examples in the descriptions of the parameters.|
|**Reference other endpoints in descriptions**|Often, AIs will confuse similar endpoints. To help the AI differentiate between endpoints, consider referencing other endpoints in the descriptions. For example, you could say "This endpoint is similar to the `get_all_lights` endpoint, but it only returns a single light."|
|**Provide helpful error messages**|While not within the OpenAPI specification, consider providing error messages that help the AI self-correct. For example, if a user provides an invalid ID, consider providing an error message that suggests the AI agent get the correct ID from the `get_all_lights` endpoint.|

https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins?pivots=programming-language-csharp#tips-and-tricks-for-adding-openapi-plugins

  
References

[1] [Give agents access to OpenAPI APIs | Microsoft Learn](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-openapi-plugins)

[2] [OpenApiKernelExtensions.ImportPluginFromOpenApiAsync Method (Microsoft ...](https://learn.microsoft.com/en-us/dotnet/api/microsoft.semantickernel.openapikernelextensions.importpluginfromopenapiasync?view=semantic-kernel-dotnet)