# Challenge 1: Basic Arithmetic Calculator

## Objective

Create a script that takes two numbers as input and performs basic arithmetic operations (addition, subtraction, multiplication, division).

## Requirements

- Prompt user for two numbers
- Perform all four operations
- Display the results
- Handle division by zero

## Example Output

```
Enter first number: 10
Enter second number: 5

Results:
10 + 5 = 15
10 - 5 = 5
10 × 5 = 50
10 ÷ 5 = 2
```

## Solution

```bash
#!/bin/bash

echo "Enter first number : "
read first_number

echo "Enter second number : "
read second_number

echo "Addition of both numbers: $((first_number + second_number))"
echo "First Number subtracted by Second number: $((first_number - second_number))"
echo "First Number multiplied by the Second Number: $((first_number * second_number))"

if [ $second_number == 0 ]; then
    echo "Choose a different number as any number divided by zero cannot be performed"
    exit 1
fi

echo "First Number divided by the Second Number: $((first_number / second_number))"
