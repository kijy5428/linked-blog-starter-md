As of today, the function choice behaviors are represented by three static methods of the `FunctionChoiceBehavior` class:

- **Auto**: Allows the AI model to choose from ***zero or more*** function(s) from the provided function(s) for invocation.
- **Required**: Forces the AI model to choose ***one or more function(s)*** from the provided function(s) for invocation.
- **None**: Instructs the AI model not to choose any function(s).


```csharp
PromptExecutionSettings settings = new() { FunctionChoiceBehavior = FunctionChoiceBehavior.Auto() };
```

---

The following table summarizes the effects of various combinations of the AllowParallelCalls and AllowConcurrentInvocation options:

| AllowParallelCalls  | AllowConcurrentInvocation | # of functions chosen per AI roundtrip  | Concurrent Invocation by SK |
|---------------------|---------------------------|-----------------------------------------|-----------------------|
| false               | false                     | one                                     | false                 |
| false               | true                      | one                                     | false*                |
| true                | false                     | multiple                                | false                 |
| true                | true                      | multiple                                | true                  |

`*` There's only one function to invoke

---

## Supported AI Connectors

As of today, the following AI connectors in Semantic Kernel support the function calling model:

|AI Connector|FunctionChoiceBehavior|ToolCallBehavior|
|---|---|---|
|Anthropic|Planned|❌|
|AzureAIInference|Coming soon|❌|
|AzureOpenAI|✔️|✔️|
|Gemini|Planned|✔️|
|HuggingFace|Planned|❌|
|Mistral|Planned|✔️|
|Ollama|Coming soon|❌|
|Onnx|Coming soon|❌|
|OpenAI|✔️|✔️|

---
## Function Choice Behavior Options

Certain aspects of the function choice behaviors can be configured through options that each function choice behavior class accepts via the `options` constructor parameter of the `FunctionChoiceBehaviorOptions` type. The following options are available:

- **AllowConcurrentInvocation**: This option enables the concurrent invocation of functions by the Semantic Kernel. By default, it is set to false, meaning that functions are invoked sequentially. Concurrent invocation is only possible if the AI model can choose multiple functions for invocation in a single request; otherwise, there is no distinction between sequential and concurrent invocation
    
- **AllowParallelCalls**: This option allows the AI model to choose multiple functions in one request. Some AI models may not support this feature; in such cases, the option will have no effect. By default, this option is set to null, indicating that the AI model's default behavior will be used.
    
    Copy
    
    ```
    The following table summarizes the effects of various combinations of the AllowParallelCalls and AllowConcurrentInvocation options:
    
    | AllowParallelCalls  | AllowConcurrentInvocation | # of functions chosen per AI roundtrip  | Concurrent Invocation by SK |
    |---------------------|---------------------------|-----------------------------------------|-----------------------|
    | false               | false                     | one                                     | false                 |
    | false               | true                      | one                                     | false*                |
    | true                | false                     | multiple                                | false                 |
    | true                | true                      | multiple                                | true                  |
    
    `*` There's only one function to invoke
    ```
    

[](https://learn.microsoft.com/en-us/semantic-kernel/concepts/ai-services/chat-completion/function-calling/function-choice-behaviors?pivots=programming-language-csharp#function-invocation)

---

## Function Invocation

Function invocation is the process whereby Semantic Kernel invokes functions chosen by the AI model. For more details on function invocation see [function invocation article](https://learn.microsoft.com/en-us/semantic-kernel/concepts/ai-services/chat-completion/function-calling/function-invocation).