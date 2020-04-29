# Auto Reloading file on external change in Vim

Running the following oneliner command or putting each command separately in `.vimrc` should do the job,

```
:set autoread | au CursorHold * checktime | call feedkeys("lh")
```

**Explanation:**
- `autoread`: reads the file when changed from the outside (but it doesnt work on its own, there is no internal timer or something like that. It will only read the file when vim does an action, like a command in ex `:!`.
- `CursorHold * checktime`: when the cursor isn't moved by the user for the time specified in 'updatetime' (which is 4000 miliseconds by default) checktime is executed, which checks for changes from outside the file.
- `call feedkeys("lh")`: the cursor is moved once, right and back left. and then nothing happens (... which means, that CursorHold is triggered, which means we have a loop).


What was the purpose of me looking for the above tip?
- I use file read/write for IO in competetive programming. So, I used to open two both `input.txt` and `output.txt` in Vim. But when I used to run the compiler and execute the program, I wanted `output.txt` to automatically reload on change. 
