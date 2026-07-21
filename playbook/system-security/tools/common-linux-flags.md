# Linux Command Flags Reference

## Overview

Linux flags modify how commands behave.

```bash
command -f argument
```

- `command` is the program being executed.
- `-f` is a short option or flag.
- `argument` is the file, directory, value, or target being used.

Flags are not universal. Each command defines its own options, so the same flag can mean different things depending on the command.

Use these when unsure:

```bash
command --help
```

```bash
man command
```

## Common Short Flags

| Flag | Common Meanings | What It Does | Typical Usage |
|---|---|---|---|
| `-a` | All, archive | Includes normally hidden items or preserves file attributes during copying. | `ls -a`, `cp -a source/ backup/` |
| `-A` | Almost all | Includes hidden files but excludes the special `.` and `..` entries. | `ls -A` |
| `-b` | Bytes, batch | Displays values in bytes or enables noninteractive operation. | Meaning depends heavily on the command. |
| `-c` | Command, create, count | Executes supplied command text, creates an archive, or counts matches. | `bash -c "whoami"`, `tar -cf backup.tar files/`, `grep -c error log.txt` |
| `-d` | Directory, data | Tests for a directory or supplies request data. | `[ -d /var/log ]`, `curl -d "user=alex" URL` |
| `-e` | Exists, expression | Tests whether a path exists or supplies an expression. | `[ -e file ]`, `sed -e 's/old/new/' file` |
| `-E` | Extended behavior | Commonly enables extended regular expressions. | `grep -E 'error|failed' log.txt` |
| `-f` | Force, file | Suppresses prompts, tests for a regular file, reads patterns from a file, or specifies an archive filename. | `rm -f file`, `[ -f file ]`, `grep -f patterns.txt data.txt`, `tar -cf backup.tar files/` |
| `-F` | Fixed strings, classify | Treats patterns literally or adds symbols showing file types. | `grep -F '192.168.1.1' log.txt`, `ls -F` |
| `-h` | Human-readable, help | Converts byte counts into readable units or displays help. | `ls -lh`, `du -h` |
| `-H` | Header, follow links | Supplies an HTTP header or changes symbolic-link handling. | `curl -H "Content-Type: application/json" URL` |
| `-i` | Interactive, ignore case, identity | Requests confirmation, ignores capitalization, or selects an SSH key. | `rm -i file`, `grep -i password file`, `ssh -i key.pem user@host` |
| `-I` | Interface, include, ignore | Often selects a network interface or adds an include location. | Check the command documentation. |
| `-j` | Jobs | Controls how many tasks run in parallel. | `make -j4` |
| `-k` | Insecure, keep | With `curl`, disables TLS certificate verification. | `curl -k https://lab-server` |
| `-l` | Long, list, listening | Displays detailed output, lists objects, or shows listening sockets. | `ls -l`, `ss -l` |
| `-L` | Follow links, location | Follows symbolic links or HTTP redirects. | `find -L directory`, `curl -L URL` |
| `-m` | Mode, modification, maximum | Sets a permission mode, filters by modification time, or limits a value. | `mkdir -m 700 private`, `find . -mmin -30` |
| `-n` | Numeric, line numbers, no execution | Shows line numbers, prevents hostname lookups, or disables a default action. | `grep -n error file`, `ss -n` |
| `-N` | No command | With SSH, creates a connection without running a remote command. | `ssh -N -L 8080:localhost:80 user@host` |
| `-o` | Output, option, only matching | Selects an output file, enables an option, or prints only matched text. | `curl -o page.html URL`, `grep -o '[0-9]*' file` |
| `-O` | Original filename | Saves a downloaded file using the remote filename. | `curl -O URL` |
| `-p` | Parents, port, preserve | Creates missing parent directories, selects a port, or preserves file attributes. | `mkdir -p logs/archive`, `ssh -p 2222 host`, `cp -p source dest` |
| `-P` | Port, Perl regex, physical | Selects an SCP port, enables Perl-compatible regex, or resolves a physical path. | `scp -P 2222 file host:/tmp`, `grep -P '\d+' file`, `pwd -P` |
| `-q` | Quiet | Suppresses normal output when only success or failure matters. | `grep -q root /etc/passwd` |
| `-r` | Recursive, reverse | Processes directories recursively or reverses output order. | `grep -r password /etc`, `rm -r directory`, `sort -r file` |
| `-R` | Recursive | Recursively processes directory trees. Behavior may differ slightly from lowercase `-r`. | `chmod -R 750 directory`, `chown -R user:group directory` |
| `-s` | Silent, size | Suppresses output or tests whether a file contains data. | `curl -s URL`, `[ -s logfile ]` |
| `-S` | Size, socket | Sorts by size or identifies a socket. | `ls -lS`, `[ -S socket ]` |
| `-t` | Time, type, TCP | Sorts by time, selects an object type, or enables TCP output. | `ls -lt`, `find . -type f`, `ss -t` |
| `-u` | User, update, UDP | Selects a user, copies only newer files, or enables UDP output. | `ps -u root`, `cp -u source dest`, `ss -u` |
| `-v` | Verbose, invert match | Displays extra details or selects lines that do not match. | `cp -v source dest`, `ssh -v host`, `grep -v success log.txt` |
| `-V` | Version | Commonly displays program version information. | Check whether the command uses `-V` or `--version`. |
| `-w` | Word, writable | Matches complete words or tests write permission. | `grep -w root file`, `[ -w file ]` |
| `-x` | Executable, trace, filesystem boundary | Tests execution permission, traces script commands, or prevents filesystem traversal. | `[ -x script.sh ]`, `bash -x script.sh`, `find / -xdev` |
| `-X` | Request method, exclude | Selects an HTTP method or excludes matching items. | `curl -X POST URL` |
| `-y` | Assume yes | Automatically confirms prompts. | `sudo apt install -y package` |
| `-z` | Empty string, gzip, null delimiter | Tests for an empty string, enables gzip compression, or changes input separation. | `[ -z "$name" ]`, `tar -czf backup.tar.gz files/` |

## Combined Flags

Single-letter flags can often be combined.

```bash
ls -l -a -h
```

Equivalent:

```bash
ls -lah
```

Options that require a value still need that value:

```bash
ssh -p 2222 user@host
```

Here, `2222` belongs to `-p`.

## Bash Test Operators

Test operators are commonly used inside:

```bash
[ condition ]
```

or:

```bash
[[ condition ]]
```

## File and Directory Tests

| Operator | Meaning | Example |
|---|---|---|
| `-e` | Path exists | `[ -e "$path" ]` |
| `-f` | Regular file exists | `[ -f "$file" ]` |
| `-d` | Directory exists | `[ -d "$directory" ]` |
| `-L` | Symbolic link exists | `[ -L "$path" ]` |
| `-b` | Block device exists | `[ -b /dev/sda ]` |
| `-c` | Character device exists | `[ -c /dev/tty ]` |
| `-p` | Named pipe exists | `[ -p "$path" ]` |
| `-S` | Unix socket exists | `[ -S "$path" ]` |
| `-s` | File exists and is not empty | `[ -s "$logfile" ]` |

## Permission Tests

| Operator | Meaning | Example |
|---|---|---|
| `-r` | Current user can read the path | `[ -r "$file" ]` |
| `-w` | Current user can write to the path | `[ -w "$file" ]` |
| `-x` | Current user can execute or traverse the path | `[ -x "$file" ]` |
| `-u` | SUID permission is set | `[ -u "$file" ]` |
| `-g` | SGID permission is set | `[ -g "$file" ]` |
| `-k` | Sticky bit is set | `[ -k "$directory" ]` |

## String Tests

| Operator | Meaning | Example |
|---|---|---|
| `-z` | String is empty | `[ -z "$variable" ]` |
| `-n` | String is not empty | `[ -n "$variable" ]` |
| `=` | Strings are equal | `[ "$answer" = "yes" ]` |
| `!=` | Strings are different | `[ "$user" != "root" ]` |

Quote variables inside single-bracket tests:

```bash
[ -n "$username" ]
```

## Common Command Flag References

## `ls`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-l` | Long listing | Show permissions, owner, group, size, and timestamps. |
| `-a` | All entries | Include hidden files. |
| `-A` | Almost all | Include hidden files but omit `.` and `..`. |
| `-h` | Human-readable | Show sizes such as `4K`, `12M`, and `2G`. |
| `-t` | Sort by modification time | Show recently modified files first. |
| `-S` | Sort by size | Show largest files first. |
| `-R` | Recursive | List subdirectory contents. |

```bash
ls -lah
```

## `grep`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-i` | Ignore case | Match uppercase and lowercase versions. |
| `-n` | Line numbers | Show where each match appears. |
| `-r` | Recursive | Search files throughout a directory tree. |
| `-v` | Invert match | Display lines that do not match. |
| `-E` | Extended regex | Enable operators such as `|`, `+`, `?`, and parentheses. |
| `-F` | Fixed string | Search literally instead of using regex. |
| `-w` | Whole word | Match a complete word. |
| `-c` | Count | Display the number of matching lines. |
| `-q` | Quiet | Produce no output and rely on the exit status. |
| `-o` | Only matching | Display only the matched part of each line. |

```bash
grep -rin "failed password" /var/log
```

## `find`

`find` mainly uses expressions rather than normal short flags.

| Expression | Meaning | Typical Use |
|---|---|---|
| `-name` | Match filename | `find /etc -name "*.conf"` |
| `-iname` | Case-insensitive filename | Match different capitalization. |
| `-type f` | Regular files only | Exclude directories and devices. |
| `-type d` | Directories only | Search only for directories. |
| `-size` | Match by size | Find unusually large files. |
| `-mtime` | Modified a number of days ago | Find old or recently modified files. |
| `-mmin` | Modified a number of minutes ago | Useful during incident investigation. |
| `-user` | Match owner | Locate files owned by a specific account. |
| `-group` | Match group | Locate files assigned to a group. |
| `-perm` | Match permissions | Find writable files or SUID executables. |
| `-exec` | Run a command on results | Process every matching path. |
| `-delete` | Delete results | Dangerous; inspect results first. |
| `-xdev` | Stay on one filesystem | Avoid mounted filesystems. |

```bash
find /var/log -type f -mtime -1
```

## `curl`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-o FILE` | Output filename | Save the response under a chosen filename. |
| `-O` | Remote filename | Save using the remote filename. |
| `-I` | Headers only | Inspect HTTP response headers. |
| `-H` | Request header | Add authorization or content-type headers. |
| `-X` | Request method | Select `GET`, `POST`, `PUT`, or `DELETE`. |
| `-d` | Request data | Send form or API data. |
| `-L` | Follow redirects | Continue after HTTP redirects. |
| `-s` | Silent | Hide progress output. |
| `-S` | Show errors | Show errors while otherwise remaining silent. |
| `-k` | Insecure TLS | Skip certificate verification during controlled testing. |
| `-v` | Verbose | Display detailed connection information. |

```bash
curl -sS -L -o page.html https://example.com
```

## `ssh`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-p PORT` | Remote SSH port | Connect to a port other than 22. |
| `-i FILE` | Identity file | Select a private key. |
| `-v` | Verbose | Troubleshoot connections and authentication. |
| `-N` | No remote command | Create a tunnel without opening a shell. |
| `-L` | Local forwarding | Forward a local port through the SSH server. |
| `-R` | Remote forwarding | Expose a local service through the remote server. |
| `-D` | Dynamic forwarding | Create a SOCKS proxy. |
| `-J` | Jump host | Connect through an intermediate SSH server. |
| `-o` | Configuration option | Supply an SSH setting directly. |

```bash
ssh -i ~/.ssh/id_ed25519 -p 2222 user@server
```

## `scp`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-r` | Recursive | Copy an entire directory. |
| `-i FILE` | Identity file | Authenticate with a private key. |
| `-P PORT` | SSH port | Connect to a nonstandard SSH port. |
| `-p` | Preserve | Retain permissions and timestamps. |
| `-v` | Verbose | Troubleshoot the transfer. |

```bash
scp -P 2222 file.txt user@server:/tmp/
```

SCP uses uppercase `-P` for the port.

## `tar`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-c` | Create | Build a new archive. |
| `-x` | Extract | Extract an archive. |
| `-t` | List | Display archive contents without extracting. |
| `-f FILE` | Archive file | Specify the archive filename. |
| `-v` | Verbose | Display files as they are processed. |
| `-z` | Gzip | Use gzip compression. |
| `-j` | Bzip2 | Use bzip2 compression. |
| `-J` | XZ | Use XZ compression. |
| `-C DIR` | Change directory | Extract or operate from a selected directory. |

Create:

```bash
tar -czf backup.tar.gz directory/
```

Extract:

```bash
tar -xzf backup.tar.gz
```

## `ps`

| Flag or Form | Meaning | Typical Use |
|---|---|---|
| `-e` | Every process | Show processes belonging to all users. |
| `-f` | Full format | Display additional process details. |
| `-u USER` | Select user | Show processes owned by a specific user. |
| `aux` | BSD-style detailed listing | Show nearly every process with resource usage. |

```bash
ps aux
```

```bash
ps -ef
```

## `ss`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-t` | TCP | Show TCP sockets. |
| `-u` | UDP | Show UDP sockets. |
| `-l` | Listening | Show services waiting for connections. |
| `-n` | Numeric | Do not resolve ports or IP addresses into names. |
| `-p` | Processes | Show which process owns each socket. |
| `-a` | All | Show listening and connected sockets. |

```bash
sudo ss -tulpn
```

## `tcpdump`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-i INTERFACE` | Interface | Select the interface to capture from. |
| `-n` | Numeric addresses | Disable hostname resolution. |
| `-nn` | Numeric addresses and ports | Disable hostname and service-name resolution. |
| `-c NUMBER` | Packet count | Stop after capturing a selected number of packets. |
| `-w FILE` | Write capture | Save packets to a PCAP file. |
| `-r FILE` | Read capture | Read packets from a PCAP file. |
| `-v` | Verbose | Display more packet details. |
| `-A` | ASCII payload | Display packet contents as text. |
| `-X` | Hex and ASCII payload | Display packet contents in hex and text. |

```bash
sudo tcpdump -i eth0 -nn -w capture.pcap
```

## `nmap`

| Flag | Meaning | Typical Use |
|---|---|---|
| `-sS` | SYN scan | Perform a TCP SYN scan. |
| `-sT` | TCP connect scan | Complete normal TCP connections. |
| `-sU` | UDP scan | Scan UDP ports. |
| `-sV` | Service versions | Identify software and service versions. |
| `-sC` | Default scripts | Run Nmap's default NSE scripts. |
| `-Pn` | Skip host discovery | Treat the target as online. |
| `-p` | Ports | Select specific ports or port ranges. |
| `-p-` | All ports | Scan all 65,535 TCP ports. |
| `-O` | OS detection | Attempt to identify the operating system. |
| `-A` | Aggressive detection | Enable OS detection, version detection, scripts, and traceroute. |
| `-oN FILE` | Normal output | Save results in normal text format. |
| `-oX FILE` | XML output | Save results as XML. |
| `-oA NAME` | All main formats | Save normal, XML, and grepable output. |
| `-v` | Verbose | Display more progress and scan details. |

```bash
nmap -sV -sC -p 22,80,443 192.168.1.10
```

Only scan systems you own or are authorized to test.

## Important Rules

- Flags belong to the command, not Bash itself.
- Uppercase and lowercase flags are different.
- Never assume a flag has the same meaning across every command.
- Options may require values, such as `ssh -p 2222`.
- Combined flags are shorthand for separate single-letter flags.
- Long options are often easier to understand than short flags.

Examples:

```bash
rm --recursive directory/
```

```bash
ls --human-readable
```

```bash
grep --ignore-case pattern file
```

## Quick Reference

| Need | Common Flag |
|---|---|
| Include hidden items | `-a` |
| Detailed output | `-l` |
| Human-readable sizes | `-h` |
| Recursive operation | `-r` or `-R` |
| Verbose output | `-v` |
| Quiet output | `-q` |
| Force an action | commonly `-f` |
| Select a port | commonly `-p` or `-P` |
| Select an output file | commonly `-o` |
| Test for a file | `[ -f file ]` |
| Test for a directory | `[ -d directory ]` |
| Test for execution permission | `[ -x file ]` |
| Test for an empty string | `[ -z "$variable" ]` |
