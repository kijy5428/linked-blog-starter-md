## MCP Protocol

### Basics

- Open protocol
- Provide LLM with context
- Provde a standardized way for AI models to connect different data sources / tools

### Benefits
![](attachments/Pasted%20image%2020250715233637.png)

- Community support of resources ready to be plugged in
- Switch between LLM Models
- Security best practices

### Components
![](attachments/Pasted%20image%2020250715233551.png)

#### MCP hosts

	- AI tools (IDE / Clause Desktop)
	- which embed and interact between
		- IDE
		- LLM

### MCP clients

	- Client program

### MCP servers

Lightweight server
3 different types
- Tools
- Resources
- Prompts

### Concepts

### Transport

- Stdio
- http

### Implementations

- MCP server

- Use C# SDK packages
- Use dotnet run to create the MCP server


- MCP client

- Use typescript SDK packages ?!

- Now Claude only support local MCP servers
- ![問題](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAEJSURBVDhPY2RAA8udt6oxMP+tAkp4ALniYMF/DMf+MzFMitzltxLMRwIoBoA0MzL/3g5i/2dgms3EyPABxP73758LIyODB1AsGd0QFigNAUCbQdT/v6yekXu9b4HFIGDGcreNOxj/MeQB2SgGMEFpMGBk+GcLtGUlmmYwYGJk3ABUbQXlwgGKAUCuEtDZj6Ac6oLlbpvaVrhtuAvlwgGaC7ADoOZwoPfyQAELFYIDjGhEB1DNc/8zMB6J3OUPiloUgNcAWLQCNd/GphkE8HuB+c+kf/8YPuPSDAJ4DWBkYHRnYmIohHJJAyDnr3Db9B/KxQlwuoCJ5a8TlDlAYJnLhgsUeYE4wMAAADQ2UW0jvvHhAAAAAElFTkSuQmCC) Questions

- How LLM can access MCP servers exposed items ?? Function calling ??