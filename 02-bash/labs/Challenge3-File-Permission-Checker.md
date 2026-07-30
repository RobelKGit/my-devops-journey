# Challenge 3: File Checker with Permissions

## Objective

Create a script that checks if a file exists and displays its permissions.

## Requirements

- Prompt user for a filename
- Check if the file exists
- If it exists, check if it's readable, writable, and executable
- Display appropriate messages for each permission

## Solution

```bash
#!/bin/bash

echo "Please enter filename : "
read filename

if [ -f $filename ]; then
    echo "File exists"

    if [ -r $filename ]; then
        echo "File is readable"
    else
        echo "File is not readable"
    fi

    if [ -w $filename ]; then
        echo "File is writeable"
    else
        echo "File is not writeable"
    fi

    if [ -x $filename ]; then
        echo "File is executable"
    else
        echo "File is not executable"
    fi
else
    echo "File does not exist"
fi
```
