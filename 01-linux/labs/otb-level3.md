# Lab: OverTheBandit Level 3

## Objective

The password for the next level is stored in a hidden file in the inhere directory.

## Commands Used

```bash
ls                        # list directories
cd inhere                 # change into inhere directory
ls -la                    # list all files including hidden ones
cat "...Hiding From You"  # read the hidden file
```

## Output

Password for Level 4: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

## Challenges


At first, I ran the ls command to list all directories for the current user. Attempted to use the sudo command to read the contents of the file inhere (sudo cat inhere), this was rhe wrong approach. Later discovered using the manual page (man ls), ls -la results in all directories being listed (including hidden ones). cat "...Hiding From You"  allowed me to the read the contents of this file.  

## What I Learned

- `.` at the beginning of filenames are hidden. The ls command alone does not show them.
- `ls -la` reveals all files including hidden ones
- Current directory is represented by `.`. `..` represents the parent directory.
- Configuration files such as `.bashrc` are mainly hidden files
