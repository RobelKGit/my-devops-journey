# Lab: OverTheBandit Level 8

## Objective

Find the password in `data.txt` — it is the only line of text that appears exactly once.

## Commands Used

```bash
sort data.txt | uniq -u
```

## Output

Password for Level 9: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

## Challenges

The file contained many duplicate lines. `uniq` only works on consecutive duplicate lines, so `sort` had to be run first to group identical lines together before `uniq -u` could filter for the unique one.

## What I Learned

- `sort` arranges lines alphabetically, grouping duplicates together
- `uniq -u` prints only lines that appear exactly once
- Combining `sort` and `uniq` with a pipe is a common and powerful pattern
