# Lab: Bash Battle Arena — Level 3: Conditional Statements

## Objective
Check if a file named `hero.txt` exists in the `Arena` directory. If it does, print `Hero found!`; otherwise, print `Hero missing!`.

## Commands Used
```bash
#!/bin/bash

if [ -f Arena/hero.txt ];
then
  echo "Hero found!"
else
  echo "Hero missing"
fi
```

## Output
Prints `Hero found!` if the file exists, or `Hero missing` if it does not.

## Challenges
How to provide a solution for this question. Understanding the -f flag checks to see if the file exists is important. I was previously not aware of this.

## What I Learned
- The `-f` flag in a test (`[ -f file ]`) checks whether a regular file exists.
