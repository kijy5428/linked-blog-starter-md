## Using Plugins for Retrieval Augmented Generation (RAG)

You would need to ask yourself questions before using RAG with plugins

1. How will you (or your AI agent) "search" for the required data? Do you need [semantic search](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#semantic-search) or [classic search](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#classic-search)?
2. Do you already know the data the AI agent needs ahead of time ([pre-fetched data](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#pre-fetched-data-retrieval)), or does the AI agent need to retrieve the data [dynamically](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#dynamic-data-retrieval)?
3. How will you keep your data secure and [prevent oversharing of sensitive information](https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag#keeping-data-secure)?