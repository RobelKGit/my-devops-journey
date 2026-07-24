# Piping and Redirections

## Key Concepts

- Piping allows us to pass the output of one command, into the input of another command
- Piping allows us to use the output of one command as the input for another command using the pipe symbol
- Piping within function enable us to perform advanced data operations and store the results in variables
- We can combine piping with other commands or functions to create more complex data manipulation pipelines.

## Commands

- `ls "$directory" | wc -l` -- uses the command ls directory and pipes this into the command wc -l (word count -l)
- `grep "$search_term" log.txt | awk '{ print $2 }'` -- the grep command searches for search_term within the file log.txt, and awk prints the second column of the file using the output of the previous command

## Examples

Get_file_count is the function, get_file_count ./ The current directory (./) is used as the user input hence (Number of files in ./: 13):
```bash
#!/bin/bash

get_file_count() {
    local directory="$1"
    local file_count

    file_count=$(ls "$directory" | wc -l)
    echo "Number of files in $directory: $file_count"
}

get_file_count "./"
```

Function is search_logs, the grep command is used to value of search_term within the file log.txt, awk '{ print $2 }' prints the second column:
```bash
#!/bin/bash

search_logs() {
    local search_term="$1"
    grep "$search_term" log.txt | awk '{ print $2 }'
}

search_logs "ERROR"
```

## What I Learned

Piping allows us to use the output of one command as the input for another command using the pipe symbol. Piping within function enable us to perform advanced data operations and store the results in variables. We can combine piping with other commands or functions to create more complex data manipulation pipelines.
