# Environment & Path

## Key Concepts

- Change PATH Permanently:
  - The path environment variable is a critical system variable that specifies the directories where the shell should look for executable files.
  - Sometimes we add our own directories to PATH, particularly when installing new software, or when we want our own scripts and binaries to be available system wide
  - A directory is made my_scripts
  - Using vim, a bash script is made within this directory and contains the shebang line along with echo "Hello World!"
  - Chmod +x to make this file executable.
  - The next step is to add the directory to the PATH variable.
  - Key Note: Changes to path made in the terminal are temporary and get lost when the shell session ends.
  - echo "export PATH=$PATH:~/my_scripts " >> ~/.zshrc this adds my_scripts directory to the PATH (the variable the shell looks checks when a command is inputted).
  - Source ~/.zshrc -this reloads the zshrc file so that it is permanently changes to reflect the changes.
  - This example is shown below in the example section. 
- Reading Environmental Variables:
  - Environmental Variables allow us to store and retrieve important information within our bash script.
  - Environment Variables are like containers that hold valuable information for our scripts.
  - Provides a way to store settings and configurations that our scripts can access when needed.
  - How to read environmental variables within bash scripts. To access the value of an environmental variable, we use the variable name propended by a dollar sign.
  - echo "Home Directory: $HOME" - $HOME is the environmental variable of the home directory of the current user
  - echo "Current user: $USER" - $USER is the environment variable of the current user
  - echo "OS Type: $OSTYPE" - $OSTYPE is the environment variable of the operating system
  - You can assign local variables to environment variables
- Standard Environment Variables:
  - Standard Environment Variables give us valuable insights into various aspects of the system, user and runtime environment.
  - They provide information that can help us create more robust and adaptable bash scripts.
  - Common standard environment variables
  - $LOGNAME -- searches the login name for the current user
  - $SHELL - Shell environment variable stores the PATH of the current user's shell
  - $PWD -- prints the current working directory
  - Other commonly used standard environment variables include PATH for the systems executable search paths and LANG for the default language setting
  - Echo "Executable Paths: $PATH" -- this prints out the different executable search paths and where the binaries are located.
  - Echo "Default Language: $LANG" -- This prints the default language
  - Summary:
    - We can access the values of environment variables using the variable name proceeded by a dollar sign.
    - Assigning environment variables to local variables makes our code easy to read and work with.
    - Standard Environment Variable provide valuable information about the system, user and runtime environment.
- Reading Files:
  - Reading files allows us to access and extract valuable information from different types of files.
  - Different methods to read files:
  - Method 1- Simple redirection -- We have a function called read_file. In the body of the function, we have a local variable (file_path) which is equal to the first parameter ($1).
  - Within the while loop we have the read command which reads each line of the file.
  - While loops ensure the lines consistently get read
  - IFS ensures trailing and trading white spaces characters are preserved.
  - read ensures each lines of the file are read.
  - -r option ensures back slashes are not interpreted as escape characters.
  - echo "$line" -- for each iteration, each line that is read is outputted.
  - done < "$file_path" -- feeds this file into the loop to read each line
  - read_file ./log.txt - ./log.txt is the first parameter ($1). This Is the file that is being read.
  - Method 2 -- Using the cat command
  - Function defined (process_file)
  - Within the body local variable file_path=$1
  - cat "$file_path -- each line is read and printed once it is piped into the while loop.
  - Summary:
    - Redirection and the while loop can be used to read the file contents line by line
    - Cat command be used to read the contents of a file and piped for further processing.
- Writing Files:
  - Writing files in a bash script within a function.
  - Writing files allows us to create, modify and store information in various formats.
  - Function is called write_to_file
  - Within the body of the function, we have two local variables (local file_path="$1" and local data="$2")
  - echo "data" > "$file_path" the contents of data (using echo "data") is redirected using the greater than symbol (>) into the first parameter (first argument) passed in by the user.
  - Write_to_file "read.txt" "Hello World" the function is written alongside the two parameters.
  - Once run, in the terminal cat read.txt prints Hello World.
  - To append information within a file, use the greater than symbol twice >>.
- File Checksums:
  - File checksums are cryptographic hashes that provide a unique fingerprint for a file which allows us to verify the authenticity of the file.
  - Every file has a file checksum which differs from one another.
  - MD five sum command is used to generate file checksums.
  - Function is called calculate_md5sum
  - Local variable is the local file_path which is equal to $1.
  - We use md5sum to generate the file checksum of the file path.
  - The function is called along with the first parameter read.txt
  - Sha256 is another common algorithm used for file checksums.
  - Checksums are useful for checking the integrity of a file overtime or across different systems so we can use it to compare two different checksums and see if their values match.
  - Function is compare_checksums
  - Within the function, we have the local variable checksum1=$1 and checksum2=$2.
  - Using the if statement we use double square brackets. This allows advanced conditional expressions in bash.
  - If checksum1 is equal to checksum2, then Checksums match, File is intact is returned
  - If they do not match, Checksums do not match. File integrity comprised is returned.
  - Summary:
    - File Checksums can be generated using various algorithms such as commands like md5sum and sha256sum
    - You have to install the commands when using it in Bash.
    - Comparing checksum value allows us to check the authenticity and integrity of a file.

## Commands

- `echo "export PATH=$PATH:~/my_scripts " >> ~/.zshrc` -- adds my_scripts directory to the PATH
- `source ~/.zshrc` -- reloads the zshrc file so that it is permanently changes to reflect the changes
- `echo "Home Directory: $HOME"` -- $HOME is the environmental variable of the home directory of the current user
- `echo "Current user: $USER"` -- $USER is the environment variable of the current user
- `echo "OS Type: $OSTYPE"` -- $OSTYPE is the environment variable of the operating system
- `$LOGNAME` -- searches the login name for the current user
- `$SHELL` -- stores the PATH of the current user's shell
- `$PWD` -- prints the current working directory
- `while IFS= read -r line; do ... done < "$file_path"` -- reads each line of the file
- `echo "data" > "$file_path"` -- redirected using the greater than symbol (>) into the first parameter
- `>>` -- To append information within a file, use the greater than symbol twice
- `md5sum "$file_path"` -- generate the file checksum of the file path

## Examples

A directory is made my_scripts, using vim a bash script is made within this directory, chmod +x to make this file executable:
```
~$ mkdir my_scripts
~$ vi my_scripts/hello_world.sh
~$ chmod +x my_scripts/hello_world.sh
```

echo "export PATH=$PATH:~/my_scripts" >> ~/.zshrc adds my_scripts directory to the PATH, source ~/.zshrc reloads the file:
```
~$ echo "export PATH=$PATH:~/my_scripts" >> ~/.zshrc
~$ source ~/.zshrc

~$ hello_world.sh
Hello World
```

echo "Home Directory: $HOME" - $HOME is the environmental variable of the home directory of the current user:
```bash
#!/bin/bash

echo "Home Directory: $HOME"
echo "Current user: $USER"
echo "OS Type: $OSTYPE"
```
Output:
```
Home Directory: /Users/abdurahmanabukar
Current user: abdurahmanabukar
OS Type: darwin21
```

You can assign local variables to environment variables:
```bash
#!/bin/bash

my_home="$HOME"
my_user="$USER"
my_os="$OSTYPE"

echo "Home Directory: $my_home"
echo "Current user: $my_user"
echo "OS Type: $my_os"
```

$LOGNAME searches the login name for the current user, $SHELL stores the PATH of the current user's shell, $PWD prints the current working directory:
```bash
#!/bin/bash

echo "Username: $LOGNAME"
echo "Shell: $SHELL"
echo "Current Directory: $PWD"
```
Output:
```
Username: abdurahmanabukar
Shell: /bin/zsh
Current Directory: (current path)
```

Other commonly used standard environment variables include PATH for the systems executable search paths and LANG for the default language setting:
```bash
#!/bin/bash

echo "Executable Paths: $PATH"
echo "Default Language: $LANG"
```

Method 1- Simple redirection -- We have a function called read_file. Within the while loop we have the read command which reads each line of the file:
```bash
#!/bin/bash

read_file() {
    local file_path="$1"

    while IFS= read -r line; do
        echo "$line"
    done < "$file_path"
}

read_file "./log.txt"
```

Method 2 -- Using the cat command. Function defined (process_file), cat "$file_path" -- each line is read and printed once it is piped into the while loop:
```bash
#!/bin/bash

process_file() {
    local file_path="$1"

    cat "$file_path" | while IFS= read -r line
    do
        echo "Processing line: $line"
        # additional processing logic
    done
}

process_file "./log.txt"
```

Function is called write_to_file. echo "data" > "$file_path" the contents of data is redirected using the greater than symbol into the first parameter:
```bash
#!/bin/bash

write_to_file() {
    local file_path="$1"
    local data="$2"

    echo "$data" > "$file_path"
}

write_to_file "read.txt" "Hello World"
```
Terminal: cat read.txt prints Hello World.

Function is called calculate_md5sum. We use md5sum to generate the file checksum of the file path:
```bash
#!/bin/bash

calculate_md5sum() {
    local file_path="$1"
    md5sum "$file_path"
}

calculate_md5sum "read.txt"
```

Function is compare_checksums. If checksum1 is equal to checksum2, then Checksums match, File is intact is returned:
```bash
#!/bin/bash

compare_checksums() {
    local checksum1="$1"
    local checksum2="$2"

    if [[ "$checksum1" == "$checksum2" ]]; then
        echo "Checksums match. File is intact"
    else
        echo "Checksums do not match. File integrity compromised"
    fi
}

compare_checksums "123" "1234"
```

## What I Learned

We can access the values of environment variables using the variable name proceeded by a dollar sign, and assigning environment variables to local variables makes our code easy to read and work with. Standard Environment Variables provide valuable information about the system, user and runtime environment. Redirection and the while loop can be used to read the file contents line by line, and the cat command can be used to read the contents of a file and piped for further processing. File Checksums can be generated using various algorithms such as commands like md5sum and sha256sum (you have to install the commands when using it in Bash), and comparing checksum value allows us to check the authenticity and integrity of a file.
