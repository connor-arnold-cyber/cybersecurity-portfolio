# Bash Cheat Sheet

A simple reference for common Linux commands and basic Bash scripting.

> This page is for quick reminders, not complete explanations.

# Index

- [Navigation](#navigation)
- [Files and Directories](#files-and-directories)
- [Viewing Files](#viewing-files)
- [Searching](#searching)
- [Users and Permissions](#users-and-permissions)
- [Processes and Services](#processes-and-services)
- [Networking](#networking)
- [Packages](#packages)
- [Compression](#compression)
- [Redirection and Pipes](#redirection-and-pipes)
- [Command Chaining](#command-chaining)
- [Wildcards](#wildcards)
- [Variables](#variables)
- [Environment Variables](#environment-variables)
- [Command Substitution](#command-substitution)
- [Exit Status](#exit-status)
- [Tests](#tests)
- [`[ ]` and `[[ ]]`](#--and-)
- [`if`](#if)
- [`if / else`](#if--else)
- [`if / elif / else`](#if--elif--else)
- [Commands as Conditions](#commands-as-conditions)
- [`case`](#case)
- [`select`](#select)
- [Loops](#loops)
- [Arithmetic](#arithmetic)
- [`exit`](#exit)
- [Script Basics](#script-basics)
- [Comments](#comments)
- [Help](#help)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Core Commands to Remember](#core-commands-to-remember)
- [Core Scripting Syntax to Recognize](#core-scripting-syntax-to-recognize)

# Navigation

| Command | What It Does |
|---|---|
| `pwd` | Show the current directory |
| `ls` | List files and folders |
| `ls -l` | Show a detailed list |
| `ls -la` | Include hidden files |
| `cd folder` | Enter a folder |
| `cd ..` | Go up one folder |
| `cd ~` | Go to your home directory |
| `clear` | Clear the terminal |

# Files and Directories

| Command | What It Does |
|---|---|
| `touch file.txt` | Create an empty file |
| `mkdir folder` | Create a folder |
| `mkdir -p path/to/folder` | Create a folder and any missing parent folders |
| `cp source destination` | Copy a file |
| `cp -r source destination` | Copy a folder and its contents |
| `mv old new` | Move or rename something |
| `rm file.txt` | Delete a file |
| `rm -r folder` | Delete a folder and its contents |
| `rmdir folder` | Delete an empty folder |

> Be careful with `rm`. Deleted files normally do not go to a recycle bin.

# Viewing Files

| Command | What It Does |
|---|---|
| `cat file.txt` | Display the entire file |
| `less file.txt` | View a file one screen at a time |
| `head file.txt` | Show the first 10 lines |
| `tail file.txt` | Show the last 10 lines |
| `tail -f logfile` | Watch new lines as they are added |
| `nano file.txt` | Open or create a file in Nano |

# Searching

| Command | What It Does |
|---|---|
| `grep "text" file.txt` | Search inside a file |
| `grep -i "text" file.txt` | Search without case sensitivity |
| `grep -r "text" folder` | Search recursively through a folder |
| `find . -name "file.txt"` | Find a file by name |
| `find . -name "*.txt"` | Find files matching a pattern |
| `which command` | Show the location of a command |
| `command -v command` | Check whether a command exists |

# Users and Permissions

| Command | What It Does |
|---|---|
| `whoami` | Show the current user |
| `id` | Show user and group information |
| `sudo command` | Run a command with elevated privileges |
| `chmod +x script.sh` | Make a script executable |
| `chmod 755 file` | Set numeric permissions |
| `chown user file` | Change the owner |
| `chown user:group file` | Change the owner and group |

# Processes and Services

| Command | What It Does |
|---|---|
| `ps aux` | List running processes |
| `top` | View live process activity |
| `kill PID` | Ask a process to stop |
| `kill -9 PID` | Force a process to stop |
| `systemctl status service` | Check a service |
| `sudo systemctl start service` | Start a service |
| `sudo systemctl stop service` | Stop a service |
| `sudo systemctl restart service` | Restart a service |
| `sudo systemctl enable service` | Start a service automatically at boot |

# Networking

| Command | What It Does |
|---|---|
| `ip addr` | Show IP addresses and interfaces |
| `ping host` | Test connectivity |
| `ss -tuln` | Show listening TCP and UDP ports |
| `curl URL` | Request or download data from a URL |
| `wget URL` | Download a file |
| `hostname` | Show the computer name |

# Packages

## Debian and Ubuntu

```bash
sudo apt update
sudo apt install package
sudo apt remove package
```

## Red Hat-Based Systems

```bash
sudo dnf install package
sudo dnf remove package
```

# Compression

These are the main commands worth keeping here:

```bash
zip -r archive.zip folder
unzip archive.zip

tar -czf archive.tar.gz folder
tar -xzf archive.tar.gz
```

- `zip -r` creates a ZIP archive from a folder.
- `unzip` extracts a ZIP archive.
- `tar -czf` creates a compressed `.tar.gz` archive.
- `tar -xzf` extracts a `.tar.gz` archive.

# Redirection and Pipes

| Operator | What It Does |
|---|---|
| `>` | Send output to a file and overwrite it |
| `>>` | Append output to a file |
| `2>` | Send error output to a file |
| `2>/dev/null` | Discard error output |
| `|` | Send one command's output into another command |
| `<` | Use a file as input |

Examples:

```bash
echo "Hello" > file.txt
echo "Another line" >> file.txt
grep "ERROR" logfile.txt > errors.txt
cat logfile.txt | grep "ERROR"
```

A cleaner version of the last command is:

```bash
grep "ERROR" logfile.txt
```

# Command Chaining

| Operator | Meaning |
|---|---|
| `;` | Run the next command regardless |
| `&&` | Run the next command only if the first succeeds |
| `||` | Run the next command only if the first fails |

Examples:

```bash
mkdir Logs && cd Logs
```

```bash
cp file backup/ || echo "Copy failed"
```

# Wildcards

| Pattern | Meaning |
|---|---|
| `*` | Zero or more characters |
| `?` | Exactly one character |
| `[abc]` | One character from the list |
| `[0-9]` | One number in the range |

Examples:

```bash
ls *.txt
rm file?.log
ls report[0-9].txt
```

# Variables

Create a variable:

```bash
name="Connor"
```

Use the variable:

```bash
echo "$name"
```

Do not place spaces around `=`:

```bash
name="Connor"       # Correct
name = "Connor"     # Incorrect
```

Use braces when the variable touches other text:

```bash
echo "${name}_backup"
```

# Environment Variables

```bash
echo "$HOME"
echo "$PATH"
echo "$USER"
```

Create an environment variable for the current shell:

```bash
export VARIABLE="value"
```

# Command Substitution

Store the output of a command:

```bash
current_date=$(date)
```

Use it:

```bash
echo "$current_date"
```

# Exit Status

Every command returns a number after it finishes.

```bash
echo $?
```

- `0` means success.
- Any non-zero number means failure or another condition.

Example:

```bash
mkdir Logs
echo $?
```

`$?` only contains the exit status of the most recently completed command.

# Tests

Tests return success or failure and are commonly used with `if`.

## String Tests

| Test | Meaning |
|---|---|
| `"$a" = "$b"` | Strings are equal |
| `"$a" != "$b"` | Strings are different |
| `-z "$a"` | String is empty |
| `-n "$a"` | String is not empty |

## Number Tests

| Test | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal |
| `-le` | Less than or equal |

## File Tests

| Test | Meaning |
|---|---|
| `-e path` | Path exists |
| `-f path` | Regular file exists |
| `-d path` | Directory exists |
| `-r path` | Readable |
| `-w path` | Writable |
| `-x path` | Executable |

Examples:

```bash
[ -f report.txt ]
```

```bash
[ -d Logs ]
```

```bash
[ "$age" -ge 18 ]
```

# `[ ]` and `[[ ]]`

Both can evaluate conditions.

Traditional test syntax:

```bash
[ -f file.txt ]
```

Bash extended test syntax:

```bash
[[ -f file.txt ]]
```

Important spacing:

```bash
[ -f file.txt ]     # Correct
[-f file.txt]       # Incorrect
```

`[` and `]` must be separated from the condition by spaces.

For Bash scripts, `[[ ]]` is usually safer and easier for string comparisons and patterns.

# `if`

Run commands only when a condition succeeds:

```bash
if [[ -f report.txt ]]
then
    echo "File exists."
fi
```

# `if / else`

Handle both possible outcomes:

```bash
if [[ -d Logs ]]
then
    echo "Directory exists."
else
    mkdir Logs
fi
```

Only one branch runs.

# `if / elif / else`

Check several conditions in order:

```bash
if [[ "$score" -ge 90 ]]
then
    echo "A"
elif [[ "$score" -ge 80 ]]
then
    echo "B"
else
    echo "Below B"
fi
```

Bash stops after the first matching condition.

# Commands as Conditions

An `if` statement can test a command directly:

```bash
if cp report.txt backup/
then
    echo "Copy succeeded."
else
    echo "Copy failed."
fi
```

The `then` block runs when `cp` returns exit status `0`.

# `case`

Use `case` when one value may match several choices:

```bash
case "$choice" in
    start)
        echo "Starting..."
        ;;
    stop)
        echo "Stopping..."
        ;;
    restart)
        echo "Restarting..."
        ;;
    *)
        echo "Invalid option."
        ;;
esac
```

- Each pattern ends with `)`.
- Each section normally ends with `;;`.
- `*` catches anything that did not match.
- `esac` ends the statement.

# `select`

Create a numbered menu:

```bash
select choice in Backup Restore Quit
do
    case "$choice" in
        Backup)
            echo "Creating backup..."
            ;;
        Restore)
            echo "Restoring backup..."
            ;;
        Quit)
            break
            ;;
        *)
            echo "Invalid choice."
            ;;
    esac
done
```

Bash displays:

```text
1) Backup
2) Restore
3) Quit
#?
```

The selected word is stored in `$choice`.

# Loops

## `for`

Repeat once for each item:

```bash
for file in *.txt
do
    echo "$file"
done
```

## `while`

Repeat while a condition succeeds:

```bash
count=1

while [[ "$count" -le 5 ]]
do
    echo "$count"
    ((count++))
done
```

## Loop Control

```bash
break
```

Immediately leave the current loop.

```bash
continue
```

Skip the rest of the current repetition and begin the next one.

# Arithmetic

```bash
count=$((count + 1))
```

```bash
((count++))
```

Arithmetic conditions:

```bash
if (( count > 10 ))
then
    echo "Greater than 10"
fi
```

Inside `(( ))`, variables do not require `$`.

# `exit`

End the script immediately:

```bash
exit 0
```

- `exit 0` means the script succeeded.
- A non-zero value normally means an error.

Example:

```bash
if [[ ! -f config.txt ]]
then
    echo "Error: config.txt is missing."
    exit 1
fi

echo "Continuing..."
```

If the file is missing, the script ends before reaching `echo "Continuing..."`.

Custom codes can be documented inside the script:

```bash
# Exit codes:
# 0 = Success
# 1 = Missing configuration
# 2 = Backup failure
```

The numbers communicate why the script ended. They do not perform different actions by themselves.

# Script Basics

Start a Bash script with:

```bash
#!/usr/bin/env bash
```

Make it executable:

```bash
chmod +x script.sh
```

Run it:

```bash
./script.sh
```

You can also run it without changing permissions:

```bash
bash script.sh
```

# Comments

```bash
# This is a comment
```

Comments explain the script and are ignored by Bash.

# Help

| Command | What It Does |
|---|---|
| `man command` | Open the manual page |
| `command --help` | Show command help |
| `help builtin` | Show help for a Bash built-in |
| `type command` | Show what kind of command it is |

Examples:

```bash
man grep
grep --help
help cd
type echo
```

# Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Tab` | Autocomplete |
| `Up Arrow` | Previous command |
| `Ctrl + C` | Stop the current command |
| `Ctrl + L` | Clear the terminal |
| `Ctrl + R` | Search command history |
| `Ctrl + A` | Move to the beginning of the line |
| `Ctrl + E` | Move to the end of the line |

# Core Commands to Remember

```text
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
systemctl
ping
ip
ss
curl
echo
man
```

# Core Scripting Syntax to Recognize

```text
$?
$variable
$(command)
[ condition ]
[[ condition ]]
(( arithmetic ))
if / then / elif / else / fi
case / esac
for / while / do / done
select
break
continue
exit
```
