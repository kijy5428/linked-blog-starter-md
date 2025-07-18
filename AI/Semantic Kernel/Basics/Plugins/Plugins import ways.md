## Different ways of Import
```csharp
kernel.Plugins.AddFromType<XYZ>("xyz");

kernel.ImportPluginFromObject(
	new MemoryPlugin(
		memoryConnector, 
		defaultIndex: "LawSK", 
		waitForIngestionToComplete: true
		), 
		"memory"
	);

var myFunction = kernel.CreateFunctionFromPrompt(skPrompt);
var answer = await myFunction.InvokeAsync(kernel,

    "any news from NASA about Orion?");

  

Console.WriteLine(answer);
```


