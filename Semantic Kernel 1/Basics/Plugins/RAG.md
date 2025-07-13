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

## Reference data
https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag