# Get Current Working Directory in Command Mode

Simply add `%:p:h`and hit `Tab` to watch it auto expand.
Use `%:p` to get the full path including the current buffer file name as well.

```
:e %:p:h
```

## Why did I need this?

I use [airblade/vim-rooter](https://github.com/airblade/vim-rooter) along with [FZF](https://github.com/junegunn/fzf) setup in which the cwd is always set to project root irrespective of what file in open in the current buffer. Sometimes when I am in deep nested folder and want to file nearby to the actual cwd, I had to fzf (yes, i ma using fzf as a verb now) to the deep nested path first which is not cool.
So looked for a way to solve this.

## References

- [VIM Fandom Wiki](https://vim.fandom.com/wiki/Set_working_directory_to_the_current_file)
