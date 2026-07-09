# Windows Command Prompt (CMD) Cheat Sheet

A quick-reference guide for commonly used Windows Command Prompt (CMD) commands.

> This is a reference, not a tutorial.

# Navigation

| Command | Description |
|----------|-------------|
| `cd` | Change directory |
| `cd ..` | Go up one directory |
| `cd \` | Go to the root of the current drive |
| `dir` | List files and folders |
| `cls` | Clear the screen |
| `tree` | Display directory structure |

# File & Directory Management

| Command | Description |
|----------|-------------|
| `mkdir folder` or `md folder` | Create directory |
| `rmdir folder` or `rd folder` | Remove empty directory |
| `rmdir /s folder` | Remove directory and contents |
| `copy source destination` | Copy file(s) |
| `xcopy source destination` | Copy files and directories (legacy) |
| `robocopy source destination` | Advanced file and directory copy |
| `move source destination` | Move or rename file |
| `rename old new` | Rename file or folder |
| `del file` | Delete file |
| `type file` | Display file contents |

# Searching

| Command | Description |
|----------|-------------|
| `find "text" file` | Search for text |
| `findstr "text" file` | Advanced text search |
| `where program` | Locate executable |
| `dir /s filename` | Find file recursively |

# Networking

| Command | Description |
|----------|-------------|
| `ipconfig` | Display IP configuration |
| `ipconfig /all` | Detailed network information |
| `ipconfig /release` | Release DHCP address |
| `ipconfig /renew` | Renew DHCP address |
| `ipconfig /flushdns` | Clear DNS cache |
| `ping host` | Test connectivity |
| `tracert host` | Trace network path |
| `nslookup domain` | Query DNS |
| `netstat -ano` | View network connections and listening ports |

# Processes

| Command | Description |
|----------|-------------|
| `tasklist` | List running processes |
| `taskkill /PID pid` | End process by PID |
| `taskkill /IM process.exe` | End process by name |
| `start program` | Launch program |

# System Information

| Command | Description |
|----------|-------------|
| `hostname` | Show computer name |
| `whoami` | Show current user |
| `systeminfo` | Display system information |
| `ver` | Show Windows version |
| `echo %USERNAME%` | Show current username |
| `echo %COMPUTERNAME%` | Show computer name |

# Users & Permissions

| Command | Description |
|----------|-------------|
| `net user` | List local users |
| `net user username` | View user information |
| `net localgroup` | List local groups |
| `net localgroup Administrators` | View Administrators group |

# Environment Variables

| Command | Description |
|----------|-------------|
| `set` | Display environment variables |
| `set VAR=value` | Create variable (current session) |
| `echo %PATH%` | Display PATH variable |
| `echo %VARIABLE%` | Display variable value |

# Redirection & Pipes

| Operator | Description |
|----------|-------------|
| `>` | Overwrite output |
| `>>` | Append output |
| `<` | Redirect input |
| `|` | Pipe output to another command |

Example:

```cmd
ipconfig | findstr IPv4
```

# Batch Variables

```cmd
set NAME=Connor

echo %NAME%
```

# Conditional Operators

| Operator | Meaning |
|----------|---------|
| `&&` | Run next command if previous succeeds |
| `||` | Run next command if previous fails |
| `&` | Run commands sequentially |

Example:

```cmd
mkdir Logs && cd Logs
```

# Wildcards

| Wildcard | Meaning |
|----------|---------|
| `*` | Zero or more characters |
| `?` | Exactly one character |

Examples:

```cmd
dir *.txt

del file?.txt
```

# Help

| Command | Description |
|----------|-------------|
| `help` | List available commands |
| `command /?` | Show help for a command |

Examples:

```cmd
help

ipconfig /?

tasklist /?
```

# Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `↑` | Previous command |
| `↓` | Next command |
| `Tab` | Autocomplete file/folder names |
| `F7` | Command history |
| `Ctrl + C` | Cancel current command |
| `cls` | Clear screen |

# Core Commands to Memorize

```
cd
dir
cls
tree
mkdir
rmdir
copy
move
rename
del
type
findstr
where
ipconfig
ping
tracert
nslookup
netstat
tasklist
taskkill
hostname
whoami
systeminfo
set
echo
help
```
