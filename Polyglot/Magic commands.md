
Magic commands are simple commands that do something special, which could be telling time, connecting to data source, or sharing values between cells and kernels. A magic command can take parameters. You can recognize a magic command if the code begins with `#!`, followed by the command as shown:

JavaScriptCopy

```
#!mycommand 
```

In following example, we'd use the `set` command. The `set` command allows us to use a variable between kernels. Here's how to use parameters with the `set` command:

JavaScriptCopy

```
#!set --value @csharp:name --name name
```

This command allows us to use the variable `name` in our C# kernel for operations in our JavaScript kernel.