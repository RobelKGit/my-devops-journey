# Variables and Parameters

## Key Concepts

- Variables:
  - Variables are essentially component of bash scripting that allows you to store and manipulate data. It makes your script dynamic and flexible.
  - In bash, variables are like containers that hold data such as text strings, numbers and arrays. They provide a way to store value that can be accessed and modified throughout the script.
  - To create a variable in bash script, you assign a value to is using an assignment operator.
  - The variable created is greeting. The string "Hello World!" is attached to the variable.
  - Propending the variable name with a dollar sign to access the value of the variable. The echo command is used to output the value of the variable once the script is being run in the terminal
  - Variables in bash are not consigned to one data type. They can hold different types of data such as strings, numbers and arrays.
  - The fruits variable is assigned to the values (array) apple, banana and orange. This is done using parenthesis ( ).
  - Variables being used within strings to create dynamic output. This is known as variable interpolation. This is shown here (echo "Hello, $name")
- Parameters:
  - Bash scripts can receive input values, known as parameters or arguments from the command line when they're executed.
  - This allows you to customize your scripts and make it more flexible
  - Parameters are all separated by spaces
  - The script script.sh is being run along with the parameters parameter1 parameter2 coming right after
  - Hello is parameter 1 here
  - Hi is parameter 2 here.
  - The echo command is used to display the outputs of the parameters 1,2 and 3.
  - So when executing scripts with parameters, the values passed on the command line will be substituted into the scripts parameter variables $1, $2, $3.
  - echo "All Parameters: $@" this is used to execute the output of all the parameters in one line.
  - $@ is a special variable used to access all the parameters passed through the script.
- Arthimetic Expansion:
  - Bash Scripts allow Mathematical Calculations, which are performed using the dollar symbol and double paranthesis notation. It also evaluates expressions this way.
  - Within the dollar symbol and double paranthesis notation, Arithmetic Expansion (Arithmetic Caculations) is performed.
  - Provides flexibility and makes the script more dynamic.
  - The two variables, num1 and num2 have the respective values 5 and 10.
  - The result variable contains the arithmetic calculation of num1 and num2.
  - Echo "The sum of $num1 and $num2 is: prints the result shown on the right.
  - Arthmetic Expansion allows us to perform calculations using the values of variables and parameters which provides a convenient way to incorporate dynamic calculations into our scripts.
  - Using arithmetic expansions for calculations of a rectangle area and perimeter.
  - Area length times width. The star is used for multiplication.
  - Summary:
    1. Arithmetic Expansion enables mathematical calculation and expression evaluation within bash scripts.
    2. Allows the incorporation of variables and parameters into the calculations which makes the script dynamic and flexible.
    - Provides a concise and readable syntax using the dollar and double parenthesis notation.
- Arthimetic Expansion (with Parameters):
  - Arthimetic Expansions with parameters allow us to make calculations using inputted values from the users from the command line argument (as parameters) to perform calculations based on those values.
  - Allows flexibility and interactivity with the script
  - The positional parameters to assign the values passed as command line arguments to these variables
  - ./arthimetic.sh 8 5 has the parameters 8 and 5
  - The variable length has the value $1 (first positional parameter which is 8) and width (second positional parameter which is).
- Configure VSCode:
  - In VSCode, theres two primary places where settings can be satisfied, user settings and workplace settings.
  - User Settings apply globally to any instance of VSCode you open.
  - WorkPlace settings are specific to a single workspace and only apply when that workspace is open.
  - CodeRunner provides a convenient way to run code snippets or code files in many languages.
  - Top right corner has a play button at the top right corner of the editor. When selected, it will select the whole file or the highlighted text selected. This is important in scripting, as I will use the play button for writing scripts and using the play button to run them.

## Commands

- `greeting="Hello World!"` -- The variable created is greeting. The string "Hello World!" is attached to the variable.
- `echo $greeting` -- Propending the variable name with a dollar sign to access the value of the variable.
- `fruits=("apple", "banana", "orange")` -- The fruits variable is assigned to the values (array) apple, banana and orange. This is done using parenthesis.
- `echo "Parameter 1: $1"` -- values passed on the command line will be substituted into the scripts parameter variables $1, $2, $3
- `echo "All Parameters: $@"` -- this is used to execute the output of all the parameters in one line
- `result=$((num1 + num2))` -- The result variable contains the arithmetic calculation of num1 and num2

## Examples

The variable created is greeting, propending with a dollar sign to access it:
```bash
#!/bin/bash

greeting="Hello World!"

echo $greeting
```

Variables in bash are not consigned to one data type, and variable interpolation shown here (echo "Hello, $name"):
```bash
#!/bin/bash

greeting="Hello World!"
count=42
fruits=("apple", "banana", "orange")

name="Ahmed"
echo "Hello, $name"
```

The script script.sh is being run along with the parameters parameter1 parameter2 coming right after:
```
~$ ./script.sh parameter1 parameter2

~$ vi script.sh
~$ ./script.sh hello hi
Parameter 1: hello
Parameter 2: hi
Parameter 3:
```

The echo command is used to display the outputs of the parameters 1,2 and 3:
```bash
#!/bin/bash

echo "Parameter 1: $1"
echo "Parameter 2: $2"
echo "Parameter 3: $3"
```

The two variables, num1 and num2 have the respective values 5 and 10. The result variable contains the arithmetic calculation:
```bash
#!/bin/bash

num1=5
num2=10

result=$((num1 + num2))

echo "The sum of $num1 and $num2 is: $result"
```
Output: The sum of 5 and 10 is: 15

Using arithmetic expansions for calculations of a rectangle area and perimeter:
```bash
#!/bin/bash

length=5
width=8

area=$((length * width))
perimeter=$((2 * (length + width)))

echo "Rectangle area: $area"
echo "Rectangle permiter: $perimeter"
```
Output:
```
Rectangle area: 40
Rectangle permiter: 26
```

Arthimetic Expansions with parameters, the positional parameters assign the values passed as command line arguments to these variables. ./arthimetic.sh 8 5 has the parameters 8 and 5:
```bash
#!/bin/bash

length="$1"
width="$2"

area=$((length * width))
perimeter=$((2 * (length + width)))

echo "Rectangle area: $area"
echo "Rectangle permiter: $perimeter"
```
```
chmod +x arithmetic.sh
./arithmetic.sh 8 5
Rectangle area: 40
Rectangle permiter: 26
./arithmetic.sh 10 15
Rectangle area: 150
Rectangle permiter: 50
```

## What I Learned

Variables are used when assigning a name to data. This allows you to store and manipulate data. Arthmetic Expansion allows us to perform calculations using the values of variables and parameters which provides a convenient way to incorporate dynamic calculations into our scripts. Arithmetic Expansion enables mathematical calculation and expression evaluation within bash scripts, allows the incorporation of variables and parameters into the calculations which makes the script dynamic and flexible, and provides a concise and readable syntax using the dollar and double parenthesis notation.
