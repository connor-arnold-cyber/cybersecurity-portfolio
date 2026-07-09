# PowerShell Cheat Sheet

A quick-reference guide for commonly used PowerShell commands.

> This is a reference, not a tutorial.

# Navigation

| Command | Description |
|----------|-------------|
| `Get-Location` | Show current directory |
| `pwd` | Alias for Get-Location |
| `Get-ChildItem` | List files and folders |
| `ls` | Alias for Get-ChildItem |
| `Set-Location folder` | Change directory |
| `cd folder` | Alias for Set-Location |
| `Clear-Host` | Clear the console |
| `cls` | Alias for Clear-Host |

# File & Directory Management

| Command | Description |
|----------|-------------|
| `New-Item -ItemType Directory -Name Folder` | Create directory |
| `mkdir Folder` | Alias for New-Item |
| `New-Item file.txt -ItemType File` | Create file |
| `ni file.txt` | Alias for New-Item |
| `Copy-Item source destination` | Copy file or folder |
| `cp source destination` | Alias for Copy-Item |
| `Move-Item source destination` | Move or rename |
| `mv source destination` | Alias for Move-Item |
| `Rename-Item old new` | Rename |
| `Remove-Item file` | Delete file or folder |
| `rm file` | Alias for Remove-Item |

# Viewing Files

| Command | Description |
|----------|-------------|
| `Get-Content file.txt` | Display file contents |
| `cat file.txt` | Alias for Get-Content |
| `gc file.txt` | Alias for Get-Content |

# Searching

| Command | Description |
|----------|-------------|
| `Select-String "text" file.txt` | Search file contents |
| `Get-ChildItem -Recurse` | Find files recursively |
| `Get-Command name` | Find available commands |
| `Get-Help command` | View help |

# Networking

| Command | Description |
|----------|-------------|
| `Get-NetIPAddress` | Show IP addresses |
| `Test-Connection host` | Ping a host |
| `Resolve-DnsName domain` | DNS lookup |
| `Get-NetTCPConnection` | View TCP connections |
| `Get-NetAdapter` | View network adapters |

# Processes & Services

| Command | Description |
|----------|-------------|
| `Get-Process` | List processes |
| `gps` | Alias for Get-Process |
| `Stop-Process -Id PID` | End process |
| `Start-Process program.exe` | Launch program |
| `Get-Service` | List services |
| `Start-Service ServiceName` | Start service |
| `Stop-Service ServiceName` | Stop service |
| `Restart-Service ServiceName` | Restart service |

# System Information

| Command | Description |
|----------|-------------|
| `hostname` | Computer name |
| `whoami` | Current user |
| `Get-ComputerInfo` | System information |
| `Get-Date` | Current date and time |
| `$env:COMPUTERNAME` | Computer name variable |
| `$env:USERNAME` | Current username |

# Users

| Command | Description |
|----------|-------------|
| `Get-LocalUser` | List local users |
| `New-LocalUser` | Create local user |
| `Set-LocalUser` | Modify local user |
| `Remove-LocalUser` | Delete local user |

# Active Directory (Windows Server)

| Command | Description |
|----------|-------------|
| `Get-ADUser` | View AD users |
| `New-ADUser` | Create AD user |
| `Set-ADUser` | Modify AD user |
| `Remove-ADUser` | Delete AD user |
| `Get-ADGroup` | View AD groups |

# Environment Variables

| Command | Description |
|----------|-------------|
| `Get-ChildItem Env:` | View environment variables |
| `$env:PATH` | Display PATH |
| `$env:VARIABLE` | Display variable |
| `$env:VARIABLE="Value"` | Set variable (current session) |

# Pipeline

PowerShell pipelines pass **objects**, not plain text.

```powershell
Get-Process | Sort-Object CPU
```

```powershell
Get-Service | Where-Object Status -eq "Running"
```

# Variables

```powershell
$name = "Connor"

$name
```

# Conditionals

```powershell
if ($condition) {

}
elseif ($condition) {

}
else {

}
```

# Comparison Operators

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal |
| `-le` | Less than or equal |

# Logical Operators

| Operator | Meaning |
|----------|---------|
| `-and` | AND |
| `-or` | OR |
| `-not` | NOT |

# Help

| Command | Description |
|----------|-------------|
| `Get-Help command` | View help |
| `Get-Command` | List available commands |
| `Get-Member` | Inspect object properties |
| `Get-Alias` | View aliases |

Examples:

```powershell
Get-Help Get-Process

Get-Help Get-Process -Examples

Get-Command *service*
```

# Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Tab` | Autocomplete |
| `↑` | Previous command |
| `Ctrl + C` | Cancel command |
| `Ctrl + L` | Clear console |
| `Ctrl + R` | Search history |

# Core Commands to Memorize

```
Get-Location
Get-ChildItem
Set-Location
New-Item
Copy-Item
Move-Item
Rename-Item
Remove-Item
Get-Content
Select-String
Get-Command
Get-Help
Get-Process
Stop-Process
Get-Service
Restart-Service
Get-NetIPAddress
Test-Connection
Resolve-DnsName
Get-ComputerInfo
Get-Date
Get-LocalUser
Get-ADUser
```
