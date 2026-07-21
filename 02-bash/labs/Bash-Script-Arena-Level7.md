# Lab: Bash Battle Arena — Level 7: File Sorting Script

## Objective
Write a script that sorts all `.txt` files in a directory by size, from smallest to largest, and displays the sorted list.

## Commands Used
```bash
#!/bin/bash

Directory=$1

if [ -d $1 ] ; then
  ls -lh $1/*.txt | sort -k5,5 -h | awk '{print $9, $5}'
else
  echo "Please enter a directory"
fi
```

## Output
Prints filenames and human-readable sizes of all `.txt` files in the given directory, sorted smallest to largest.

## Challenges
Understanding what parameter for the sort command to use to sort the size of the file numerically.

## What I Learned
- `-d` tests whether the argument provided is a directory.
- `sort -k5,5 -h` sorts by the 5th column using human-readable numeric sizes.
- `awk '{print $9, $5}'` prints specific columns. Only the 9th (filename) and 5th (human readable size) columns are printed in this instance.
