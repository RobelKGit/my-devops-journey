# Error Handling and Exit Codes

## Key Concepts

- Introduction to Error Handling:
  - Error handling is about foreseeing where things can go wrong in scripts and taking appropriate measures rather than letting things crash or continuing in an erroneous state.
  - Effective error handling can save you a lot of time, making your scripts trustworthy and reliable.
- Exit Codes:
  - Whenever a command or script ends, it returns an exit code to the system.
  - This is a numerical value representing whether the command or script is completed successfully or not.
  - In general, exit codes of zero indicate success. Exit codes of non-zero indicate an error.
  - After a command in the terminal is entered (whether successful or not), enter echo $? to get the exit code.
- Set -e:
  - When using set-e at the start of a script, the script will stop executing as soon as any command returns a non-zero exit code.
  - set -e is at the top of the script.
  - Set -e allows us to catch errors as soon as they occur and prevent unexpected behaviour as a result of unhandled errors.
- Set -u:
  - Set -u option forces a bash script to stop if it encounters an uninitialized variable (undefined variable).
  - It prevents scenarios where missing data can lead to incorrect results or unexpected behaviour.
  - The script stops executing when it encounters the uninitialized variable X (the variable that has not been defined).
  - Summary: Set -u stops your scripts from running into problems due to missing data.
- Set -x:
  - Set -x -- this command prints each command that will be executed to the terminal before its actually executed.
  - It helps with following the flow of your script.
  - set -x at the top
  - Set -x enables each command to be printed before its executed (notated with a + at the start of each command)
  - Set +x allows the rest of the commands beyond this point to be executed without being debugged.
  - This is useful for helping you debug a certain part of your script.
- Set -eux:
  - Bash scripts enables us to combine set -e, set -u and set -x to be used in one script (set -eux)
  - Set -e will stop the correct due to an error
  - Set -u will stop the script to an un initialized variable.
  - Set x -- will print each command before execution
  - Each command is printed before execution.
  - This makes the script easier to debug and safer to use, preventing the propagation of errors.
- More set Commands:
  - Set -o nounset -- this command is essentially the same as set -u. It prevents the script executing any uninitialized variables.
  - Set -o errexit -- works the same way as set -e. It causes the shell to exit if any invoked command fails.
  - Set -o pipefail -- this causes the pipeline to return the exit status of the last command in the pipeline that exited with a non-zero status. Useful when piping commands together.
  - The cat command fails because the file doesn't exist.
  - Using set -o pipefail, this failure is propagated and causes the entire pipeline to fail (grep "something" doesn't not get executed)

## Commands

- `echo $?` -- After a command in the terminal is entered (whether successful or not), enter this to get the exit code
- `command -v git 2>/dev/null` -- Command -v essentially searches if a command exists
- `set -e` -- the script will stop executing as soon as any command returns a non-zero exit code
- `set -u` -- forces a bash script to stop if it encounters an uninitialized variable
- `set -x` -- prints each command that will be executed to the terminal before its actually executed
- `set +x` -- allows the rest of the commands beyond this point to be executed without being debugged
- `set -eux` -- combines set -e, set -u and set -x to be used in one script
- `set -o nounset` -- essentially the same as set -u
- `set -o errexit` -- works the same way as set -e
- `set -o pipefail` -- causes the pipeline to return the exit status of the last command in the pipeline that exited with a non-zero status

## Examples

Here, num1 divided by num2 cannot be performed as any number divided by 0 is not mathematically solvable, this results in the script to crash:
```bash
#!/bin/bash

num1=10
num2=0

result=$((num1 / num2))

echo "The result is: $result"
```
Output:
```
error_handling.sh: line 11: num1 / num2: division by 0 (error token is "2")
The result is:
```

Using if statement, specifying the condition that if $num2 -eq 0, then print Error: Division by zero is not allowed:
```bash
#!/bin/bash

num1=10
num2=0

if [ $num2 -eq 0 ]; then
    echo "Error: Division by zero is not allowed"
    exit 1
fi

result=$((num1 / num2))

echo "The result is: $result"
```

The variable FILE is set to a file /nonexistent, if [[ -f "$FILE" ]]; then checks if the file exists:
```bash
#!/bin/bash

FILE="/nonexistent"

if [[ -f "$FILE" ]]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```
Output: File does not exist.

Command -v git 2>/dev/null searches if a command exists, if [[ $? -ne 0 ]] checks if the exit code is not equal to zero:
```bash
#!/bin/bash

command -v git 2>/dev/null

if [[ $? -ne 0 ]]; then
    echo "git is not installed. Please install git."
    exit 1
else
    echo "git is installed"
fi
```
Output:
```
/opt/homebrew/bin/git
git is installed
```

set -e is at the top of the script. Echo "Before the script" is printed. The command nonexistentcommand does not exist:
```bash
#!/bin/bash

set -e

echo "Before the script"

nonexistentcommand

echo "After the script"
```
Output:
```
Before the script
error_handling.sh: line 7: nonexistentcommand: command not found
```

The script stops executing when it encounters the uninitialized variable X:
```bash
#!/bin/bash

set -u

echo "The value of variable X is: $X"
```
Output: error_handling.sh: line 5: X: unbound variable

X and Y variables have the respective values 10 and 20. Z is equal to x+y+w. W has not been initialized:
```bash
#!/bin/bash

set -u

X=10
Y=20
Z=$((X + Y + W))
echo "Z equals: $Z"
```
Output: error_handling.sh: line 7: W: unbound variable

set -x at the top. A string is being printed (echo "This is a test"). Each command is printed before it is executed:
```bash
#!/bin/bash

set -x

echo "This is a test."
X=10
echo "The value of X is: $X"
```
Output:
```
+ echo 'This is a test.'
+ X=10
This is a test.
The value of X is: 10
+ echo 'The value of X is: 10'
```

Set +x allows the rest of the commands beyond this point to be executed without being debugged:
```bash
#!/bin/bash

set -x

echo "Starting the script."
X=10
Y=20
Z=$((X + Y))
echo "The value of Z is: $Z"

set +x

echo "After the script."
```
Output:
```
+ echo 'Starting the script.'
+ X=10
+ Y=20
+ Z=30
+ echo 'The value of Z is: 30'
Starting the script.
The value of Z is: 30
+ set +x
After the script.
```

Bash scripts enables us to combine set -e, set -u and set -x to be used in one script (set -eux). Nonexistentcommand is not a command and due to set -e this will not be executed or be printed before execution:
```bash
#!/bin/bash

set -eux

echo "This is a test."
X=10
echo "The value of X is: $X"

nonexistentcommand
```
Output:
```
+ echo 'This is a test.'
+ X=10
+ echo 'The value of X is: 10'
This is a test.
The value of X is: 10
+ nonexistentcommand
error_handling.sh: line 9: nonexistentcommand: command not found
```

Set -o errexit works the same way as set -e:
```bash
#!/bin/bash

set -o errexit

echo "This is a test"

nonexistentcommand

echo "This is another test"
```
Output:
```
This is a test
error_handling.sh: line 7: nonexistentcommand: command not found
```

The cat command fails because the file doesn't exist. Using set -o pipefail, this failure is propagated and causes the entire pipeline to fail (grep "something" doesn't not get executed):
```bash
#!/bin/bash

set -o pipefail

cat nonexistentfile | grep "something"
```
Output: cat: nonexistentfile: No such file or directory

## What I Learned

Set -e allows us to catch errors as soon as they occur and prevent unexpected behaviour as a result of unhandled errors -- though not all non-zero exit codes are indicative of errors that should stop your script, so in that instance you don't use set -e. Set -u stops your scripts from running into problems due to missing data. Set -x enables each command to be printed before its executed (notated with a + at the start of each command), which helps with following the flow of your script, and set +x allows the rest of the commands beyond that point to run without being debugged. Combining set -e, set -u and set -x into set -eux makes the script easier to debug and safer to use, preventing the propagation of errors. Set -o pipefail is useful when piping commands together, since it causes the pipeline to return the exit status of the last command in the pipeline that exited with a non-zero status.
