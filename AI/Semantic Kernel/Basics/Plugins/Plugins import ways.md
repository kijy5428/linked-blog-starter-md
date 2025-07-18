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

kernel.CreateFunctionFromPrompt(skPrompt);

```


