- [ ] 001
```csharp
#r "nuget: dotenv.net, 3.1.3"

dotenv.net.DotEnv.Load();
var env = dotenv.net.DotEnv.Read();

await memory.ImportDocumentAsync("sample-KM-Readme.pdf", documentId: "doc001");

var question = "What's Kernel Memory?";
var answer = await memory.AskAsync(question);
Console.WriteLine($"Question: {question}\n\nAnswer: {answer.Result}");

Console.WriteLine("Sources:\n");
foreach (var x in answer.RelevantSources)
{
    Console.WriteLine($"  - {x.SourceName}  - {x.Link} [{x.Partitions.First().LastUpdate:D}]");
}
```

- [ ] 002
- [ ] 003