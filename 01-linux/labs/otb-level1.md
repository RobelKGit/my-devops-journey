# Lab: OverTheBandit Level 1

## Objective

Read the contents of a file named `-` (a dash), which conflicts with the command syntax

## Commands Used

```bash
cat ./-
```

## Output

Password for Level 2: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

## Challenges

The filename `-` is normally interpreted by commands as a flag/option rather than a filename. Using `cat -` alone doesn't work — by specifying the path with `./` the shell is told too read the contents of the file `-`.

## What I Learned

- `./` before a filename results in the shell looking for a path to the file, rather than an option/flag for a command used. 
- Filenames with special characters at the beginning of a filename require quoting or escaping.
