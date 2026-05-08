# Lab: OverTheBandit Level 12

## Objective

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands Used

```bash
mkdir /tmp/hardtoguessname                   # create working directory
cp data.txt /tmp/hardtoguessname             # copy file into it
cd /tmp/hardtoguessname

xxd -r data.txt > data                       # reverse the hex dump into binary
file data                                    # check the file type

# Repeated decompression steps (file type determined each step with 'file'):
mv data data.gz && gzip -d data.gz           # decompress gzip
mv data data.bz2 && bzip2 -d data.bz2       # decompress bzip2
tar -xvf data.tar                            # extract tar archive
# ...repeated until plain text file reached

cat finalfile                                # read the password
```

## Output

Password for Level 13: `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

## Challenges

This was the most complex level so far. The file had been compressed multiple times with different tools. Had to:
- Learn `xxd -r` to reverse a hex dump
- Use the `file` command after each step in order to identify the correct compression command to use
- Rename files with the correct extension (e.g. `.gz`) before decompressing
- Learn three different decompression tools: `gzip`, `bzip2`, and `tar`

## What I Learned

- `xxd -r` reverses a hex dump back to binary
- `file` is essential for identifying unknown file types
- `gzip -d file.gz` decompresses gzip files
- `bzip2 -d file.bz2` decompresses bzip2 files
- `tar -xvf file.tar` extracts tar archives
- The correct compression tool must be used to successfully decompress the file.
