# Lab: OverTheBandit Level 4

## Objective

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.


## Commands Used

```bash
ls                  # list directories
cd inhere           # change into inhere
ls -l               # view file details
file ./*            # check the file type of every file in the directory
cat ./-file07       # read the human-readable file (ASCII text)
```

## Output

Password for Level 5: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

## Challenges

`ls -l` showed the files but didn't reveal which one was human-readable. Had to research the `file` command, which identifies the type of each file (binary, ASCII text, etc.).

## What I Learned

- `file ./*` checks the type of every file in the current directory at once
- ASCII text files are human-readable; other types like binary data are not
- The `file` command is very useful when you don't know what a file contains
