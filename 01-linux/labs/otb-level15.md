# Lab: OverTheBandit Level 15

## Objective

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

## Commands Used

```bash
ncat --ssl localhost 30001    # connect to port 30001 with SSL encryption
# paste the current password when prompted
```

## Output

Password for Level 16: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

## Challenges

Tried several commands (`nc`, `telnet`, `ssh`, `socat`) before finding the right one. Identifying the correct command which had the SSL/TLS encryption feature.

## What I Learned

- `ncat` is an enhanced version of netcat with SSL/TLS support built in
- `--ssl` uses SSL encryption
- SSL/TLS encrypts data in transit 
