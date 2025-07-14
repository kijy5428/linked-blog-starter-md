## Using Plugins for Retrieval Augmented Generation (RAG)

You would need to ask yourself questions before using RAG with plugins

1. How will you (or your AI agent) "search" for the required data? Do you need [semantic search](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#semantic-search) or [classic search](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#classic-search)?
2. Do you already know the data the AI agent needs ahead of time ([pre-fetched data](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#pre-fetched-data-retrieval)), or does the AI agent need to retrieve the data [dynamically](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#dynamic-data-retrieval)?
3. How will you keep your data secure and [prevent oversharing of sensitive information](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#keeping-data-secure)?

--- 
## When to Use Each

Choosing between semantic and classic search depends on the nature of the query. It is ideal for content-heavy environments like knowledge bases and customer support where users might ask questions or look for products using natural language. 
- **Classic search**
	- should be employed when precision and exact matches are important.
- **Semantic Search:** 
	- It is ideal for content-heavy environments like knowledge bases and customer support where users might ask questions or look for products using natural language. 

In some scenarios, you may need to combine both approaches to provide comprehensive search capabilities. For instance, a chatbot assisting customers in an e-commerce store might use semantic search to understand user queries and classic search to filter products based on specific attributes like price, brand, or availability.

Below is an example of a plugin that combines semantic and classic search to retrieve product information from an e-commerce database.

---
## Dynamic vs pre-fetched data retrieval

When developing plugins for Retrieval Augmented Generation (RAG), you must also consider whether the data retrieval process is static or dynamic. This allows you to optimize the performance of your AI agents by retrieving data only when necessary.

[](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#dynamic-data-retrieval)

### Dynamic data retrieval

In most cases, the user query will determine the data that the AI agent needs to retrieve. For example, a user might ask for the difference between two different products. The AI agent would then need to dynamically retrieve the product information from a database or API to generate a response using [function calling](https://learn.microsoft.com/en-us/semantic-kernel/concepts/ai-services/chat-completion/function-calling/). It would be impractical to pre-fetch all possible product information ahead of time and give it to the AI agent.

Below is an example of a back-and-forth chat between a user and an AI agent where dynamic data retrieval is necessary.

|Role|Message|
|---|---|
|🔵 **User**|Can you tell me about the best mattresses?|
|🔴 **Assistant (function call)**|`Products.Search("mattresses")`|
|🟢 **Tool**|`[{"id": 25323, "name": "Cloud Nine"},{"id": 63633, "name": "Best Sleep"}]`|
|🔴 **Assistant**|Sure! We have both Cloud Nine and Best Sleep|
|🔵 **User**|What's the difference between them?|
|🔴 **Assistant (function call)**|`Products.GetDetails(25323)` `Products.GetDetails(63633)`|
|🟢 **Tool**|`{ "id": 25323, "name": "Cloud Nine", "price": 1000, "material": "Memory foam" }`|
|🟢 **Tool**|`{ "id": 63633, "name": "Best Sleep", "price": 1200, "material": "Latex" }`|
|🔴 **Assistant**|Cloud Nine is made of memory foam and costs $1000. Best Sleep is made of latex and costs $1200.|

[](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#pre-fetched-data-retrieval)

### Pre-fetched data Retrieval

Static data retrieval involves fetching data from external sources and _always_ providing it to the AI agent. This is useful when the data is required for every request or when the data is relatively stable and doesn't change frequently.

Take for example, an agent that always answers questions about the local weather. Assuming you have a `WeatherPlugin`, you can pre-fetch weather data from a weather API and provide it in the chat history. This allows the agent to generate responses about the weather without wasting time requesting the data from the API.

C#Copy

```
using System.Text.Json;
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;

IKernelBuilder builder = Kernel.CreateBuilder();
builder.AddAzureOpenAIChatCompletion(deploymentName, endpoint, apiKey);
builder.Plugins.AddFromType<WeatherPlugin>();
Kernel kernel = builder.Build();

// Get the weather
var weather = await kernel.Plugins.GetFunction("WeatherPlugin", "get_weather").InvokeAsync(kernel);

// Initialize the chat history with the weather
ChatHistory chatHistory = new ChatHistory("The weather is:\n" + JsonSerializer.Serialize(weather));

// Simulate a user message
chatHistory.AddUserMessage("What is the weather like today?");

// Get the answer from the AI agent
IChatCompletionService chatCompletionService = kernel.GetRequiredService<IChatCompletionService>();
var result = await chatCompletionService.GetChatMessageContentAsync(chatHistory);
```

[](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#keeping-data-secure)

## Keeping data secure

When retrieving data from external sources, it is important to ensure that the data is secure and that sensitive information is not exposed. To prevent oversharing of sensitive information, you can use the following strategies:

|Strategy|Description|
|---|---|
|**Use the user's auth token**|Avoid creating service principals used by the AI agent to retrieve information for users. Doing so makes it difficult to verify that a user has access to the retrieved information.|
|**Avoid recreating search services**|Before creating a new search service with a vector DB, check if one already exists for the service that has the required data. By reusing existing services, you can avoid duplicating sensitive content, leverage existing access controls, and use existing filtering mechanisms that only return data the user has access to.|
|**Store reference in vector DBs instead of content**|Instead of duplicating sensitive content to vector DBs, you can store references to the actual data. For a user to access this information, their auth token must first be used to retrieve the real da|
## Reference data
https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag