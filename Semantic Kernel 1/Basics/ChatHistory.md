## Types
- ChatHistory()
	- AddUserMessage(content)
	- AddMessage(Role, content)
## Initialization

```csharp
ChatHistory chatHistory = new ChatHistory("The weather is:\n" + JsonSerializer.Serialize(weather));

```