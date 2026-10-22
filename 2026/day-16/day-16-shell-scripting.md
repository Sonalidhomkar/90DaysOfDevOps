# Day 16 – Shell Scripting Basics

## Overview

As part of the **#90DaysOfDevOps challenge**, I started learning the fundamentals of Bash shell scripting. I practiced writing scripts to display messages, use variables, accept user input, implement conditional logic, check files, and inspect service status.

## Task 1: My First Shell Script

**File:** `hello.sh`

```bash
#!/bin/bash

echo "Hello, DevOps!"
```

**Execution:**

```bash
chmod +x hello.sh
./hello.sh
```

**Expected output:**

```text
Hello, DevOps!
```

**What I learned:** The shebang `#!/bin/bash` specifies the Bash interpreter for direct script execution. Removing it can cause execution problems or different behavior depending on the environment.

## Task 2: Variables

**File:** `variables.sh`

```bash
#!/bin/bash

NAME="Sonali"
ROLE="Aspiring DevOps Engineer"

echo "Hello, I am $NAME and I am an $ROLE"
```

**Expected output:**

```text
Hello, I am Sonali and I am an Aspiring DevOps Engineer
```

**What I learned:**

- Variables store reusable values.
- Variable assignment does not use spaces around `=`.
- Double quotes allow variable expansion, while single quotes preserve literal text.

## Task 3: User Input with `read`

**File:** `greet.sh`

```bash
#!/bin/bash

read -r -p "Enter your name: " NAME
read -r -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"
```

**Example output:**

```text
Enter your name: Sonali
Enter your favourite tool: Docker
Hello Sonali, your favourite tool is Docker
```

**What I learned:** The `read` command accepts user input and stores it in a variable for later use.

## Task 4: If-Else Conditions

### A. Number Validation

**File:** `check_number.sh`

```bash
#!/bin/bash

read -r -p "Enter a number: " NUM

if [[ ! "$NUM" =~ ^-?[0-9]+$ ]]; then
    echo "Invalid input. Please enter an integer."
elif (( NUM > 0 )); then
    echo "The number is positive."
elif (( NUM < 0 )); then
    echo "The number is negative."
else
    echo "The number is zero."
fi
```

**Example output:**

```text
Enter a number: 10
The number is positive.
```

The script checks whether the input is an integer and classifies it as positive, negative, or zero.

### B. File Existence Check

**File:** `file_check.sh`

```bash
#!/bin/bash

read -r -p "Enter filename: " FILE

if [[ -f "$FILE" ]]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

**Example output:**

```text
Enter filename: hello.sh
File exists.
```

The `-f` test checks whether a path points to an existing regular file.

## Task 5: Service Status Check

**File:** `server_check.sh`

```bash
#!/bin/bash

SERVICE="nginx"

read -r -p "Do you want to check the status of $SERVICE? (y/n): " ANSWER

if [[ "$ANSWER" == "y" || "$ANSWER" == "Y" ]]; then
    if systemctl is-active --quiet "$SERVICE"; then
        echo "$SERVICE is active."
    else
        echo "$SERVICE is not active."
    fi
elif [[ "$ANSWER" == "n" || "$ANSWER" == "N" ]]; then
    echo "Skipped."
else
    echo "Invalid choice. Please enter y or n."
fi
```

**Example output:**

```text
Do you want to check the status of nginx? (y/n): n
Skipped.
```

**What I learned:** Shell scripts can combine variables, user input, conditions, and Linux commands to automate simple administrative checks. The service name must match a service available in the Linux environment.

## Execution Commands

Make each script executable and run it:

```bash
chmod +x hello.sh variables.sh greet.sh check_number.sh file_check.sh server_check.sh

./hello.sh
./variables.sh
./greet.sh
./check_number.sh
./file_check.sh
./server_check.sh
```

## Key Learnings

1. **Shebang and execution:** Learned how Bash scripts specify an interpreter and how executable permissions allow direct execution.
2. **Variables and input:** Practiced storing values, printing messages, and collecting user input using `read`.
3. **Conditional automation:** Used `if`, `elif`, `else`, and file tests to make scripts respond to different conditions.

## Conclusion

Day 16 helped me build a foundation in Bash shell scripting. These basic scripting skills are useful for automating repetitive tasks, validating inputs, checking files, and performing simple Linux service checks in DevOps environments.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
