Semantic search utilizes vector databases to understand and retrieve information based on the meaning and context of the query rather than just matching keywords. This method allows the search engine to grasp the nuances of language, such as synonyms, related concepts, and the overall intent behind a query.

Semantic search excels in environments where user queries are complex, open-ended, or require a deeper understanding of the content. For example, searching for "best smartphones for photography" would yield results that consider the context of photography features in smartphones, rather than just matching the words "best," "smartphones," and "photography."

When providing an LLM with a semantic search function, you typically only need to define a function with a single search query. The LLM will then use this function to retrieve the necessary information. Below is an example of a semantic search function that uses Azure AI Search to find documents similar to a given query.


```csharp
using System.ComponentModel;
using System.Text.Json.Serialization;
using Azure;
using Azure.Search.Documents;
using Azure.Search.Documents.Indexes;
using Azure.Search.Documents.Models;
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.Embeddings;

public class InternalDocumentsPlugin
{
    private readonly ITextEmbeddingGenerationService _textEmbeddingGenerationService;
    private readonly SearchIndexClient _indexClient;

    public AzureAISearchPlugin(ITextEmbeddingGenerationService textEmbeddingGenerationService, SearchIndexClient indexClient)
    {
        _textEmbeddingGenerationService = textEmbeddingGenerationService;
        _indexClient = indexClient;
    }

    [KernelFunction("Search")]
    [Description("Search for a document similar to the given query.")]
    public async Task<string> SearchAsync(string query)
    {
        // Convert string query to vector
        ReadOnlyMemory<float> embedding = await _textEmbeddingGenerationService.GenerateEmbeddingAsync(query);

        // Get client for search operations
        SearchClient searchClient = _indexClient.GetSearchClient("default-collection");

        // Configure request parameters
        VectorizedQuery vectorQuery = new(embedding);
        vectorQuery.Fields.Add("vector");

        SearchOptions searchOptions = new() { VectorSearch = new() { Queries = { vectorQuery } } };

        // Perform search request
        Response<SearchResults<IndexSchema>> response = await searchClient.SearchAsync<IndexSchema>(searchOptions);

        // Collect search results
        await foreach (SearchResult<IndexSchema> result in response.Value.GetResultsAsync())
        {
            return result.Document.Chunk; // Return text from first result
        }

        return string.Empty;
    }

    private sealed class IndexSchema
    {
        [JsonPropertyName("chunk")]
        public string Chunk { get; set; }

        [JsonPropertyName("vector")]
        public ReadOnlyMemory<float> Vector { get; set; }
    }
}
```

https://learn.microsoft.com/en-us/semantic-kernel/concepts/plugins/using-data-retrieval-functions-for-rag