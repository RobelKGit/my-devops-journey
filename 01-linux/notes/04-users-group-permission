# Users, Groups & Permissions

## Key Concepts

- Linux controls who can access files through **users**, **groups**, and **permissions**
- The **root user** has full system access — use with caution
- `sudo` (super user do) lets permitted users run administrative commands

## Sudo & Root

```bash
sudo <command>        # run a single command as root
sudo su               # switch to root user entirely
whoami                # verify current user
```

> **Dangerous command** — `rm -rf /` deletes everything from the root directory. Never run this.

Sudo commands are logged for security. View logs with:
```bash
sudo tail /var/log/auth.log
```

## Managing Users

```bash
sudo useradd newuser              # create a new user
sudo passwd newuser               # set password for new user
su newuser                        # switch to a different user
sudo usermod -aG sudo newuser     # give newuser sudo privileges
sudo deluser newuser sudo         # remove sudo privileges from newuser
sudo ls /root                     # read root directory contents
```

## Managing Groups

```bash
sudo groupadd devops              # create a group called devops
cat /etc/group                    # view all groups
sudo usermod -aG devops newuser   # add newuser to devops group
groups                            # show groups current user belongs to
sudo gpasswd -d newuser devops    # remove newuser from devops group
sudo groupdel devops              # delete the devops group
```

## File Permissions

Permissions control who can **read (r)**, **write (w)**, and **execute (x)** a file.

Three categories:
- **User (u)** — the owner of the file
- **Group (g)** — users in the file's group
- **Other (o)** — everyone else

### Symbolic Permissions (chmod)

```bash
chmod u+w,g+r,o-w file.txt          # add write for user, read for group, remove write for others
chmod ug=rw,o=r file.txt            # set user+group to rw, others to r only
chmod +x greet.sh                   # add execute permission for everyone
```

### Numeric (Octal) Permissions

| Number | Permission |
|--------|-----------|
| 4 | Read |
| 2 | Write |
| 1 | Execute |

```bash
chmod 750 file.txt    # user=rwx(7), group=r-x(5), other=---(0)
```

### Changing Ownership (chown & chgrp)

```bash
sudo chown newuser file.txt                    # change owner
sudo chown ubuntu:admin2 file.txt             # change owner and group
sudo chown -R newuser:admin2 my_directory     # change recursively
sudo chgrp devops file.txt                    # change group only
```

## What I Learned

Permission are critical for security. As a DevOps engineer, you will be tasked with reading/setting permissions with both symbolic and numerical methods. I now also understand the difference betwween user/group/other
