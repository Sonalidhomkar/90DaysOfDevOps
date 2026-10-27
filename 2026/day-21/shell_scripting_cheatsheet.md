# Day 21 – Shell Scripting Cheat Sheet
## 90 Days of DevOps Challenge

### Objective
Create a practical Shell Scripting cheat sheet to revise Bash commands, operators, conditionals, loops, functions, text processing, and error handling.

This reference guide includes commonly used syntax and examples helpful for Linux administration, automation, and DevOps tasks.

## Quick Reference Table

| Topic | Key Syntax | Example |
|---|---|---|
| Shebang | `#!/bin/bash` | Defines the Bash interpreter |
| Variable | `VAR="value"` | `NAME="DevOps"` |
| User Input | `read VAR` | `read -p "Name: " NAME` |
| Argument | `$1`, `$2` | `./script.sh arg1` |
| Exit Status | `$?` | `echo $?` |
| If Condition | `if [ condition ]; then` | `if [ -f file.txt ]; then` |
| For Loop | `for i in list; do` | `for i in 1 2 3; do` |
| While Loop | `while [ condition ]; do` | `while [ "$i" -le 5 ]; do` |
| Function | `name() { ... }` | `greet() { echo "Hi"; }` |
| Grep | `grep pattern file` | `grep -in "error" app.log` |
| Awk | `awk '{print $1}' file` | `awk -F: '{print $1}' /etc/passwd` |
| Sed | `sed 's/old/new/g' file` | `sed 's/foo/bar/g' config.txt` |
| Cut | `cut -d: -f1 file` | `cut -d, -f1 data.csv` |
| Sort | `sort file` | `sort -n numbers.txt` |
| Find Files | `find path -type f` | `find . -name "*.log"` |
| Debugging | `set -x` | Displays executed commands |

---

## 1. Shell Scripting Basics

### 1.1 Shebang
The shebang specifies which interpreter should execute the script.

```bash
#!/bin/bash
echo "Hello, DevOps!"
```

### 1.2 Running a Script

```bash
chmod +x script.sh
./script.sh
```

Alternatively, execute it directly through Bash:

```bash
bash script.sh
```

### 1.3 Comments
Comments explain code and are ignored by the shell.

```bash
# This is a single-line comment
NAME="DevOps"  # This is an inline comment
```

### 1.4 Variables
Variables store values. Use `$VAR` to access a value.

```bash
NAME="Sonali"
echo "$NAME"
```

**Quoting:**

```bash
NAME="DevOps Engineer"
echo $NAME       # Variable expansion; word splitting may occur
echo "$NAME"     # Preserves spaces in the value
echo '$NAME'     # Prints the literal text $NAME
```

### 1.5 Reading User Input

```bash
read -p "Enter your name: " NAME
echo "Hello, $NAME!"
```

### 1.6 Command-Line Arguments

```bash
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Number of arguments: $#"
echo "All arguments: $@"
echo "Previous command status: $?"
```

- `$0` — Script name.
- `$1`, `$2` — First and second arguments.
- `$#` — Number of arguments.
- `"$@"` — All arguments, preserving individual argument boundaries when quoted.
- `$?` — Exit status of the previous command.

Example:

```bash
bash script.sh Linux AWS
```

### 1.7 Arithmetic Operations

```bash
A=10
B=5

echo $((A + B))
echo $((A - B))
echo $((A * B))
echo $((A / B))
```

---

## 2. Operators and Conditionals

### 2.1 String Comparisons

```bash
[ "$A" = "$B" ]     # Strings are equal
[ "$A" != "$B" ]    # Strings are different
[ -z "$A" ]         # String is empty
[ -n "$A" ]         # String is not empty
```

### 2.2 Integer Comparisons

```bash
[ "$A" -eq "$B" ]   # Equal
[ "$A" -ne "$B" ]   # Not equal
[ "$A" -lt "$B" ]   # Less than
[ "$A" -gt "$B" ]   # Greater than
[ "$A" -le "$B" ]   # Less than or equal
[ "$A" -ge "$B" ]   # Greater than or equal
```

### 2.3 File Test Operators

```bash
[ -f file.txt ]     # Regular file exists
[ -d mydir ]        # Directory exists
[ -e file.txt ]     # Path exists
[ -r file.txt ]     # Read permission is available
[ -w file.txt ]     # Write permission is available
[ -x script.sh ]    # Execute permission is available
[ -s file.txt ]     # File exists and is not empty
```

### 2.4 If, Elif, Else

```bash
#!/bin/bash

read -p "Enter a number: " NUM

if [ "$NUM" -gt 0 ]; then
    echo "Positive number"
elif [ "$NUM" -lt 0 ]; then
    echo "Negative number"
else
    echo "Zero"
fi
```

### 2.5 Logical Operators

```bash
[ "$A" -gt 0 ] && [ "$B" -gt 0 ]  # AND
[ "$A" -gt 0 ] || [ "$B" -gt 0 ]  # OR
! [ -f file.txt ]                  # NOT
```

- `&&` executes the next command if the previous command succeeds.
- `||` executes the next command if the previous command fails.
- `!` reverses a command's exit status.

### 2.6 Case Statement

Useful for menus and selecting actions.

```bash
#!/bin/bash

read -p "Enter an option (start/stop/status): " ACTION

case "$ACTION" in
    start)  echo "Starting service" ;;
    stop)   echo "Stopping service" ;;
    status) echo "Checking service status" ;;
    *)      echo "Invalid option" ;;
esac
```

---

## 3. Loops

### 3.1 List-Based For Loop

```bash
for i in Linux AWS Docker Git
do
    echo "$i"
done
```

### 3.2 C-Style For Loop

```bash
for ((i=1; i<=5; i++))
do
    echo "$i"
done
```

### 3.3 While Loop

Executes commands while the condition is true.

```bash
i=1

while [ "$i" -le 5 ]
do
    echo "$i"
    ((i++))
done
```

### 3.4 Until Loop

Executes commands until the condition becomes true.

```bash
i=1

until [ "$i" -gt 5 ]
do
    echo "$i"
    ((i++))
done
```

### 3.5 Break and Continue

```bash
for i in 1 2 3 4 5
do
    [ "$i" -eq 3 ] && continue
    [ "$i" -eq 5 ] && break
    echo "$i"
done
```

- `break` exits the loop.
- `continue` skips the current iteration.

### 3.6 Looping Over Files

```bash
for file in *.log
do
    [ -f "$file" ] || continue
    echo "Processing: $file"
done
```

### 3.7 Reading Command Output

```bash
while IFS= read -r line
do
    echo "$line"
done < input.txt
```

This approach safely reads lines without removing backslashes or trimming leading and trailing whitespace.

---

## 4. Functions

### 4.1 Defining and Calling a Function

```bash
greet() {
    echo "Hello, DevOps!"
}

greet
```

### 4.2 Passing Arguments to Functions

```bash
greet() {
    echo "Hello, $1!"
    echo "Your role is $2"
}

greet "Sonali" "DevOps Engineer"
```

Function arguments use `$1`, `$2`, and so on.

### 4.3 Return Values: Return vs Echo

Use `return` for an exit status (0–255), not for returning arbitrary text.

```bash
check_status() {
    return 0
}

if check_status; then
    echo "Success"
fi
```

Use `echo` to produce text output.

```bash
get_name() {
    echo "DevOps"
}

NAME=$(get_name)
echo "$NAME"
```

### 4.4 Local Variables

Use `local` to limit a variable's scope to its function.

```bash
greet() {
    local NAME="Sonali"
    echo "Hello, $NAME!"
}

greet
```

---

## 5. Text Processing Commands

### 5.1 Grep
Searches files for matching text or patterns.

```bash
grep "error" app.log          # Search for a pattern
grep -i "error" app.log       # Ignore case
grep -r "error" logs/         # Search recursively
grep -c "error" app.log       # Count matching lines
grep -n "error" app.log       # Show line numbers
grep -v "error" app.log       # Show non-matching lines
grep -E "error|failed" app.log # Extended regular expressions
```

### 5.2 Awk
Processes structured text, especially column-based data.

```bash
awk '{print $1}' file.txt          # Print first column
awk '{print $1, $3}' file.txt      # Print first and third columns
awk -F: '{print $1}' /etc/passwd   # Use colon as separator
awk '$3 > 1000 {print $1}' data.txt # Filter by third column
awk 'BEGIN {print "Start"} {print $0} END {print "Done"}' file.txt
```

### 5.3 Sed
Edits or transforms text streams.

```bash
sed 's/old/new/' file.txt       # Replace first match per line
sed 's/old/new/g' file.txt      # Replace all matches per line
sed '/error/d' file.txt         # Delete matching lines
sed -i 's/foo/bar/g' config.txt # Edit file in place
```

**Note:** Make a backup before using `sed -i` on important configuration files.

### 5.4 Cut
Extracts selected fields or character positions.

```bash
cut -d, -f1 data.csv      # First comma-separated field
cut -d: -f1 /etc/passwd   # First colon-separated field
cut -c1-5 file.txt        # Characters 1–5
```

### 5.5 Sort

```bash
sort names.txt       # Alphabetical sorting
sort -n numbers.txt  # Numerical sorting
sort -r names.txt    # Reverse order
sort -u names.txt    # Sort and remove duplicate lines
```

### 5.6 Uniq

`uniq` removes or counts adjacent duplicate lines. Sort first if duplicates may be scattered.

```bash
sort names.txt | uniq       # Remove adjacent duplicates after sorting
sort names.txt | uniq -c    # Count occurrences
sort names.txt | uniq -d    # Show repeated lines
```

### 5.7 Tr
Translates or deletes characters.

```bash
echo "hello" | tr 'a-z' 'A-Z'    # Convert to uppercase
echo "hello" | tr 'a-z' 'A-Z'    # Convert to uppercase
echo "a,b,c" | tr ',' '\n'       # Replace commas with newlines
echo "hello123" | tr -d '0-9'    # Delete digits
```

### 5.8 Wc
Counts lines, words, and bytes or characters.

```bash
wc -l file.txt    # Count lines
wc -w file.txt    # Count words
wc -c file.txt    # Count bytes
wc -m file.txt    # Count characters
```

### 5.9 Head and Tail

```bash
head -n 10 file.txt      # First 10 lines
tail -n 10 file.txt      # Last 10 lines
tail -f app.log          # Follow new log entries
tail -F app.log          # Follow by filename, useful after log rotation
```

---

## 6. Useful Patterns and One-Liners

### 6.1 Find Files Older Than Seven Days

Preview matching files first:

```bash
find /var/log -type f -name "*.log" -mtime +7 -print
```

Delete matching files only after verifying the results:

```bash
find /var/log -type f -name "*.log" -mtime +7 -delete
```

**Warning:** Check the target directory carefully before deleting files.

### 6.2 Count Lines in All Log Files

```bash
wc -l ./*.log
```

### 6.3 Replace Text Across Multiple Files

```bash
sed -i 's/old_text/new_text/g' ./*.conf
```

Back up important configuration files before editing them.

### 6.4 Check Whether a Service Is Running

```bash
systemctl is-active --quiet ssh && echo "SSH is running" || echo "SSH is not running"
```

The service name may differ by Linux distribution. Some distributions use `sshd` instead of `ssh`.

### 6.5 Check Disk Usage

```bash
df -h
```

Show a warning when root filesystem usage reaches 80%:

```bash
USAGE=$(df -P / | awk 'NR==2 {gsub(/%/,"",$5); print $5}')
if [ "$USAGE" -ge 80 ]; then
    echo "WARNING: Root filesystem usage is ${USAGE}%"
fi
```

### 6.6 Extract a CSV Column

For a simple CSV without quoted fields or embedded commas:

```bash
cut -d, -f1 data.csv
```

### 6.7 Parse JSON Using jq

```bash
jq '.name' data.json
jq '.items[] | .name' data.json
```

Install `jq` if it is not already available.

### 6.8 Monitor Logs for Errors

```bash
tail -F app.log | grep --line-buffered -iE 'error|failed|critical'
```

### 6.9 Find Large Files

```bash
find /var/log -type f -size +100M -print
```

### 6.10 Create a Timestamped Backup

```bash
tar -czf "backup_$(date +%Y%m%d_%H%M%S).tar.gz" ./my_project
```

---

## 7. Error Handling and Debugging

### 7.1 Exit Codes

An exit code of `0` indicates success; a non-zero code indicates failure.

```bash
ls /tmp
echo "$?"

exit 0  # Exit successfully
exit 1  # Exit with a general failure status
```

Check `$?` immediately after the command whose status you want to inspect.

### 7.2 Set Options

```bash
set -e           # Exit on many unhandled command failures
set -u           # Treat unset variables as errors
set -o pipefail  # Pipeline fails if a command in it fails
set -x           # Trace executed commands
```

A common starting point for Bash automation scripts is:

```bash
#!/bin/bash
set -euo pipefail
```

**Note:** These options have exceptions and require careful use with conditionals, functions, and pipelines. They do not replace explicit error checking.

### 7.3 Trap for Cleanup

Run cleanup commands when the script exits.

```bash
#!/bin/bash

TEMP_FILE=$(mktemp)

cleanup() {
    rm -f "$TEMP_FILE"
    echo "Cleanup completed"
}

trap cleanup EXIT

echo "Working with temporary file..."
```

### 7.4 Debugging a Script

```bash
bash -x script.sh
```

This runs the script with execution tracing to help identify problems.

---

## 8. Best Practices

- Always quote variables when appropriate: `"$VAR"`.
- Use meaningful variable and function names.
- Validate user input and command-line arguments.
- Check exit codes for critical operations.
- Use `set -euo pipefail` thoughtfully.
- Test scripts in a safe environment before production use.
- Avoid hardcoding passwords, secret keys, or other credentials.
- Use comments to explain complex logic.
- Make scripts executable when needed: `chmod +x script.sh`.
- Use `shellcheck` to identify common shell scripting issues.

## Key Takeaways

Through this revision, I consolidated important Bash concepts, including variables, conditionals, loops, functions, text processing, automation patterns, and error handling.

This cheat sheet will serve as a quick-reference guide for future Linux administration and DevOps automation tasks.

**Challenge:** 90 Days of DevOps  
**Day:** 21  
**Topic:** Shell Scripting Cheat Sheet

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham #Linux #BashScripting #DevOps #Automation
