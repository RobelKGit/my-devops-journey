# Lab: Bash Battle Arena — Level 9: Script to Monitor Directory Changes

## Objective
Write a script that monitors a directory for any changes (file creation, modification, or deletion) and logs the changes with a timestamp.

## Commands Used
```bash
#!/bin/bash

Directory=$1
Log_File=change_log.txt

if [ ! -d $1 ]; then
  echo "This directory does not exist"
  exit 1
fi

fswatch -r $1 | while read change; do
  if [ -e $change ]; then
    echo "$(date "+%Y-%m-%d %H:%M:%S") File modified/created: $change" >> $Log_File
  else
    echo "$(date +'%Y-%m-%d %H:%M:%S') File deleted: $change" >> $Log_File
  fi
done
```

## Output
The specified directory is constantly monitored for any changes within it. The timestamp for these changes is appended to `change_log.txt`.

## Challenges
Researching the fswatch command, learning about the date command and how to combine the two within a conditional if statement.

## What I Learned
- `fswatch -r` recursively watches a directory for filesystem changes and outputs affected paths.
- Piping `fswatch` output into a `while read` loop lets you react to each change individually.
- `date "+%Y-%m-%d %H:%M:%S"` formats a timestamp for logging.
- `>>` appends output to a file
