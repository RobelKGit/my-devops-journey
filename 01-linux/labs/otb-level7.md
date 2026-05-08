# Lab: OverTheBandit Level 7

## Objective

Find the password stored in `data.txt` next to the word `millionth`.

## Commands Used

```bash
ls                  # list files
vim data.txt        # open the file in vim
/millionth          # search for the word in vim command mode
```

## Output

Password for Level 8: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

## Challenges

The file was too large to read manually with `cat`.

## What I Learned

- `vim` can open and search large files efficiently
- In Vim command mode, `/word` searches forward for the specified word. /millionth locates the word millionth.
- `grep "millionth" data.txt` is an alternative method to search for the word millionth to get the password.
