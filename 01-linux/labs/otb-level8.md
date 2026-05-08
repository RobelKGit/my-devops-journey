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

The file contained many duplicated lines. `uniq` only works when the duplicated lines are aligned consecutively.

## What I Learned

- `sort` arranges lines alphabetically, grouping duplicates together
- `uniq -u` prints only lines that appear exactly once
- `sort` pipe `uniq -u` is a powerful way to sort the text alphabetically and print lines that appear just once 
