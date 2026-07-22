# Terminal Command Equivalents

Quick reference for performing common tasks in Bash, Windows Command Prompt (CMD), and PowerShell.

# Index

- [Navigation](#navigation)
- [Files & Directories](#files--directories)
- [Viewing Files](#viewing-files)
- [Searching](#searching)
- [Permissions](#permissions)
- [Processes & Services](#processes--services)
- [Networking](#networking)
- [Environment Variables](#environment-variables)
- [Redirection & Pipes](#redirection--pipes)
- [Command Chaining](#command-chaining)
- [Wildcards](#wildcards)
- [Variables](#variables)
- [Help](#help)
- [When to Use Each Shell](#when-to-use-each-shell)

# Navigation

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Show current directory | `pwd` | `cd` | `Get-Location` |
| List files | `ls` | `dir` | `Get-ChildItem` |
| Detailed listing | `ls -l` | `dir` | `Get-ChildItem` |
| Show hidden files | `ls -la` | `dir /a` | `Get-ChildItem -Force` |
| Change directory | `cd folder` | `cd folder` | `Set-Location folder` |
| Go up one directory | `cd ..` | `cd ..` | `cd ..` |
| Go home | `cd ~` | `cd %USERPROFILE%` | `cd ~` |
| Clear screen | `clear` | `cls` | `Clear-Host` |

# Files & Directories

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Create file | `touch file.txt` | `type nul > file.txt` | `New-Item file.txt` |
| Create folder | `mkdir folder` | `mkdir folder` | `mkdir folder` |
| Copy file | `cp file copy` | `copy file copy` | `Copy-Item file copy` |
| Copy folder | `cp -r src dst` | `xcopy src dst` | `Copy-Item src dst -Recurse` |
| Move / Rename | `mv old new` | `move old new` | `Move-Item old new` |
| Delete file | `rm file` | `del file` | `Remove-Item file` |
| Delete folder | `rm -r folder` | `rmdir /s folder` | `Remove-Item folder -Recurse` |

# Viewing Files

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Display file | `cat file` | `type file` | `Get-Content file` |
| Page through file | `less file` | `more file` | `Get-Content file \| more` |
| First lines | `head file` | — | `Get-Content file -Head 10` |
| Last lines | `tail file` | — | `Get-Content file -Tail 10` |
| Follow live updates | `tail -f file` | — | `Get-Content file -Wait` |

# Searching

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Search text | `grep "text" file` | `findstr "text" file` | `Select-String "text" file` |
| Search recursively | `grep -r "text"` | `findstr /s "text"` | `Select-String -Path * -Pattern "text"` |
| Find file | `find . -name "*.txt"` | `dir /s *.txt` | `Get-ChildItem -Recurse *.txt` |
| Locate executable | `which program` | `where program` | `Get-Command program` |

# Permissions

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Current user | `whoami` | `whoami` | `whoami` |
| User information | `id` | `whoami /all` | `whoami /all` |
| Run as administrator | `sudo command` | `runas` | `Start-Process -Verb RunAs` |
| Make executable | `chmod +x file` | — | — |

# Processes & Services

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| List processes | `ps aux` | `tasklist` | `Get-Process` |
| Live process monitor | `top` | `tasklist` | `Get-Process` |
| Kill process | `kill PID` | `taskkill /PID PID` | `Stop-Process PID` |
| Service status | `systemctl status` | `sc query` | `Get-Service` |
| Start service | `systemctl start` | `net start` | `Start-Service` |
| Stop service | `systemctl stop` | `net stop` | `Stop-Service` |
| Restart service | `systemctl restart` | — | `Restart-Service` |

# Networking

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Show IP addresses | `ip addr` | `ipconfig` | `Get-NetIPAddress` |
| Ping host | `ping host` | `ping host` | `Test-Connection host` |
| Show listening ports | `ss -tuln` | `netstat -ano` | `Get-NetTCPConnection` |
| DNS lookup | `dig domain` | `nslookup domain` | `Resolve-DnsName domain` |
| Download file | `wget URL` | `curl URL` | `Invoke-WebRequest URL` |

# Environment Variables

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Show PATH | `echo $PATH` | `echo %PATH%` | `$env:PATH` |
| Show variable | `echo $VAR` | `echo %VAR%` | `$env:VAR` |
| Create variable | `export VAR=value` | `set VAR=value` | `$env:VAR="value"` |

# Redirection & Pipes

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Overwrite output | `>` | `>` | `>` |
| Append output | `>>` | `>>` | `>>` |
| Redirect input | `<` | `<` | `<` |
| Pipe output | `|` | `|` | `|` *(passes objects instead of text)* |

# Command Chaining

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Always run next command | `;` | `&` | `;` |
| Run if previous succeeds | `&&` | `&&` | `&&` |
| Run if previous fails | `\|\|` | `\|\|` | `\|\|` |

# Wildcards

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Zero or more characters | `*` | `*` | `*` |
| One character | `?` | `?` | `?` |
| Character set | `[abc]` | — | `[abc]` |
| Numeric range | `[0-9]` | — | `[0-9]` |

# Variables

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| Create variable | `name="Connor"` | `set name=Connor` | `$name="Connor"` |
| Read variable | `echo $name` | `echo %name%` | `echo $name` |

# Help

| Task | Bash | CMD | PowerShell |
|------|------|------|------------|
| General help | `man command` | `help` | `Get-Help command` |
| Quick help | `command --help` | `command /?` | `Get-Help command -Examples` |
| List commands | `compgen -c` | `help` | `Get-Command` |

# When to Use Each Shell

| Situation | Best Choice |
|-----------|-------------|
| Linux systems | Bash |
| Kali Linux | Bash |
| Ubuntu | Bash |
| Red Hat / AlmaLinux | Bash |
| Windows desktop | PowerShell |
| Windows Server | PowerShell |
| Active Directory | PowerShell |
| Legacy batch scripts | CMD |
| Cross-platform administration | Bash + PowerShell |
