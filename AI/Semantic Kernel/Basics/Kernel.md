## Setup

```csharp
builder.AddAzureOpenAIChatCompletion(deploymentName, 
endpoint, apiKey); 

builder.Plugins.AddFromType<WeatherPlugin>();
```
--- 

## Chat

```csharp
kernel.InvokeAsync(promptFunction))
kernel.InvokePromptAsync("Given the current time of day and weather, what is the likely color of the sky in Boston?", new(settings));

await kernel.InvokeAsync(skFun, arguments: new() { { "message", question } });

```