### Composition
- Markdown cell
- Code cell

## Features
- Magic command
- flowchart rendering
- variable sharing

## Notes book creation
When you install the Polyglot extension, it installs a set of commands available through the Command Palette (**Ctrl + Shift + P**). Each command allows you to carry out a separate activity. Here are some of the commands installed:

- **Polyglot Notebook: Open Notebook**: This command opens a notebook so you can work with it.
- **Polyglot Notebook: Create new blank notebook**: This command creates a new notebook for you and allows you to select your preferred file format and programming language.
- **Polyglot Notebook: Stop all notebook kernels**: This command makes it impossible for you to switch kernels between cells.
- **Polyglot Notebook: Restart the current notebook’s kernel**: This causes all program state and data to be discarded. It's especially useful if the program is in a bad state or hanging. When restarted, you need to rerun all code cells.


## File formats: .dib and .ipynb

The Jupyter notebook file format (.ipynb extension) is a plain-text file and retains not only the input cells, but also the output. It's one of the most common formats for notebooks because it makes it easy to share the file with others and not have to run it to see the output. It especially comes in handy because you could share your notebook, have someone else to run it, and then get it back to see the results. Some common examples are creating notebooks for automating or troubleshooting guides. Being a JSON file, it's hard to track and difficult to inspect changes between files.

The interactive notebook file (.dib extension) is a plain-text file that's easy to read, compare, and share. It never saves output values, which is important when notebooks are used to run code that could evaluate and print secret values like API keys and so on.