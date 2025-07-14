As of today, the function choice behaviors are represented by three static methods of the `FunctionChoiceBehavior` class:

- **Auto**: Allows the AI model to choose from ***zero or more*** function(s) from the provided function(s) for invocation.
- **Required**: Forces the AI model to choose ***one or more function(s)*** from the provided function(s) for invocation.
- **None**: Instructs the AI model not to choose any function(s).


```csharp
PromptExecutionSettings settings = new() { FunctionChoiceBehavior = FunctionChoiceBehavior.Auto() };
```

The following table summarizes the effects of various combinations of the AllowParallelCalls and AllowConcurrentInvocation options:

| AllowParallelCalls  | AllowConcurrentInvocation | # of functions chosen per AI roundtrip  | Concurrent Invocation by SK |
|---------------------|---------------------------|-----------------------------------------|-----------------------|
| false               | false                     | one                                     | false                 |
| false               | true                      | one                                     | false*                |
| true                | false                     | multiple                                | false                 |
| true                | true                      | multiple                                | true                  |

`*` There's only one function to invoke