# Conditionals

## Key Concepts

- If Statements:
  - Allows you to introduce decision making logic into your scripts, executing different code blocks based on specific conditions
  - Provide a way to control the flow of your bash scripts.
  - Evaluate conditions and execute different code blocks based on the results.
  - Structure of an if statement
  - If condition (if the condition were evaluating is true)
  - Then a code block is executed between then and fi.
  - Condition in if statements are formed using comparison operators
    - eq= equal
    - ne= not equal to
    - lt= less than
    - gt= greater than
    - le= less than or equal to
    - ge= greater than or equal to
  - These operators allow you to compare values and see if conditions are true or false
  - Variable age has the value 25
  - For the if condition, the example shown [ $age -gt 18 ] showcases if the variable age notated by a dollar symbol is greater than 18 then the output is executed and 'You are an adult!' is printed.
  - Logical Operators -- two examples:
    - && representing AND
    - || representing OR
  - This is used in the If Statement. For example [ $age -gt 18 ] && [ $age -lt 17 ]. This would lead to the code block not being executed and nothing being printed doing to it not meeting the if statement as the age is 25.
  - Can use string comparisons aswell. Examples are:
    - == representing equal to
    - =! Representing not equal to
  - This prints Hello Alice.
  - The name variable Alice is being compared to the string "Alice"
  - To summarize, if statements are used to make decisions and execute code commands based on conditions. Conditions are formed using comparison and logical operators
- Else and Elif:
  - THE else clause provides an alternate code block if the if condition provides to be false.
  - Provides an alternative path to your scripts flow, offering flexibility and versatility.
  - Else Clause gives you an alternate code block to execute when the initial condition is false
  - If age is greater than 18, then You are an adult is the output.
  - In this scenario, age=15, therefore You are not an adult is printed.
  - Else clause is useful when combined with complex conditions and multiple if statements (ELIF clause).
  - Variable is the score which is 85
  - If statement is score is greater than or equal to 90
  - Then return Excellent as the output.
  - Elif Clause here is used to provide an alternate if statement, if the score is greater than or equal to 80, print good.
  - Elif allows us to add another condition if the first condition is not met.
  - Else clause is like a fail safe, it executes a command if the if statements are not met.
  - To summarize, the script evaluates the value of the score variable and provides different messages based on the score range.
  - The else clause is used in conjunction with the if statement and can be combined with the Elif keyword for more complex conditions.
  - This adds more flexibility and versality to Bash scripts
- Nested If Statements:
  - Nested If statements allow us to make more complex decision-making structures by embedding if statements within other if statements.
  - Two variables, age being 18 and grade being 85.
  - The if statement contains the condition that if the variable age is greater than or equal to 18, then return "You are eligible based on age".
  - To evaluate if they're eligible for the scholarship, this is where the nested if statement comes into play
  - If the grade is greater than or equal to 80, then You are eligible based on grade and Congrats you are eligible based on scholarship is returned as the output.
  - If the grade is not met, the else clauses executes the command to show Sorry you're not eligible based on grade
  - If the age is not met, the else clause for the first if statement is executed and returns You are not eligible.
  - Summary of nested if statement benefits:
    1. They allow the evaluation of multiple conditions and execution of code blocks based on the results.
    2. They provide a way to handle complex decision-making scenarios
    3. Enhance the flexibility and versality of bash scripts.
  - Easy to adapt to different situations.

## Commands

- `if [ $age -gt 18 ]` -- showcases if the variable age notated by a dollar symbol is greater than 18
- `[ $age -gt 18 ] && [ $age -lt 17 ]` -- Logical Operators, && representing AND
- `[ "$name" == "Alice" ]` -- string comparisons, == representing equal to
- `if ... then ... else ... fi` -- Else Clause gives you an alternate code block to execute when the initial condition is false
- `if ... then ... elif ... then ... else ... fi` -- Elif allows us to add another condition if the first condition is not met

## Examples

Structure of an if statement:
```bash
#!/bin/bash

if condition
then

fi
```

Variable age has the value 25, the example shown [ $age -gt 18 ]:
```bash
#!/bin/bash

age=25

if [ $age -gt 18 ]
then
    echo "You are an adult!"
fi
```
Output: You are an adult!

This prints Hello Alice, the name variable Alice is being compared to the string "Alice":
```bash
#!/bin/bash

name="Alice"

if [ "$name" == "Alice" ]
then
    echo "Hello, Alice"
fi
```

Else Clause gives you an alternate code block to execute when the initial condition is false:
```bash
#!/bin/bash

if condition
then
    # Code block if condition is true
else
    # Code block if condition is false
fi
```

If age is greater than 18, then You are an adult is the output. In this scenario, age=15, therefore You are not an adult is printed:
```bash
#!/bin/bash

age=15

if [ $age -gt 18 ]
then
    echo "You are an adult!"
else
    echo "You are not an adult!"
fi
```
Output: You are not an adult!

Variable is the score which is 85. If statement is score is greater than or equal to 90, Elif Clause here is used to provide an alternate if statement:
```bash
#!/bin/bash

score=85

if [ $score -ge 90 ]
then
    echo "Excellent!"
elif [ $score -ge 80 ]
then
    echo "Good!"
else
    echo "Better luck next time!"
fi
```
Output: Good!

Two variables, age being 18 and grade being 85 -- nested if statement:
```bash
#!/bin/bash

age=18
grade=85

if [ $age -gt 18 ]; then
    echo "You are eligible based on age"
    if [ $grade -ge 80 ]; then
        echo "You are elgigble based on grade"
        echo "Congrats you are eligible based on scholorship"
    else
        echo "Sorry you're not eligible based on grade"
    fi
else
    echo "You are not eligible"
fi
```

## What I Learned

To summarize, if statements are used to make decisions and execute code commands based on conditions. Conditions are formed using comparison and logical operators. The else clause is used in conjunction with the if statement and can be combined with the Elif keyword for more complex conditions, which adds more flexibility and versality to Bash scripts. Nested if statements allow the evaluation of multiple conditions and execution of code blocks based on the results, provide a way to handle complex decision-making scenarios, and enhance the flexibility and versality of bash scripts -- easy to adapt to different situations.
