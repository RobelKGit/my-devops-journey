# Lab: OverTheBandit Level 13

## Objective

No password for this level — instead, gain access to Level 14 using a private SSH key (`sshkey.private`) found in the home directory.

## Commands Used

```bash
# On the bandit13 server
mkdir /tmp/rk
cp sshkey.private /tmp/rk
chmod 600 /tmp/rk/sshkey.private

# Exit bandit13, then on local machine:
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .   # download the key
ls -l sshkey.private                                                  # verify permissions
chmod 600 sshkey.private                                              # set correct permissions if needed

# SSH into bandit14 using the private key
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

## Output

Successfully logged into bandit14 using the private key.

## Challenges

- Initially tried `ssh -i sshkey.private bandit14@localhost -p 2220` — this doesn't work because you can't connect to the port via localhost from within the server itself
- Took a while to understand I needed to exit bandit13 first, download the key to my local machine using `scp`, then SSH in from outside
- SSH is strict about key file permissions — the key must be set to `600` or SSH will refuse to use it

## What I Learned

- SSH private keys must have `chmod 600` permissions — too-open permissions are rejected
- `scp -P 2220` copies files securely from a remote server to your local machine
- You authenticate with a private key using `ssh -i keyfile user@host -p port`
- Understanding the difference between connecting from inside vs outside a server is important
