# Lab: OverTheBandit Level 10

## Objective

Find the password in `data.txt`, which contains base64 encoded data.

## Commands Used

```bash
base64 -d data.txt
```

## Output

Password for Level 11: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

## Challenges

No major challenges — once I identified it was base64 encoded, I identified base64 -d is used to decode base64 encoded data.

## What I Learned

- Base64 is an encoding scheme that converts binary data into text format using 64 printable ASCII characters.
