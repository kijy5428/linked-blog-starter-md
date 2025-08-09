```csharp
OpenAIPromptExecutionSettings openAIPromptExecutionSettings = new()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};
```

Today's LLM models are capable of iteratively calling functions to solve user's need
Especially with the help of function calling

Parallel function calling is also supported by OpenAI models in 1106


https://learn.microsoft.com/en-us/semantic-kernel/concepts/planning?pivots=programming-language-csharp