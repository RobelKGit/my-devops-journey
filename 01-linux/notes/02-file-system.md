# Linux File System

## Key Concepts

- Organised in a **hierarchical structure** starting from the root directory `/`
- Everything in Linux is treated as a file

- ## Directory Structure

| Directory | Purpose |
|-----------|---------|
| `/` | Root directory — top of the hierarchy |
| `/home` | Home directory — contains personal directories for each user |
| `/bin` | Essential command binaries (ls, cd, pwd live here) |
| `/boot` | Files related to the boot process including the Linux kernel |
| `/dev` | Device files — represents hardware attached to the system such as discs and terminal |
| `/se` | contains system wide configuration and shell scripts used to boot and initialise file systems |

## File Management Commands

### touch
Creates a new file (or updates the timestamp of an existing one).

```bash
touch myfile.txt  creates myfile.txt
ls -l            - shows timestamp of when file was created
```

### echo
Displays text and can write content to files.

```bash
echo "Hello World"                - prints Hello World to terminal
echo "Hello World" > myfile.txt   - writes Hello World to myfile.txt (overwrites)
echo "Hello World" >> myfile.txt  - appends Hello World to myfile.txt
### cat
Reads and displays file contents. Can also combine multiple files.

```bash
cat myfile.txt                      - displays file contents
cat file1.txt file2.txt             - combines and displays both files
```

### head and tail
```bash
head myfile.txt          - shows first 10 lines by default
head -n 5 myfile.txt     - shows first 5 lines
tail myfile.txt          - shows last 10 lines by default
head -n 10 myfile.txt | tail -n 5   - shows lines 6–10
```

### cp, mv, rm
```bash
cp myfile.txt myfile2.txt     - copies a file
cp -r dir1 dir2               - copies a directory recursively
mv myfile.txt newname.txt     - renames or moves a file
rm myfile.txt                 - removes a file
rm -r mydirectory             - removes a directory and its contents
```

### mkdir and rmdir
```bash
mkdir myfolder                - creates a directory
mkdir -p parent/child         - creates directories stored in directories
mkdir "My Project"            - creates directory with spaces in name
ls -R                         - lists all directories recursively
rmdir emptyfolder             - removes an empty directory
rm -r myfolder                - removes directory including contents
```

## What I Learned

Linux file system becomes logical once you understand where everything within it is stored. This is important for troubleshooting. Navigating the filesystem using the above commands is extrememly important.
