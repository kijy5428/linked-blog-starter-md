- [Supported AI models](https://learn.microsoft.com/en-us/semantic-kernel/get-started/quick-start-guide?pivots=programming-language-csharp)
- [Supported AI Services](https://learn.microsoft.com/en-us/semantic-kernel/concepts/ai-services/)

### ChatCompletion
- IChatCompletionService

```csharp
 IChatCompletionService chatCompletion = kernel.GetRequiredService<IChatCompletionService>();
 ```
```csharp
ChatResponse response = await chatCompletion.GetChatMessageContentAsync( chatHistory, executionSettings: openAIPromptExecutionSettings, kernel: kernel)
```

