# Loops and Flow Control

## Key Concepts

- **While loops** repeat a block of code as long as a condition remains true; useful for automating tasks and iterating over data. The condition is evaluated before each iteration.
- While loops can process data from arrays or files, not just simple counters.
- **For loops** iterate over a sequence of values (a range, a list, an array, or command output) and run a block of code for each one.
- `seq 1 5` generates a sequence of numbers from the first argument to the second, useful for looping a set number of times.
- **Break** immediately exits the innermost loop it's placed in, regardless of the loop's condition.
- **Continue** skips the rest of the current iteration and moves on to the next one, without exiting the loop.
- Both `break` and `continue` work inside `for` and `while` loops.

## Commands

- `while [ condition ]; do ... done` - repeats a block of code while a condition is true
- `for var in list; do ... done` - iterates over a list of values
- `for (( i=1; i<=5; i++ )); do ... done` - C-style counting loop
- `for var in $(seq 1 5); do ... done` - iterates over a generated numeric sequence
- `((count++))` - increments a variable by 1 using arithmetic expansion
- `break` - exits the loop immediately
- `continue` - skips to the next loop iteration

## Examples

Basic while loop structure:
```bash
#!/bin/bash

while condition
do
    # Code to be executed
done
```

While loop counting to 5:
```bash
#!/bin/bash

count=1

while [ $count -le 5 ]
do
    echo "Count: $count "
    ((count++))
done
```
Output:

Count: 1
Count: 2
Count: 3
Count: 4
Count: 5


While loop iterating over an array:
```bash
#!/bin/bash

fruits=("apple" "banana" "orange")
index=0

while [ $index -lt ${#fruits[@]} ]
do
    echo "Fruit: ${fruits[$index]}"
    ((index++))
done
```

Basic for loop structure:
```bash
#!/bin/bash

for variable in sequence
do
    # Code block to be executed
done
```

For loop with a C-style counter:
```bash
#!/bin/bash

for (( i=1; i<=5; i++ ))
do
    echo "Number: $i"
done
```
Output: `Number: 1` through `Number: 5`

For loop iterating over an array:
```bash
#!/bin/bash

fruits=("apple" "banana" "orange")

for fruit in "${fruits[@]}"
do
    echo "Fruits: $fruit"
done
```
Output: `Fruits: apple`, `Fruits: banana`, `Fruits: orange`

For loop using the `seq` command:
```bash
#!/bin/bash

for number in $(seq 1 5)
do
    echo "Number: $number"
done
```
Output: `Number: 1` through `Number: 5`

Break statement inside a for loop:
```bash
#!/bin/bash

for (( i=1; i<=5; i++ ))
do
    if [ $i -eq 3 ]
    then
        break
    fi
    echo "Number: $i"
done
```
Output:

Number: 1
Number: 2


Continue statement inside a for loop:
```bash
#!/bin/bash

for (( i=1; i<=5; i++ ))
do
    if [ $i -eq 3 ]
    then
        continue
    fi
    echo "Number: $i"
done
```
Output:

Number: 1
Number: 2
Number: 4
Number: 5


Break statement inside a while loop:
```bash
#!/bin/bash

count=1

while true
do
    echo "Count: $count"
    ((count++))
    if [ $count -eq 4 ]
    then
        break
    fi
done
```
Output:

Count: 1
Count: 2
Count: 3


Continue statement inside a while loop:
```bash
#!/bin/bash

count=1

while [ $count -le 5 ]
do
    if [ $count -eq 3 ]
    then
        ((count++))
        continue
    fi
    echo "Count: $count"
    ((count++))
done
```
Output:

Count: 1
Count: 2
Count: 4
Count: 5


## What I Learned

While loops are best when you don't know in advance how many iterations you'll need (e.g. waiting for a condition to change), while for loops are best when iterating over a known sequence, list, or array. `break` and `continue` allow additional control within both for and while loops. `break` interupts the innermost loop its placed in, regardless of its condition. `continue` skips the rest of the current iteration it is placed in and moves onto the next iteration.
