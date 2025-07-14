As of today, the function choice behaviors are represented by three static methods of the `FunctionChoiceBehavior` class:

- **Auto**: Allows the AI model to choose from ***zero or more*** function(s) from the provided function(s) for invocation.
- **Required**: Forces the AI model to choose ***one or more function(s)*** from the provided function(s) for invocation.
- **None**: Instructs the AI model not to choose any function(s).


PromptExecutionSettings settings = new() { FunctionChoiceBehavior = FunctionChoiceBehavior.Auto() };