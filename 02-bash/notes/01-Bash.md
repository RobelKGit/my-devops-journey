# Bash

## Key Concepts

- Bash is a command line tool used to interact with your computer.
- Bash scripting is a file containing a series of commands you want the computer to execute automatically.
- Reasons to learn it: automate repetitive tasks, manage systems (files, installs, configuration), and boost efficiency (less typing, more done).
- The **shebang line** (also called a hashbang or interpreter directive) is the first line of a script (e.g. `#!/bin/bash`). It tells the operating system which interpreter/shell should run the script.
- **Comments** are lines that aren't executed — they're informative text for us reading the script. There are single-line comments (`#`) and multi-line comments (`: ' ... '`).
- Comments are useful for functionality, logical purposes of the script and for temporarily disabling commands.
- Scripts can be run from anywhere (without typing the full path) if they're placed in a directory listed in the `PATH` environment variable.

## Commands

- `touch script.sh` - creates an empty file
- `vim script.sh` / `vi script.sh` - opens the file in the vim editor to write the script
- `chmod +x script.sh` - makes the script executable
- `./script.sh` - runs the script from the current directory
- `sh script.sh` - runs the script using the `sh` interpreter
- `bash script.sh` - runs the script using the `bash` interpreter
- `echo $PATH` - prints the list of directories bash searches for executables
- `sudo mv script.sh /usr/local/bin/newname` - moves a script into a PATH directory and changes the name so it can be run from anywhere in the terminal by typing its new name

## Examples

Creating and running your first script:
```
root@ubuntu:~$ touch my-first-script.sh
root@ubuntu:~$ vim my-first-script.sh
root@ubuntu:~$ chmod +x my-first-script.sh
root@ubuntu:~$ ./ myfirstscript
bash: ./: Is a directory
root@ubuntu:~$ ./myfirstscript
bash: ./myfirstscript: No such file or directory
root@ubuntu:~$ ./my-first-script
bash: ./my-first-script: No such file or directory
root@ubuntu:~$ ./my-first-script.sh
Hello World!
root@ubuntu:~$
```

Running a script explicitly with `sh` or `bash`:
```
~$ sh greet.sh
Hello World
~$ bash greet.sh
Hello World
```

Single-line and multi-line comments:
```bash
#!/bin/bash

# Prints greeting to the console
echo "Hello World"

: '
This is a multi-line comment
'
```

Using comments to temporarily disable commands:
```bash
#!/bin/bash

# Renaming all .txt files to .bak
# for file in *.txt; do
# mv "$file" "$(file%.txt).bak"
# done

: '
Explanation:
- Looping through all .txt files in the current directory
- use "mv" command to rename each .txt file to .bak
- The $(file%.txt).bak is the syntax that removes the .txt extension and appends .bak
'
```

Checking the PATH environment variable:
```
~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin:/opt/myapp
```

## What I Learned

Bash scripting enables reptitive tasks to be automated. This boosts effiency and perform complex operations. The shebang line plays a crucial role by telling the Operating System on how to interpret the script. Comments are useful for documenting the script for the user to understand each set of tasks. They are useful for temporarily disabling commands. The PATH is an environmental variable that tells the shell which directories to search for executable files in response to commands. Placing a script into the PATH environmental directory enables the script to be executed from anywhere without specifying the path.
