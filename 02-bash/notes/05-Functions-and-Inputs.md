# Functions and Inputs

## Key Concepts

- Basic Functions:
  - Functions allow us to turn our code into modules, improve script, organization and enhance reusability.
  - Functions are like mini programs within our bash scripts. They encapsulate (summarize) a set of instructions that can be called and executed whenever needed.
  - Function also accepts parameters allowing us to pass data to them.
  - This makes them more flexible and re-usable.
  - Local variable name is assigned to the first parameter
- Parameters:
  - Parameters allow us to pass data to functions making them more versatile and adaptable
  - Function parameters allow us to pass data to functions enabling them to perform specific tasks based on provided inputs.
  - Two types of parameters; positional parameter and special parameter.
  - Bash provides a set of special parameters that can be accessed within functions
  - Number of arguments: ($#) - $# holds the count of arguments (the number of arguments)
  - Script name: $0 - $0 is the special variable containing the name of the script.
  - First argument: $1 -- prints the first argument
  - Second argument $2 -- prints the second argument
  - All arguments: $@ - $@ is a special variable that prints all the arguments passed in.
- User Inputs:
  - User input allows interaction between users and our script. Makes the script more dynamic and responsive
  - Accepting user inputs within function creates powerful and interactive scripts.
  - Read command is useful for interactive prompts
  - Allows users to enter information within the script.
  - Command line arguments provide a direct way to pass user input when calling funtions.
  - A combination of both offers flexibility as to how user input is accepted.
- Handling bad data:
  - Bad data refers to invalid or unexpected user inputs that may cause error or undesired behaviours within our scripts.
  - By implementing proper error handling techniques, we ensure our functions gracefully handle bad data and provide informative feedback to the user.
  - Conditional statements are used to validate user input
  - The regular expression ^[0-9]+$] is used to check if the variable age is a numerical value.
  - Another way to handle bad data is via input sanitization. This involves cleaning or transforming user inputs so they meet the required format or constraints.
  - Sanitize string is defined as the function (sanitize_string).
  - This accepts a string input/parameter (input=$1).
  - Summary:
    - In bash, conditional statements can be used to validate user inputs ensuring they meet the desired criteria.
    - Exit codes can be leveraged to determine the success or failure of input validation and provide appropriate feedback to the user.
    - We can use input sanitization such as parameter expansion with patent substitution which can help clean and transform user inputs to meet the required formats or constraints.

## Commands

- `function_name() { }` -- Functions are defined using the function name, followed by parenthesis and then curly braces
- `hello_world` -- Functions can be called using the function name
- `local name="$1"` -- Local variable name is assigned to the first parameter
- `$#` -- holds the count of arguments (the number of arguments)
- `$0` -- special variable containing the name of the script
- `$1` / `$2` -- prints the first / second argument
- `$@` -- special variable that prints all the arguments passed in
- `read name` -- The read command captures the users input and stores it as the variable name
- `return 1` / `return 0` -- Return 1 showcases an error being encountered. Return 0 showcases no errors being encountered
- `${input//[^a-zA-Z0-9]/}` -- parameter expansion along with pattern subsitition to remove any characters that are not alpha numeric

## Examples

The structure of a function in Bash:
```bash
#!/bin/bash

function_name() {
    # code block to be executed
}
```

The function is called hello world (notated by hello_world), simply echoes Hello World!:
```bash
#!/bin/bash

hello_world() {
    echo "Hello World!"
}

hello_world
```
Output: Hello World!

Function also accepts parameters allowing us to pass data to them. Local variable name is assigned to the first parameter:
```bash
#!/bin/bash

hello_world() {
    echo "Hello World!"
}

greet_person() {
    local name="$1"
    echo "Hello, $name!"
}

greet_person "Tom"
greet_person "Sam"
```
Output:
```
Hello, Tom!
Hello, Sam!
```

Number of arguments $#, Script name $0, First argument $1, Second argument $2, All arguments $@:
```bash
#!/bin/bash

print_args() {
    echo "Number of arguments: $#"
    echo "Script name: $0"
    echo "First argument: $1"
    echo "Second argument: $2"
    echo "All arguments: $@"
}

print_args "Alice" "Bob" "Ahmed"
```
Output:
```
Number of arguments: 3
Script name: /path/to/functions.sh
First argument: Alice
Second argument: Bob
All arguments: Alice Bob Ahmed
```

Function is called greet. If statement is used to see if arguments have been passed in. If the number of parameters is 0, then we use echo "What is your name" and read name:
```bash
#!/bin/bash

greet() {
    local name

    if [ $# -eq 0 ]; then
        echo "What is your name?"
        read name
    else
        name="$1"
    fi

    echo "Hello, $name!"
}

greet
```
Terminal:
```
(base) robelkidane@Robels-MacBook-Pro ~ % ./if.sh
What is your name?
Robel
Hello, Robel!
(base) robelkidane@Robels-MacBook-Pro ~ %
```

We use a local variable called age. Conditional statements are used to validate user input. The regular expression ^[0-9]+$] is used to check if the variable age is a numerical value:
```bash
#!/bin/bash

validate_age() {
    local age=$1

    if [[ ! $age =~ ^[0-9]+$ ]]; then
        echo "Invalid age. Please provide a numeric value."
        return 1
    fi

    if (( age < 18 )); then
        echo "Sorry, you must be at least 18 years old."
        return 1
    fi

    echo "Congratulations! You are eligible."
    return 0
}

echo "Please enter your age: "
read user_age

validate_age "$user_age"
exit_code=$?

if (( exit_code != 0 )); then
    echo "Input validation failed."
else
    echo "Validation passed!"
fi
```
Terminal:
```
Please enter your age:
17
Sorry, you must be at least 18 years old.
Input validation failed.

Please enter your age:
19
Congratulations! You are eligible.
Validation passed!
```

Sanitize string is defined as the function (sanitize_string), using parameter expansion with pattern substitution to remove any characters that are not alpha numeric:
```bash
#!/bin/bash

# Function sanitizing user input
sanitize_string() {
    local input=$1
    local sanitized_input=${input//[^a-zA-Z0-9]/}

    echo "$sanitized_input"
}

# Calling the "sanitize_string" function
echo "Please enter a username:"
read input_username

sanitized_username=$(sanitize_string "$input_username")

echo "Sanitized username: $sanitized_username"
```

## What I Learned

- Summary:
    - Functions are defined using the function name, followed by parenthesis and then curly braces. The code is encapsulated within the curly braces.
    - Functions can be called using the function name.
    - Parameters are used to make functions flexibile and reusable.
    - Positional parameters allow us to pass data into functions and access them using numbered variables like $1 and $2.
    - Special parameters provide additional information about the script and arguments passed to it. Examples: $#, $@, $0. (Known as special parameters).
    - In bash, conditional statements can be used to validate user inputs ensuring they meet the desired criteria.
    - Exit codes can be leveraged to determine the success or failure of input validation.
    - Input sanitization such as parameter expansion with pattern substitution can help clean and transform user inputs to meet the required formats or constraints.
