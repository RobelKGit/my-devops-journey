# Lab: OverTheBandit Level 11

## Objective

Find the password in `data.txt` where all letters (a-z and A-Z) have been rotated by 13 positions (ROT13).

## Commands Used

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

## Output

Password for Level 12: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

## Challenges

This was tricky — I hadn't come across ROT13 before. Had to research how to reverse it and learned about the `tr` (translate) command which substitutes characters.

## What I Learned

- ROT13 is a simple cipher that shifts each letter 13 places in the alphabet to form the cipher
- `tr` translates/substitutes characters from standard output, writing to standard input
- `tr 'A-Za-z' 'N-ZA-Mn-za-m'` A becomes N, Z becomes M, n becomes a and z becomes m. The rest of the alphabet follows this squeence of shifts.
