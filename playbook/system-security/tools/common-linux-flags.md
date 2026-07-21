# Common Linux Command Flags

## Overview

Many Linux commands reuse the same short options (flags). While they are **not standardized**, these meanings are common enough that learning them will make reading Bash scripts, Linux documentation, and cybersecurity tools much easier.

Always check `man <command>` because the same flag can have different meanings depending on the command.

## Most Common Flags

| Flag | Common Meaning(s) | Frequently Seen In | Example |
|------|--------------------|--------------------|---------|
| `-a` | All | ls, cp, grep | `ls -a` |
| `-A` | Almost all (omit `.` and `..`) | ls | `ls -A` |
| `-b` | Batch mode / bytes | ssh, du | `ssh -b`, `du -b` |
| `-c` | Command, create, count | bash, tar, wc | `bash -c`, `tar -c` |
| `-d` | Directory | ls, test, find | `test -d dir` |
| `-e` | Exists / extended regex (tool dependent) | test, grep | `[ -e file ]` |
| `-E` | Extended regular expressions | grep | `grep -E` |
| `-f` | Force / file | rm, cp, test, tar | `rm -f`, `[ -f file ]` |
| `-F` | Classify output / fixed strings | ls, grep | `ls -F` |
| `-h` | Human-readable / help | ls, du, df | `du -h` |
| `-H` | HTTP header | curl | `curl -H` |
| `-i` | Ignore case / interactive / identity file | grep, rm, ssh | `grep -i` |
| `-I` | Ignore binary files / interface | grep, tcpdump | varies |
| `-j` | Jobs / parallel | make, xargs | `make -j4` |
| `-k` | Insecure / keep going | curl, make | `curl -k` |
| `-l` | Long listing / list | ls, netstat | `ls -l` |
| `-L` | Follow symlinks | cp, find | `find -L` |
| `-m` | Mode / modification time | chmod, find | varies |
| `-n` | Line numbers / dry run / numeric | grep, chown | `grep -n` |
| `-o` | Output file / only matching | curl, grep | `curl -o file` |
| `-O` | Save with original filename | curl, wget | `curl -O URL` |
| `-p` | Parents / preserve / port | mkdir, ssh, scp | `mkdir -p` |
| `-P` | Physical path / port (capital P) | pwd, scp | `scp -P 2222` |
| `-q` | Quiet | grep, ssh | `grep -q` |
| `-r` | Recursive | grep, rm, cp | `grep -r` |
| `-R` | Recursive (capital) | chmod, chown, cp | `chmod -R` |
| `-s` | Silent / file size > 0 | curl, test | `curl -s` |
| `-S` | Sort by size / show errors | ls | `ls -lS` |
| `-t` | Time / type | ls, find | `find -type f` |
| `-T` | Target directory / no target dir | mv, cp | varies |
| `-u` | User / update | ps, sort, cp | `ps -u root` |
| `-U` | Don't sort | ls | `ls -U` |
| `-v` | Verbose | cp, mv, tar | `cp -v` |
| `-V` | Version | many commands | `bash -V` |
| `-w` | Width / write | fmt, tcpdump | varies |
| `-W` | Word regex / timeout | grep, ping | varies |
| `-x` | Executable / one filesystem | test, find | `[ -x script.sh ]` |
| `-X` | HTTP request method | curl | `curl -X POST` |
| `-y` | Assume yes | apt, yum | `apt -y install` |
| `-z` | Empty string / gzip | test, tar | `[ -z "$var" ]` |

## Common Test Operators

These are used inside `test`, `[ ]`, and `[[ ]]`.

| Flag | Meaning | Example |
|------|---------|---------|
| `-f` | Regular file exists | `[ -f file ]` |
| `-d` | Directory exists | `[ -d dir ]` |
| `-e` | Path exists | `[ -e file ]` |
| `-r` | Readable | `[ -r file ]` |
| `-w` | Writable | `[ -w file ]` |
| `-x` | Executable | `[ -x script.sh ]` |
| `-s` | File exists and is not empty | `[ -s file ]` |
| `-L` | Symbolic link | `[ -L link ]` |
| `-z` | String is empty | `[ -z "$name" ]` |
| `-n` | String is not empty | `[ -n "$name" ]` |

## Cybersecurity Commands You'll See Constantly

| Command | Flags Worth Knowing |
|---------|---------------------|
| `grep` | `-r -i -n -v -E -F -q` |
| `find` | `-type -name -mtime -perm -exec` |
| `curl` | `-O -o -I -H -X -d -k -s` |
| `wget` | `-O -q -r` |
| `ssh` | `-i -p -v -N` |
| `scp` | `-i -P -r` |
| `tar` | `-c -x -v -f -z` |
| `chmod` | `-R` |
| `chown` | `-R` |
| `ps` | `-e -f -u -aux` |
| `tcpdump` | `-i -r -w -nn` |
| `ss` | `-t -u -l -p -n` |
| `netstat` | `-t -u -l -n -p` |
| `nmap` | `-sV -sC -Pn -A -p` |

## Remember

- Flags belong to the **command**, not Bash.
- Lowercase and uppercase flags usually mean different things.
- The same flag may have different meanings in different commands.
- If unsure, use:
  - `man <command>`
  - `<command> --help`
