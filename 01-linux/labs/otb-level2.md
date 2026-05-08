# Lab: OverTheBandit Level 2

## Objective

The password for the next level is stored in a file called --spaces in this filename-- located in the home directory 

## Commands Used

```bash
cat -- "--spaces in this filename--"
```

## Output

Password for Level 3: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

## Challenges


Attempted cat "--spaces in this filename--" first. This was incorrect due to the shell trying to treat this as a cat opion. Using -- before "--spaces in this filename--" allows the shell to treat this as a single argument and not an option.
```

## What I Learned

- Filenames with spaces must be quoted: `cat "spaces in this filename"`
- Alternatively you can use backslash `cat spaces\ in\ this\ filename`
- Make sure the correct filename is entered to avoid any errors when seacrhing for the filename.
