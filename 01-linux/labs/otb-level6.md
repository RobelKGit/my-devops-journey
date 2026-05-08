# Lab: OverTheBandit Level 6

## Objective

Find a file stored somewhere on the entire server with all of the following properties:
- Owned by user `bandit7`
- Owned by group `bandit6`
- 33 bytes in size

## Commands Used

```bash
ls                                                        # returned nothing
cd ..                                                     # go to root directory
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null # search entire server
cat /path/to/found/file                                   # read the file
```

## Output

Password for Level 7: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

## Challenges

- `ls` returned nothing. As a result, I navigated to the root.
- Early `find` attempts failed because I didn't specify `-user` and `-group` correctly. Initially, I was typing in - bandit7 - bandit6 
- Permission denied kept being the error recieved. I redirected this standard error using `/dev/null` with `2>/dev/null`
- `sudo` cannot be used in the bandit games so I was unable to ovveride the permission denied output.
- 
## What I Learned

- `find /` searches the entire server starting from root
- `-user` and `-group` filter by file ownership
- `2>/dev/null` suppresses error messages, the useful output I was looking for only appeared as standard output
- Stderr redirection is important in linux to clean the useful output returned on the terminal.
