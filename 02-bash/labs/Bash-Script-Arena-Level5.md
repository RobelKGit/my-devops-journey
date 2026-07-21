# Lab: Bash Battle Arena — Level 5: The Boss Battle — Combining Basics

## Objective
Write a script that:
1. Creates a directory named `Battlefield`.
2. Inside `Battlefield`, creates files `knight.txt`, `sorcerer.txt`, and `rogue.txt`.
3. Checks if `knight.txt` exists; if it does, moves it to a new directory called `Archive`.
4. Lists the contents of both `Battlefield` and `Archive`.

## Commands Used
```bash
#!/bin/bash

mkdir -p ~/Battlefield
touch ~/"Battlefield/knight.txt" ~/"Battlefield/sorcerer.txt" ~/"Battlefield/rogue.txt"

mkdir -p ~/Archive

if [ -f ~/Battlefield/knight.txt ]; then
  mv ~/Battlefield/knight.txt ~/Archive/
else
  echo "knight.txt does not exist"
fi

echo "Contents of Battlefield"
ls ~/Battlefield

echo "Contents of Archive"
ls ~/Archive
```

## Output
`Battlefield` and `Archive` directories are created, three files are created in `Battlefield`, `knight.txt` is moved into `Archive`, and both directories' contents are listed.

## Challenges
Combining directory creation, file creation, conditionals, moving files and listing contents of a file all within one script.

## What I Learned
-Combining multiple bash concepts into one well strcutured script to peform a list of tasks.
