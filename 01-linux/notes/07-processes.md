# Processes

## Key Concepts

- A process is a running instance of a program
- Every process has a unique **PID** (Process ID)
- You can view, monitor and kill processes from the terminal

## ps aux

Shows a full list of all running processes on the system.

| Flag | Meaning |
|------|---------|
| `a` | Show processes for all users |
| `u` | Display user/owner info |
| `x` | Include processes not attached to a terminal |

```bash
ps aux    # view all running processes
```

### Example output

```
USER    PID   %CPU  %MEM  COMMAND
root    1     0.0   0.1   systemd
root    234   0.1   0.3   sshd
user    567   5.2   1.0   python app.py
```

### Column meanings

| Column | Meaning |
|--------|---------|
| USER | Who started the process |
| PID | Unique process ID |
| %CPU | CPU usage |
| %MEM | Memory usage |
| COMMAND | What is running |

## Killing Processes

```bash
kill -9 <PID>    # force kill a process by its PID
```

>`kill -9` is a hard kill — the process has no chance to clean up. Use it when a process is stuck and won't stop normally.

## What I Learned

Being able to use ps aux, a useful command to view the necessary information about a process. Processes in general are important to see what is running, which allows you to make changes/kill processes when required. 
