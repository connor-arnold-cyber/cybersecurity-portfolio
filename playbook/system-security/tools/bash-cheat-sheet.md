# Bash Cheat Sheet

A quick-reference guide for commonly used Bash commands and syntax.

> This is a reference, not a tutorial.

# Navigation

| Command | Description |
|----------|-------------|
| `pwd` | Print current working directory |
| `ls` | List directory contents |
| `ls -la` | Long listing with hidden files |
| `cd directory` | Change directory |
| `cd ..` | Go up one directory |
| `cd ~` | Go to home directory |
| `clear` | Clear the terminal |

# File & Directory Management

| Command | Description |
|----------|-------------|
| `mkdir directory` | Create directory |
| `rmdir directory` | Remove empty directory |
| `touch file` | Create empty file |
| `cp source destination` | Copy file |
| `mv source destination` | Move or rename file |
| `rm file` | Delete file |
| `rm -r directory` | Delete directory recursively |

# Compression & Archiving

## gzip (Compress Single Files)

| Command | Description |
|----------|-------------|
| `gzip file` | Compress file (removes original) |
| `gzip -k file` | Compress and keep original |
| `gunzip file.gz` | Decompress file |
| `gunzip -k file.gz` | Decompress and keep compressed copy |
| `gzip -d file.gz` | Same as `gunzip` |
| `gzip -l file.gz` | View compression information |

## zip (Archive + Compress)

| Command | Description |
|----------|-------------|
| `zip archive.zip file` | Create ZIP archive |
| `zip archive.zip file1 file2` | Archive multiple files |
| `zip -r archive.zip directory/` | Archive directory recursively |
| `zip -u archive.zip file` | Update archive with newer file |
| `zip -d archive.zip file` | Remove file from archive |
| `unzip archive.zip` | Extract archive |
| `unzip archive.zip -d directory/` | Extract to another directory |
| `unzip -l archive.zip` | List archive contents |
| `unzip -t archive.zip` | Test archive integrity |

## tar (Archive Only)

| Command | Description |
|----------|-------------|
| `tar -cf archive.tar files` | Create archive |
| `tar -xf archive.tar` | Extract archive |
| `tar -tf archive.tar` | List archive contents |
| `tar -cvf archive.tar files` | Create archive (verbose) |
| `tar -xvf archive.tar` | Extract archive (verbose) |
| `tar -xf archive.tar -C directory/` | Extract to another directory |

## tar + gzip (.tar.gz)

| Command | Description |
|----------|-------------|
| `tar -czf archive.tar.gz files` | Create compressed archive |
| `tar -xzf archive.tar.gz` | Extract compressed archive |
| `tar -tzf archive.tar.gz` | List archive contents |

## tar + bzip2 (.tar.bz2)

| Command | Description |
|----------|-------------|
| `tar -cjf archive.tar.bz2 files` | Create compressed archive |
| `tar -xjf archive.tar.bz2` | Extract compressed archive |
| `tar -tjf archive.tar.bz2` | List archive contents |

## tar + xz (.tar.xz)

| Command | Description |
|----------|-------------|
| `tar -cJf archive.tar.xz files` | Create compressed archive |
| `tar -xJf archive.tar.xz` | Extract compressed archive |
| `tar -tJf archive.tar.xz` | List archive contents |

## Common tar Options

| Option | Description |
|---------|-------------|
| `-c` | Create archive |
| `-x` | Extract archive |
| `-t` | List archive contents |
| `-f` | Specify archive filename |
| `-v` | Verbose output |
| `-z` | Use gzip (`.gz`) |
| `-j` | Use bzip2 (`.bz2`) |
| `-J` | Use xz (`.xz`) |
| `-C` | Extract to directory |

## Common Archive Formats

| Extension | Description |
|-----------|-------------|
| `.gz` | Gzip compressed file |
| `.zip` | ZIP archive |
| `.tar` | Archive only (no compression) |
| `.tar.gz` / `.tgz` | Tar archive compressed with gzip |
| `.tar.bz2` | Tar archive compressed with bzip2 |
| `.tar.xz` | Tar archive compressed with xz |

# Viewing Files

| Command | Description |
|----------|-------------|
| `cat file` | Display entire file |
| `less file` | Scroll through file |
| `head file` | First 10 lines |
| `tail file` | Last 10 lines |
| `tail -f file` | Follow file as it grows |

# Searching

| Command | Description |
|----------|-------------|
| `find . -name "file"` | Find file by name |
| `grep "text" file` | Search text in file |
| `grep -r "text" directory` | Search recursively |

# Permissions

| Command | Description |
|----------|-------------|
| `chmod +x file` | Make executable |
| `chmod 755 file` | Set permissions |
| `chown user file` | Change owner |

# Processes

| Command | Description |
|----------|-------------|
| `ps` | Running processes |
| `ps aux` | Detailed process list |
| `kill PID` | Terminate process |
| `kill -9 PID` | Force terminate process |

# Networking

| Command | Description |
|----------|-------------|
| `ping host` | Test connectivity |
| `ip addr` | Show IP addresses |
| `ss -tuln` | Show listening ports |

# Redirection & Pipes

| Operator | Description |
|----------|-------------|
| `>` | Overwrite output |
| `>>` | Append output |
| `<` | Redirect input |
| `|` | Pipe output to another command |

Example:

```bash
cat logfile.txt | grep ERROR
```

# Variables

```bash
name="Connor"

echo $name
```

# Exit Status

```bash
echo $?
```

- `0` = Success
- Non-zero = Failure

# Conditionals

```bash
if [[ condition ]]
then
    command
fi
```

# Test Operators

## String

| Operator | Meaning |
|----------|---------|
| `==` | Equal |
| `!=` | Not equal |
| `-n` | Not empty |
| `-z` | Empty |

### Numeric

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal |
| `-le` | Less than or equal |

### File

| Operator | Meaning |
|----------|---------|
| `-e` | Exists |
| `-f` | Regular file |
| `-d` | Directory |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |

# Logical Operators

| Operator | Meaning |
|----------|---------|
| `&&` | AND |
| `\|\|` | OR |
| `!` | NOT |

# Wildcards

| Wildcard | Meaning |
|----------|---------|
| `*` | Zero or more characters |
| `?` | Exactly one character |
| `[abc]` | One matching character |

# Environment Variables

```bash
echo $PATH

export VARIABLE=value
```

# Help

| Command | Description |
|----------|-------------|
| `man command` | Manual page |
| `command --help` | Built-in help |
| `help builtin` | Help for Bash built-ins |

# Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Tab` | Autocomplete |
| `↑` | Previous command |
| `Ctrl + C` | Stop current command |
| `Ctrl + L` | Clear screen |
| `Ctrl + R` | Search command history |

# Core Commands to Memorize

```
pwd
ls
cd
mkdir
touch
cp
mv
rm
cat
less
grep
find
chmod
chown
ps
kill
ping
ip
echo
man
```
