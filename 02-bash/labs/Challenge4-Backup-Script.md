# Challenge 4: Backup Script for Text Files

## Objective

Create a script that backs up all `.txt` files from one directory to another.

## Requirements

- Prompt user for source directory
- Create a backup directory if it doesn't exist
- Copy all `.txt` files to the backup directory
- Add timestamp to backup directory name
- Display count of files backed up

## Solution

```bash
#!/bin/bash

echo "Please enter a directory : "
read directory

backup_directory="backup_$(date +%Y-%m-%d)"

if [ -d $directory ]; then
    mkdir -p $backup_directory
    echo "The backup directory $backup_directory was created on $(date)"

    cp $directory/*.txt $backup_directory
    echo "files backed up : $(ls $backup_directory/*.txt | wc -l)"
else
    echo "Please enter valid directory name"
fi
```
