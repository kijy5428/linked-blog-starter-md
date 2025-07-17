
https://blog.miniasp.com/post/2022/05/28/Sum-up-ASPNETCORE-Environment-Variables

- ASPNETCORE_ENVIRONMENT
	could be used for environment setting
- ASPNETCORE_URLS
	- dotnet run would by default read the Properties/launchSettings.json's applicationUrl first
	- but for those already published, it would read this environment varaible
	- see [URLs settings](URLs%20settings.md)