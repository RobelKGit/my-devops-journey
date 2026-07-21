# Lab: Bash Battle Arena — Level 4: File Manipulation

## Objective
Create a script that copies all `.txt` files from the `Arena` directory to a new directory called `Backup`.

## Commands Used
```bash
#!/bin/bash

mkdir -p ~/Backup

write_to_directory () {
  local directory="$1"
  local file_path1="$2"
  local file_path2="$3"
  local file_path3="$4"

  cp "$file_path1" "$file_path2" "$file_path3" "$directory"
}

write_to_directory ~/"Backup" "warrior.txt" "mage.txt" "archer.txt"
```

## Output
A `Backup` directory is created (if it doesn't already exist), and `warrior.txt`, `mage.txt`, and `archer.txt` are copied into it.

## Challenges
Familiarising myself with positional arguments with local variables within functions.

## What I Learned
- `mkdir -p` creates a diretory, only if it does not exist. This avoids duplicate directories being created improving effiency.
- Functions can accept multiple arguments (`$1`, `$2`, `$3`, `$4`...) and can be assigned to variables.
- `cp` can copy multiple files and move them to a directory in one command.
