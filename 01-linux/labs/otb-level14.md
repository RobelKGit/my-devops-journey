# Lab: OverTheBandit Level 14

## Objective

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.


## Commands Used

```bash
cat /etc/bandit_pass/bandit14     # retrieve current level password
nc localhost 30000                 # connect to port 30000
# paste the password when prompted
```

## Output

Password for Level 15: `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

## Challenges

Finding the correct command for connecting to a port to send and recieve data. Having the knowledge that the current levels password is stored in `/etc/bandit_pass/bandit14` from the previous level helped to retrieve the next levels password.

## What I Learned

- `nc` (netcat) reads and writes data across network connections using TCP or UDP
- `nc localhost 30000` a connection is opened to port 30000 on the local hoat.
- TCP (Transmission Control Protocol) — reliable, ordered and connected.
- UDP (User Datagram Protocol) — faster but no guarantee datas delivered.
