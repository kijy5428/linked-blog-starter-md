https://modelcontextprotocol.io/quickstart/server

### Logging in MCP Servers

When implementing MCP servers, be careful about how you handle logging:**For STDIO-based servers:** Never write to standard output (stdout). This includes:

- `print()` statements in Python
- `console.log()` in JavaScript
- `fmt.Println()` in Go
- Similar stdout functions in other languages

Writing to stdout will corrupt the JSON-RPC messages and break your server.**For HTTP-based servers:** Standard output logging is fine since it doesn’t interfere with HTTP responses.

### 

https://modelcontextprotocol.io/quickstart/server#best-practices-4
Best Practices

1. Use a logging library that writes to stderr or files