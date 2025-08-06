### Check the nuget sources

```csharp
dotnet nuget list source

/*
Registered Sources: 1. nuget.org [Enabled] https://api.nuget.org/v3/index.json 2. Microsoft Visual Studio Offline Packages [Enabled] C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\
*/



```

--- 
### Default Nuget config location

%AppData%\NuGet\nuget.config


--- 
### Create a nuget.config 

```csharp

dotnet new nugetconfig

```

--- 
### Others commands

```csharp
# 先移除預設的 nuget 來源
dotnet nuget remove source nuget

# 將一個本機目錄加入到 nuget.config 設定檔中，並取名為 local
dotnet nuget add source "D:\NuGet" -n local

# 將預設的 nuget 來源加入到專案的 nuget.config 設定檔中
dotnet nuget add source "https://api.nuget.org/v3/index.json" -n nuget

```

https://blog.miniasp.com/post/2022/02/15/Manage-NuGet-Source-by-NuGetconfig-file-in-NET

---
