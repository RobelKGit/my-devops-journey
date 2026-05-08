# SSH & Systemd

---

## SSH (Secure Shell)

### Key Concepts

- A secure way to access and control another computer's command line over a network
- Everything is **encrypted** — no one can intercept your data
- Most Linux servers use **OpenSSH**, which provides the client (`ssh`) and server daemon (`sshd`)

### Installing OpenSSH (Ubuntu)

```bash
sudo apt update
sudo apt install openssh-client openssh-server
```

### Starting & Enabling the SSH Service

```bash
sudo systemctl start ssh      # start the service
sudo systemctl enable ssh     # enable it to start on boot
sudo systemctl status ssh     # check if it's running
```

### Connecting to a Machine

```bash
ssh username@ip-address       # connect to a remote machine
ssh localhost                 # test SSH is working on your own machine
```

---

## Systemd

### Key Concepts

- When Linux boots up, it needs something to start and manage services (web servers, databases, etc.)
- **Systemd** is the init system on most modern Linux distros — it handles this
- You use the `systemctl` command to interact with systemd

### Units

Systemd manages things called **units**. The most common types:

| Unit type | Purpose |
|-----------|---------|
| `.service` | A program/process to run (e.g. nginx, postgres) |
| `.timer` | A schedule that triggers a service |
| `.socket` | Socket-based activation |
| `.mount` | Filesystem mount points |

### Common systemctl Commands

```bash
sudo systemctl start nginx      # start a service
sudo systemctl stop nginx       # stop a service
sudo systemctl restart nginx    # restart a service
sudo systemctl enable nginx     # start service automatically on boot
sudo systemctl disable nginx    # remove from boot startup
sudo systemctl status nginx     # check service status
```

## What I Learned


SSH is fundamental in DevOps - It is used to connect cloud servers such as AWS, EC2, etc. Systemd is important to understand as you will commonly manage services on remote servers.
