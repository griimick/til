# Prettify JSON in Vim

Required: Python

Simply run the following command in Vim:
```
:%!python -m json.tool
```

- `:` - Brings you from Normal Mode into Command-Line Mode. Vim now waits for you to enter a command.
- `%` - A symbolic identifier to specify a range. `%` defines a range from the first to the last line of the current buffer. You could also specify line numbers like `2,5` which defines the range from line 2 to line 5. Another possible way to define a range is to use Visual Mode. Simply select your target lines and type `:`. This prepares the command line with `'<,'>`, which is the range definition for “Everything that has been visually selected”.
- `!` - Starting your command with `!` lets you run any shell command from within Vim. Having a range selected before makes the shell using that as standard input stream.
- `python -m json.tool` - The actual shell command. Here we run a Python library module `json.tool` that does the actual task. The output of this command is sent back to the Vim buffer once executed.
