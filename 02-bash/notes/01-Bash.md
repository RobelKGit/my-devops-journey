# Bash

## Key Concepts

- Bash is a command line tool to interact with your computer.
- Bash scripting is a file containing a series of commands you want the computer to execute automatically.
- Why Learn it?
  - Automate tasks -- saves time on repetitive actions
  - Manage Systems -- Handle files, software installs and system configuration
  - Boost Efficiency -- Less typing hence more work gets done
- Bash Scripting allows you to manipulate files, process data and automate backups and perform complex operations.
- The Shebang Line:
  - Common Names -- Shebang, a Hash bang or the interpreted directive.
  - Plays a crucial role in the bash script
  - It is the first line you find in any bash script. #!/bin/bash is at the top and is the shebang line
  - It serves as a directive on how the operating system should interpret the script. (the system interprets it using binary/bash)
  - The path after the exclamation mark is essentially pointing to the specific interpreter or shell that should handle the script.
  - Shebang line allows you to specify the different interpreters or different types of scripts.
  - Example #!/user/bin/python2 . This instructs the operating system to interpret the script using the python interpreter.
  - You can use sh greet.sh or bash greet.sh to run this bash script. If the interpreter within the bash script hasn't been specified, the commands sh and bash are used to tell the operating system to interpret it using bash.
  - To Summarize, the shebang line starts with #! and specifies the interpreter or shell that handles the script. It enables consistent executional scripts across different environments regardless of what shell you're using.
- Comments:
  - Comments are lines in a script that are not executed as part of the code, instead they form as informative text for us reading the script.
  - Adding comments to your scripts are considered a best practice as it gives you and others purpose, functionality and logic of the script.
  - There are two types of comments in bash: Single line comment and multi-line comment
  - # Prints greeting to the console is an example of a single line comment.
  - Single line comments begin with a # (hash symbol)
  - This is a multi-line comment. It starts with: ' and ends in '.
  - Running ./greet.sh will only show Hello World. The comments are not shown as they are not executable. When using cat greet.sh, the comments are shown as it shows the contents of the file.
  - Lines 4-6 were commands but have been temporarily made into comments by adding a Hash in front of command.
  - Comments are useful for temporarily disabling commands.
  - If you run the script ./greet.sh, it will not run as all the commands have been commented.
- Running Scripts from Anywhere:
  - ./ sh bash are three common ways used to run scripts from its current directory
  - To run the script from anywhere without specifying its path, is to place the script in one of the directories within its path environmental variable.
  - The PATH is an environmental variable that tells the shell which directories to search for executable files in response to commands
  - There are several directories separated by colons. This represents the path environmental variable.
  - Any executable file placed in one of these directories can be executed anywhere within the terminal without specifying the path
  - Sudo mv greet.sh /usr/local/bin/greet moves the executable file into the Path enviornmental directory whilst changing the file name to greet.
  - If you type in greet from any directory within the terminal, Hello World is printed out

## Commands

- `touch my-first-script.sh` -- Creates the bash script my-first-script. The .sh at the end makes sure it's a bash script.
- `chmod +x my-first-script.sh` -- Scripts are executables, so this makes it executable
- `./my-first-script.sh` -- runs the script and prints Hello World!
- `sh greet.sh` / `bash greet.sh` -- used to run this bash script if the interpreter within the bash script hasn't been specified
- `echo $PATH` -- shows the path environmental variable
- `sudo mv greet.sh /usr/local/bin/greet` -- moves the executable file into the Path enviornmental directory whilst changing the file name to greet

## Examples

In vim mode, I typed in this at the top #!/bin/bash and 2 lines below echo "Hello World!":
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

Running the script with sh or bash:
```
~$ sh greet.sh
Hello World
~$ bash greet.sh
Hello World
```

Single line comment example (# Prints greeting to the console) and multi-line comment (starts with : ' and ends in '):
```bash
#!/bin/bash

# Prints greeting to the console
echo "Hello World"

: '
This is a multi-line comment
'
```

Lines 4-6 were commands but have been temporarily made into comments by adding a Hash in front of command:
```bash
#!/bin/bash

# Renaming all .txt files to .bak
# for file in *.txt; do
# mv "$file" "$(file%.txt).bak"
# done

: '
Explanation:
- Looping through all .txt files in the current directory
- use 'mv' command to rename each .txt file to .bak
- The $(file%.txt).bak is the syntax that removes the .txt extension and appends .bak
'
```

There are several directories separated by colons. This represents the path environmental variable:
```
~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin:/opt/myapp
```

## What I Learned

To Summarize, the shebang line starts with #! and specifies the interpreter or shell that handles the script. It enables consistent executional scripts across different environments regardless of what shell you're using. Comments are useful for temporarily disabling commands, and give you and others purpose, functionality and logic of the script. Any executable file placed in one of the directories within the PATH environmental variable can be executed anywhere within the terminal without specifying the path.
