```csharp

#r "nuget: Microsoft.KernelMemory.WebClient"


// we can use below to quickly create envrionment variables
#r "nuget: dotenv.net, 3.1.3"
  
// first create a .env file in the same folder
dotenv.net.DotEnv.Load();
var env = dotenv.net.DotEnv.Read();

```
