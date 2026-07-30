# Challenge 2: File Operations Script

## Objective

Create a script that automates directory and file creation.

## Requirements

- Create a directory called `bash_demo`
- Navigate into the directory
- Create a file called `demo.txt`
- Write text to the file (include current date)
- Display the file contents

## Solution

```bash
#!/bin/bash

mkdir bash_demo
echo "Directory bash_demo has been created"

cd bash_demo
touch demo.txt
echo "File demo.txt has been created"

echo "This file was created by a Bash Script on" $(date) > demo.txt

cat demo.txt
```
