## Sharing values between code cells

As it stands, you can use what you write in one cell in another cell. For example, if you define an array in code cell, you can use that same array in another cell:

JavaScriptCopy

```
let companies = ["Microsoft", "Apple"]; // a code cell
console.log(companies[0]); // a different code cell, prints "Microsoft"
```

The preceding case isn't what we mean by variable sharing, but a built-in capability. Variable sharing comes into play when you need to share variables between code cells, so let's describe that in the next section.

## Variable sharing

In this scenario, you you want to write some code in C# and some other code in JavaScript, most likely to accomplish different things. Maybe you want the C# code to fetch some data, then use JavaScript to render it differently or use a library that C# doesn't have. Now that we have a use case, how would we make it happen?

### The Set command

To carry out variable sharing, we can use the `set` command. Let's say we have the code written in a C# code cell:

C#Copy

```
var cars = new []{"Saab", "Volvo","BMW" };
Console.WriteLine(cars[0]);
```

To use the `cars` variable in a JavaScript code cell, we need to use the `set` command. First, switch your kernel to JavaScript, then input this code:

JavaScriptCopy

```
#!set --value @csharp:cars --name carsFromCSharp
console.log(carsFromCSharp)
```

Let's summarize what the `set` command does. The `set` command points out which variable to share via `--value @csharp:cars`, then names the variable in the JavaScript cell to `carsFromCsharp`.

The biggest takeaway is that the parameter names are different, but they're otherwise equivalent.

So how do you use the value in the JavaScript cell? Well, we gave it the name `carsFromSharp`, so that's what we's need to refer to:

JavaScriptCopy

```
console.log(carsFromCSharp[0]); // prints "Saab"
```

## Variables view

When you create variables in code cells, there's a UI element—a _variables view_—that keeps track of all variables created. It lists information on the variable like type, value, kernel, and so on. Here's what it looks like:

![A screenshot showing a table that keeps track of all variables created within Polyglot Notebooks and their details.](https://learn.microsoft.com/en-us/training/modules/polyglot-notebooks/media/variable-table-12.png)

From the image, you can see the name of the variable (`cars`), its values (Saab, Volvo, and BMW), its type, and its kernel. The kernel becomes extra interesting, because we also have an **Actions** column that lets you share this particular variable in another cell of a different kernel type.

## User input

To make your code flexible, you might want to rely on user input. You could be asking the user for information on things like configuration, secrets, API keys, and more. Polyglot Notebooks offer a way to collect user input using an `@input` prefix. The idea is that by adding this prefix, the user receives a prompt and can submit their value that's assigned to a specific variable. Here's an example of how it works:

C#Copy

```
#!set --name url --value @input:"Please enter a URL"
```

In the code, the user is prompted for input with the text _Please enter a URL_, and the result is stored in the `url` variable.

## Direct data entry with `#!value`

Another handy functionality is storing values of different types. Imagine you have a few lines of JSON or XML, and you just want to store the value as is. Here's a great prefix you can use for the call: `#!value`. Here's an example:

JavaScriptCopy

```
#!value --name productsJSON
[
    {"id": 1, "name": "video game"},
    {"id": 2, "name": "book"}
]
```

What's great about storing a value as shown is that this variable (`productsJSON`) isn't tied to any specific programming language. Hence, you can use it from different cells with different kernels. You could, for example, use it from a .NET cell or JavaScript cell through variable sharing.