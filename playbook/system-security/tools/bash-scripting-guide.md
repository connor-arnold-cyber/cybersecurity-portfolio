# Bash Scripting Guide

Learn the fundamentals of writing Bash scripts.

## Index

- [What Is a Bash Script?](#what-is-a-bash-script)
- [Creating a Script](#creating-a-script)
- [Running a Script](#running-a-script)
- [Comments](#comments)
- [Variables](#variables)
- [Reading User Input](#reading-user-input)
- [Exit Codes](#exit-codes)
- [Conditionals](#conditionals)
- [Case Statements](#case-statements)
- [Loops](#loops)
- [Functions](#functions)
- [Useful Commands](#useful-commands)

# What Is a Bash Script?

A Bash script is simply a text file containing Bash commands that execute from top to bottom.

Example:

```bash
#!/bin/bash

echo "Hello, world!"
pwd
date
```

## Creating a Script

Create a file:

```bash
nano script.sh
```

Add the shebang at the top:

```bash
#!/bin/bash
```

Make it executable:

```bash
chmod +x script.sh
```

## Running a Script

Run directly:

```bash
./script.sh
```

Or with Bash:

```bash
bash script.sh
```

## Comments

Single-line comments:

```bash
# This is a comment
```

Use comments to explain *why*, not *what*.

## Variables

Create:

```bash
name="Connor"
```

Use:

```bash
echo "$name"
```

Command substitution:

```bash
today=$(date)
```

## Reading User Input

```bash
read -p "Enter your name: " name

echo "Hello, $name!"
```

## Exit Codes

Success:

```bash
exit 0
```

Failure:

```bash
exit 1
```

Check the previous command:

```bash
echo $?
```

## Conditionals

```bash
if [[ -f file.txt ]]; then
    echo "Found"
else
    echo "Missing"
fi
```

## Case Statements

```bash
case "$choice" in
    1) echo "Option 1" ;;
    2) echo "Option 2" ;;
    *) echo "Invalid" ;;
esac
```

## Loops

For loop:

```bash
for file in *.txt
do
    echo "$file"
done
```

While loop:

```bash
while true
do
    echo "Running..."
    break
done
```

## Functions

```bash
greet() {
    echo "Hello!"
}

greet
```

Functions help organize reusable code.

## Useful Commands

| Command | Purpose |
|---------|---------|
| `echo` | Print text |
| `read` | Read user input |
| `test`, `[ ]`, `[[ ]]` | Evaluate conditions |
| `if` | Decision making |
| `case` | Multiple-choice branching |
| `for` | Iterate over items |
| `while` | Repeat while a condition is true |
| `break` | Exit a loop |
| `continue` | Skip to the next iteration |
| `exit` | End the script |
| `chmod +x` | Make a script executable |
| `bash script.sh` | Run a script with Bash |
