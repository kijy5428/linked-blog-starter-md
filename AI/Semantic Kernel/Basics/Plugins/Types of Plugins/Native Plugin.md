- Let you create customized logics with ease
	- Provide KernelFunction annotation
	- Description to provide the Information for Agent to understand the function
- Tips
	- Because the LLMs are predominantly trained on Python code, it is recommended to use snake_case for function names and parameters (even if you're using C# or Java). This will help the AI agent better understand the function and its parameters.
- You can also provide Description on the Property
	- ![](attachments/Pasted%20image%2020250810074336.png)

https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/adding-native-plugins?pivots=programming-language-csharp

# Provide native code to your agents (C#) – Notes

## Overview

Wrap existing C# code as a native plugin so Semantic Kernel can describe and invoke your functions via function calling. Behind the scenes, Kernel uses your annotations and reflection to expose plugin capabilities to the AI agent.

---

## Semantic Information Required

- name of the plugin
- names of the functions
- descriptions for each function
- parameter names, descriptions, and schema
- return value schema

Semantic Kernel auto-generates most schema details from your code; your focus is on clear semantic descriptions.

---

## Defining a Native Plugin

- start with a C# class
- annotate methods with `[KernelFunction("snake_case_name")]`
- use `[Description("...")]` on methods and parameters to explain intent, inputs, outputs, and side effects
- prefer snake_case naming for functions and parameters to align with model training conventions

### Example: LightsPlugin

```csharp
public class LightsPlugin
{
    private readonly List<LightModel> _lights;
    public LightsPlugin(LoggerFactory loggerFactory, List<LightModel> lights)
    {
        _lights = lights;
    }

    [KernelFunction("get_lights")]
    [Description("Gets a list of lights and their current state")]
    public async Task<List<LightModel>> GetLightsAsync()
    {
        return _lights;
    }

    [KernelFunction("change_state")]
    [Description("Changes the state of the light")]
    public async Task<LightModel?> ChangeStateAsync(LightModel changeState)
    {
        var light = _lights.FirstOrDefault(l => l.Id == changeState.Id);
        if (light == null) { return null; }
        light.IsOn = changeState.IsOn;
        light.Brightness = changeState.Brightness;
        light.Color = changeState.Color;
        return light;
    }
}
```

This illustrates stateless queries (`get_lights`) and state-changing operations (`change_state`).

---

## Parameter and Return Types

Passing a single complex object (e.g., `LightModel` with properties `Id`, `IsOn`, `Brightness`, `Color`) enables Kernel to auto-generate accurate parameter and return schemas and to marshal data into your types.

---

## Registering Plugins with the Kernel

- import by type: `kernel.ImportPluginFromType<YourPlugin>()`
- import by instance: `kernel.ImportPluginFromObject(yourPluginInstance)`

Cloning a kernel per agent lets you inject state or credentials before creating agents.

---

## Using Plugins with Agents

- ChatCompletionAgent requires explicit enabling of function calling:
    
    ```csharp
    new ChatCompletionAgent
    {
        Kernel = agentKernel,
        Arguments = new KernelArguments(
            new OpenAIPromptExecutionSettings
            {
                FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
            })
    };
    ```
    
- OpenAIAssistant agents support automatic function calling by default.

---

## Best Practices

- annotate liberally with `[Description]` to provide semantic clarity
- adopt snake_case for function and parameter names
- organize related capabilities into a single plugin to leverage dependency injection and maintain clean architecture

---

## Next Steps

Decide which capability to expose first—data retrieval, state mutation, or external API integration—and begin class definition and annotation accordingly.
