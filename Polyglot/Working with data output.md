## Working with data output

When you want to output data from a cell, you have a few different techniques you can rely on like:

- **Expression**: In this case, you put the variable on a standalone row like this:
    
    C#Copy
    
    ```
    var name = "Diego";
    name
    ```
    
    In the example, you see how the variable name is placed on the last row and there's no semicolon. Polyglot Notebooks interpret that as an expression rather than a statement (code that is completed with a semicolon at the end).
    
- **Language-specific output**: Depending on then language in which you're writing, the way to output information has a different syntax. Here are two examples of C# and JavaScript, respectively:
    
    C#Copy
    
    ```
    var name = "Diego";
    Console.WriteLine(name);
    ```
    
    Next, Create a separate code cell with JavaScript as the selected kernel:
    
    JavaScriptCopy
    
    ```
    name = "Chris";
    console.log(name)
    ```
    
- **Display command**: To further improve the output, you can use a display helper. When you call the `display`function, it provides a more appealing output. Other benefits of using display helper include:
    
    - You can call it repeatedly. You can, for example, call `Display()` using either of the following code snippets, and each output is shown:
    
    C#Copy
    
    ```
    (1+1).Display();
    name.Display();
    ```
    
    - It reacts to updates. You can assign the result of calling `display` to a reference, and by calling `Update`, the result updates in the cell's output like so:
    
    C#Copy
    
    ```
    var displayRef =  "initial value".Display(); 
    System.Threading.Thread.Sleep(10000); 
    displayRef.Update("different value");
    ```
    
    This code cell shows _initial value_, and 10 seconds later it shows _different value_.