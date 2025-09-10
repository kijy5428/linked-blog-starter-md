# Kernel Memory (KM) and SK Semantic Memory (SM)

**Kernel Memory (KM) is a service** built on the feedback received and lessons learned from developing Semantic Kernel (SK) and Semantic Memory (SM). It provides several features that would otherwise have to be developed manually, such as storing files, extracting text from files, providing a framework to secure users’ data, etc. The KM codebase is entirely in .NET, which eliminates the need to write and maintain features in multiple languages. As a service, **KM can be used from any language, tool, or platform, e.g. browser extensions and ChatGPT assistants.**

**Semantic Memory (SM) is a library for C#, Python, and Java** that wraps direct calls to databases and supports vector search. It was developed as part of the Semantic Kernel (SK) project and serves as the first public iteration of long-term memory. The core library is maintained in three languages, while the list of supported storage engines (known as “connectors”) varies across languages.

Here’s comparison table:

|Feature|Kernel Memory|Semantic Memory|
|---|---|---|
|Data formats|Web pages, PDF, Images, Word, PowerPoint, Excel, Markdown, Text, JSON, HTML|Text only|
|Search|Cosine similarity, Hybrid search with filters (AND/OR conditions)|Cosine similarity|
|Language support|Any language, command line tools, browser extensions, low-code/no-code apps, chatbots, assistants, etc.|C#, Python, Java|
|Storage engines|[Azure AI Search](https://azure.microsoft.com/products/ai-services/ai-search), [Elasticsearch](https://www.nuget.org/packages/FreeMindLabs.KernelMemory.Elasticsearch), [MongoDB Atlas](https://www.mongodb.com/atlas/database), [Postgres+pgvector](https://github.com/microsoft/kernel-memory/extensions/postgres), [Qdrant](https://qdrant.tech/), [Redis](https://redis.io/), [SQL Server](https://www.nuget.org/packages/Microsoft.KernelMemory.MemoryDb.SQLServer/), In memory KNN, On disk KNN.|Azure AI Search, Chroma, DuckDB, Kusto, Milvus, MongoDB, Pinecone, Postgres, Qdrant, Redis, SQLite, Weaviate|
|File storage|Disk, [Azure Blobs](https://learn.microsoft.com/azure/storage/blobs/storage-blobs-introduction), [AWS S3](https://aws.amazon.com/s3), [MongoDB Atlas](https://www.mongodb.com/atlas/database), In memory (volatile)|-|
|RAG|Yes, with sources lookup|-|
|Summarization|Yes|-|
|OCR|Yes via [Azure Document Intelligence](https://azure.microsoft.com/products/ai-services/ai-document-intelligence)|-|
|Security Filters|Yes|-|
|Large document ingestion|Yes, including async processing using queues ([Azure Queues](https://learn.microsoft.com/azure/storage/queues/storage-queues-introduction), [RabbitMQ](https://www.rabbitmq.com/), File based or In memory queues)|-|
|Document storage|Yes|-|
|Custom storage schema|some DBs|-|
|Vector DBs with internal embedding|Yes|-|
|Concurrent write to multiple vector DBs|Yes|-|
|LLMs|[Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/concepts/models), [OpenAI](https://platform.openai.com/docs/models), [Anthropic](https://www.anthropic.com/), [Ollama](https://ollama.com/), [LLamaSharp](https://github.com/SciSharp/LLamaSharp), [LM Studio](https://lmstudio.ai/), Semantic Kernel connectors|Azure OpenAI, OpenAI, Gemini, Hugging Face, ONNX, custom ones, etc.|
|LLMs with dedicated tokenization|Yes|No|
|Cloud deployment|Yes|-|
|Web service with OpenAPI|Yes|-|
