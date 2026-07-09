# Terminal Command Equivalents

A quick-reference guide comparing common tasks across Bash, Windows Command Prompt (CMD), and PowerShell.

> This page focuses on accomplishing the same task in different shells.

# Navigation

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Print current directory | `pwd` | `cd` | `Get-Location` (`pwd`) |
| List files | `ls` | `dir` | `Get-ChildItem` (`ls`) |
| Change directory | `cd folder` | `cd folder` | `Set-Location folder` (`cd`) |
| Home directory | `cd ~` | `cd %USERPROFILE%` | `cd ~` |
| Clear screen | `clear` | `cls` | `Clear-Host` (`cls`) |

# File & Directory Management

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Create directory | `mkdir folder` | `mkdir folder` | `mkdir folder` |
| Remove empty directory | `rmdir folder` | `rmdir folder` | `Remove-Item folder` |
| Remove directory recursively | `rm -r folder` | `rmdir /s folder` | `Remove-Item folder -Recurse` |
| Create file | `touch file.txt` | `type nul > file.txt` | `New-Item file.txt -ItemType File` (`ni`) |
| Copy file | `cp file1 file2` | `copy file1 file2` | `Copy-Item file1 file2` (`cp`) |
| Move file | `mv file1 file2` | `move file1 file2` | `Move-Item file1 file2` (`mv`) |
| Rename file | `mv old new` | `rename old new` | `Rename-Item old new` |
| Delete file | `rm file` | `del file` | `Remove-Item file` (`rm`) |

# Viewing Files

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Display file | `cat file` | `type file` | `Get-Content file` (`cat`) |
| View first lines | `head file` | N/A | `Get-Content file -Head 10` |
| View last lines | `tail file` | N/A | `Get-Content file -Tail 10` |
| Follow file live | `tail -f file` | N/A | `Get-Content file -Wait` |

# Searching

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Search text | `grep "text" file` | `findstr "text" file` | `Select-String "text" file` |
| Find files | `find . -name file` | `dir /s file` | `Get-ChildItem -Recurse` |
| Locate executable | `which program` | `where program` | `Get-Command program` |

# Permissions & Ownership

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Change permissions | `chmod` | `icacls` | `icacls` |
| Change owner | `chown` | `takeown` | `Set-Acl` / `takeown` |
| View permissions | `ls -l` | `icacls file` | `Get-Acl file` |

# Processes

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| List processes | `ps` | `tasklist` | `Get-Process` (`gps`) |
| Kill by PID | `kill PID` | `taskkill /PID PID` | `Stop-Process -Id PID` |
| Kill by name | `pkill process` | `taskkill /IM process.exe` | `Stop-Process -Name process` |
| Start program | `program` | `start program` | `Start-Process program` |

# Services

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| List services | `systemctl list-units --type=service` | `sc query` | `Get-Service` |
| Start service | `systemctl start service` | `sc start service` | `Start-Service service` |
| Stop service | `systemctl stop service` | `sc stop service` | `Stop-Service service` |
| Restart service | `systemctl restart service` | N/A | `Restart-Service service` |

# Networking

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Show IP address | `ip addr` | `ipconfig` | `Get-NetIPAddress` |
| Ping | `ping host` | `ping host` | `Test-Connection host` |
| DNS lookup | `dig` / `nslookup` | `nslookup` | `Resolve-DnsName` |
| View connections | `ss -tuln` | `netstat -ano` | `Get-NetTCPConnection` |
| Trace route | `traceroute` | `tracert` | `Test-NetConnection -TraceRoute` |

# Users

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Current user | `whoami` | `whoami` | `whoami` |
| List users | `cat /etc/passwd` | `net user` | `Get-LocalUser` |
| Create user | `useradd` | `net user /add` | `New-LocalUser` |
| Change password | `passwd` | `net user username *` | `Set-LocalUser` |

# Environment Variables

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Display PATH | `echo $PATH` | `echo %PATH%` | `$env:PATH` |
| Display variable | `echo $VAR` | `echo %VAR%` | `$env:VAR` |
| Create variable | `export VAR=value` | `set VAR=value` | `$env:VAR="value"` |

# Redirection & Pipelines

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| Overwrite output | `>` | `>` | `>` |
| Append output | `>>` | `>>` | `>>` |
| Redirect input | `<` | `<` | `<` |
| Pipe output | `|` | `|` | `|` *(passes objects instead of text)* |

# Help

| Task | Bash | CMD | PowerShell |
|------|------|-----|------------|
| General help | `man command` | `help` | `Get-Help command` |
| Quick help | `command --help` | `command /?` | `Get-Help command -Examples` |
| List commands | `compgen -c` | `help` | `Get-Command` |

# Key Differences

## Bash

- Linux and macOS shell
- Text-based pipeline
- Strong scripting capabilities
- Common in servers and cybersecurity

## Windows Command Prompt (CMD)

- Legacy Windows shell
- Simple command interpreter
- Best for older scripts and compatibility

## PowerShell

- Modern Windows shell
- Object-oriented pipeline
- Built for automation and administration
- Standard for Windows Server and Active Directory

# Shell Selection Guide

| If you're working with... | Use... |
|---------------------------|---------|
| Linux | Bash |
| Kali Linux | Bash |
| Ubuntu | Bash |
| Red Hat / AlmaLinux | Bash |
| Windows 10/11 | PowerShell |
| Windows Server | PowerShell |
| Active Directory | PowerShell |
| Legacy Windows batch scripts | CMD |
| Cross-platform administration | Bash + PowerShell |
