# Lab: Bash Battle Arena — Level 2: Variables and Loops

## Objective
Create a script that outputs the numbers 1 to 10, one number per line.

## Commands Used
```bash
#!/bin/bash

for (( i=1; i<=10; i++ ))
do
  echo "$i"
done
```

## Output
The numbers 1 through 10 are printed, one per line.

## Challenges
None — task was to create a loop to output numbers 1 to 10 (no number beyond 10).

## What I Learned
- `for (( i=1; i<=10; i++ ))` sets up a loop: The first iteration of `i` starts at 1, the loop continues while `i<=10`, and `i++` increments `i` each iteration.
- The loop stops once `i` exceeds 10.
