# Lab: Bash Battle Arena — Level 10: Boss Battle 2 — Immediate Scripting

## Objective
Write a script that:
1. Creates a directory called `Arena_Boss`.
2. Creates 5 text files inside it, named `file1.txt` to `file5.txt`.
3. Generates a random number of lines (between 10 and 20) in each file.
4. Sorts the files by size and displays the list.
5. Checks if any file contains the word `Victory`, and if found, moves it to a directory called `Victory_Archive`.

## Commands Used
```bash
#!/bin/bash

mkdir ~/Arena/Arena_Boss
mkdir ~/Arena/Victory_Archive

for (( i=1 ; i<=5 ; i++ ))
do
  touch ~/Arena/Arena_Boss/file$i.txt
  lines=$((RANDOM % 11 + 10))
  for (( j=1 ; j<=$lines ; j++ ))
  do
    echo "This is line $j" >> ~/Arena/Arena_Boss/file$i.txt
  done
done

echo "Files sorted by size"
ls -lh ~/Arena/Arena_Boss/file*.txt | sort -k5,5 -h | awk '{print $2, $5}'

for file in ~/Arena/Arena_Boss/*.txt
do
  if grep -q Victory $file ; then
    mv $file ~/Arena/Victory_Archive
  else
    echo "File does not contain the word Victory"
  fi
done
```

## Output
Creates `Arena_Boss` with 5 files each containing 10–20 random lines, prints those files sorted by size, and moves any file containing "Victory" into `Victory_Archive`.

## Challenges
Combining nested loops (outer loop for files, inner loop for lines) with random number generation and a final search-and-move step.
Understanding the RANDOM and how to generate numbers within the range  11-20.

## What I Learned
- `$RANDOM` generates a pseudo-random number; `% 11 + 10` constrains it to a range of 10–20.
- Nested loops let you generate variable, randomized content across multiple files.
- `grep -q` performs a silent (no output) search.
- This exercise tied together directory creation, loops, randomization, sorting, and conditional file operations from all previous levels.
