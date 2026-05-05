# Environment Variables

## Key Concepts

- Variables set in the environment that affect how processes behave
- Store configuration settings and important system information

## Common Environment Variables

| Variable | Meaning |
|----------|---------|
| `PATH` | Directories where the system looks for executable commands |
| `HOME` | The current user's home directory |
| `USER` | The current user's username |
| `SHELL` | The shell program in use |

## Viewing Variables

```bash
printenv              # show all current environment variables
echo $HOME            # access the value of a specific variable ($ dereferences it)
echo $PATH            # show all directories in the PATH
```

## Setting Variables

### Temporary (current session only)
```bash
export JAVA_HOME=/usr/bin/java    # set a variable for this session
echo $JAVA_HOME                   # verify it's set (user/bin/java)
```

### Permanent (survives reboots)
Add the export to your shell config file:

```bash
vim ~/.bashrc         # for Bash users
vim ~/.zshrc          # for Zsh users
```
![alt text](image-1.png)

Add at the bottom:
```bash
export MY_VAR="HELLO WORLD"
export PATH=$PATH:/home/ubuntu    # adds /home/ubuntu to PATH
```

Then reload the config:
```bash
source ~/.bashrc      # or source ~/.zshrc
```

## Aliases

Shortcuts to simplify long or frequent commands.

```bash
alias ll='ls -la'     # temporary alias for current session
```

To make permanent, add the alias to `~/.bashrc` or `~/.zshrc`, then `source` the file.

## Example Script Using Variables

![alt text](image.png)
```bash
#!/bin/bash
# A simple script to greet the user
echo "Hello, $USER! Welcome to $HOSTNAME."
```

```bash
vim greet.sh          # create the script
chmod +x greet.sh     # give it execute permission
./greet.sh            # run it
```

## What I Learned

Environmental variables essentially set the way command tools work. The Path Enviornmental variable is important as it tells the system where to look for executable files
