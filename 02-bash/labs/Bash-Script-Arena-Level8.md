# Lab: Bash Battle Arena — Level 8: The Multi-file Searcher

## Objective
Create a script that searches for a specific word or phrase across all `.log` files in a directory and outputs the names of the files that contain it.

## Commands Used
```bash
#!/bin/bash

Word=$1
Directory=$2

if [ ! -n $1 ]; then
  echo "No word provided"
  exit 1
elif [ ! -d $2 ] ; then
  echo "Directory does not exist, Please enter a Directory."
  exit 1
else
  grep -rl $1 $2/*.log
fi
```

## Output
Prints the names of `.log` files containing the specified word, or an error message is outputted if the word is invalid/not entered.

## Challenges
Identifying the correct command and paremeter to search for files containing the specific word entered.

## What I Learned
- `! -n` checks for an empty/missing argument.
- `grep -rl` recursively searches files and lists only the filenames containing the specific word.
- `exit 1` stops script execution early when validation fails.
