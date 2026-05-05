# Data Redirection

## Key Concepts

Three standard streams in Linux:

| Stream | Description |
|--------|-------------|
| **Standard Input (stdin)** | Input you type at the keyboard, passed to a running program |
| **Standard Output (stdout)** | Output a command sends — displayed in terminal by default |
| **Standard Error (stderr)** | Error messages from commands — displayed in terminal by default |

**Example:** When you run `ls`, you type it as stdin and the file list appears as stdout.

## Redirection Operators

```bash
command > file.txt      # redirect stdout to a file (overwrites)
command >> file.txt     # append stdout to a file
command 2> error.txt    # redirect stderr to a file
command &> file.txt     # redirect both stdout and stderr to the same file
```

### Discarding output
```bash
command > /dev/null     # discard stdout
command 2> /dev/null    # discard stderr
command &> /dev/null    # discard everything
cat /dev/null           # always empty — cannot be read
```

## Pipes

Pipes (`|`) pass the output of one command as the input to another.

### Example — Finding the most frequent IP address in a log file

```bash
# Step by step pipeline
cat /home/admin/access.log                                          # view raw log
awk '{print $1}' /home/admin/access.log                            # extract IP addresses (column 1)
awk '{print $1}' /home/admin/access.log | sort                     # sort IPs alphabetically
awk '{print $1}' /home/admin/access.log | sort | uniq -c           # count unique IPs
awk '{print $1}' /home/admin/access.log | sort | uniq -c | sort -nr           # sort by frequency (highest first)
awk '{print $1}' /home/admin/access.log | sort | uniq -c | sort -nr | head -1 # top IP only
awk '{print $1}' /home/admin/access.log | sort | uniq -c | sort -nr | head -1 | awk '{print $2}'  # print just the IP
# Save result to file
awk '{print $1}' /home/admin/access.log | sort | uniq -c | sort -nr | head -1 | awk '{print $2}' > /home/admin/highestip.txt
```

## What I Learned

I have learned that having the ability to chain commands together and direct output wherever you need it is essential for automating tasks and writing scripts.
