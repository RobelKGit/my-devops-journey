# Lab: OverTheBandit Level 5

## Objective

Find a file somewhere under the `inhere` directory that matches all of the following:
- Human-readable
- 1033 bytes in size
- Not executable

## Commands Used

```bash
find -readable -size 1033c ! -executable
```

## Output

Password for Level 6: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

## Challenges

The directory contained 8o files. Manully going through each to find the correct file is not efficient. Took me a while, but through trial and error, the find command is used to identify the file matching the required criteria in the objective  

## What I Learned

- `find` is a powerful command to search for files by criteria thats specified
- `-readable` filters for human-readable files
- `-size 1033c` filters by size in bytes (`c` = bytes)
- `! -executable` excludes executable files (`!` means NOT)
- Combining these filters together leads to the file search to be narrowed down.
