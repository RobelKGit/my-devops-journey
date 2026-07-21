# Lab: Bash Battle Arena — Level 6: Argument Passing

## Objective
Write a script that accepts a filename as an argument and prints the number of lines in that file. If no filename is provided, display `No file provided`.

## Commands Used
```bash
#!/bin/bash

file=$1

file_name (){
  if [ -z $file ]; then
    echo "No file provided"
  else
    if [ -f $file ]; then
      echo "filename accepted"
      echo "file contains $(wc -l $file) lines"
    else
      echo "file does not exist"
    fi
  fi
}
```

## Output
line count of the file is outputted if the file inputted is recognised. If the file is not recognised, file doesn't exist is returned. If nothing is passed through, no file provided is outputted.

## Challenges
Understanding the difference between checking for an empty argument (`-z`) versus checking for file existence (`-f`) and combining the two within conditonal if statements. 

## What I Learned
- `-z` tests whether the argument provided is empty
- `wc -l` counts the number of lines in a file.
