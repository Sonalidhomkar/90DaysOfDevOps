# Day 17 – Shell Scripting: Loops, Arguments & Error Handling

## Objective

The objective of this practical is to improve my Bash scripting skills by working with `for` and `while` loops, command-line arguments, package installation, and basic error handling.

## 1. For Loop

### Script 1: `for_loop.sh`

```bash
#!/bin/bash

for fruit in Apple Banana Mango Orange Grapes
do
    echo "$fruit"
done
```

**Output:**

```text
Apple
Banana
Mango
Orange
Grapes
```

### Script 2: `count.sh`

```bash
#!/bin/bash

for i in {1..10}
do
    echo "$i"
done
```

**Output:**

```text
1
2
3
4
5
6
7
8
9
10
```

### Key Learnings

- A `for` loop repeats commands for each item in a list.
- `{1..10}` generates a sequence of numbers from 1 to 10.

## 2. While Loop

### Script: `countdown.sh`

```bash
#!/bin/bash

read -p "Enter a number: " num

while [ "$num" -ge 0 ]
do
    echo "$num"
    num=$((num - 1))
done

echo "Done!"
```

**Example Output:**

```text
Enter a number: 5
5
4
3
2
1
0
Done!
```

### Key Learnings

- A `while` loop executes while its condition is true.
- Arithmetic expansion `$(( ))` performs calculations in Bash.

Note: This example expects a non-negative integer as input.

## 3. Command-Line Arguments

### Script 1: `greet.sh`

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: ./greet.sh <name>"
    exit 1
fi

echo "Hello, $1!"
```

**Run the script:**

```bash
chmod +x greet.sh
./greet.sh Sonali
```

**Output:**

```text
Hello, Sonali!
```

If no argument is provided:

```bash
./greet.sh
```

Output:

```text
Usage: ./greet.sh <name>
```

### Script 2: `args_demo.sh`

```bash
#!/bin/bash

echo "Script name: $0"
echo "Total arguments: $#"
echo "All arguments: $@"
```

**Run the script:**

```bash
chmod +x args_demo.sh
./args_demo.sh Linux Docker AWS
```

**Output:**

```text
Script name: ./args_demo.sh
Total arguments: 3
All arguments: Linux Docker AWS
```

### Key Learnings

- `$1` represents the first argument.
- `$#` represents the total number of arguments.
- `$@` represents all supplied arguments.
- `$0` represents the script name.

## 4. Install Packages Using a Script

### Script: `install_packages.sh`

```bash
#!/bin/bash

if [ "$EUID" -ne 0 ]; then
    echo "Run this script as root using sudo."
    exit 1
fi

if command -v apt-get >/dev/null 2>&1; then
    package_manager="apt"
elif command -v dnf >/dev/null 2>&1; then
    package_manager="dnf"
elif command -v yum >/dev/null 2>&1; then
    package_manager="yum"
else
    echo "Unsupported package manager."
    exit 1
fi

packages=(nginx curl wget)

for package in "${packages[@]}"
do
    if [ "$package_manager" = "apt" ]; then
        if dpkg-query -W -f='${Status}' "$package" 2>/dev/null | grep -q "install ok installed"; then
            echo "$package is already installed. Skipping."
        else
            echo "Installing $package..."
            apt-get install -y "$package" || {
                echo "Failed to install $package."
                exit 1
            }
        fi
    else
        if rpm -q "$package" >/dev/null 2>&1; then
            echo "$package is already installed. Skipping."
        else
            echo "Installing $package..."
            "$package_manager" install -y "$package" || {
                echo "Failed to install $package."
                exit 1
            }
        fi
    fi
done

echo "Package check completed."
```

**Run the script:**

```bash
chmod +x install_packages.sh
sudo ./install_packages.sh
```

**Example Output:**

```text
nginx is already installed. Skipping.
Installing curl...
Installing wget...
Package check completed.
```

*The output above is illustrative. Actual messages depend on which packages are installed and whether installation succeeds.*

### Key Learnings

- The script checks whether it is running with root privileges.
- It detects common Linux package managers.
- It skips installed packages and attempts to install missing ones.
- Package installation requires appropriate privileges and network or repository access.

## 5. Error Handling

### Script: `safe_script.sh`

```bash
#!/bin/bash
set -e

mkdir -p /tmp/devops-test || {
    echo "Failed to create directory."
    exit 1
}

cd /tmp/devops-test || {
    echo "Failed to enter directory."
    exit 1
}

touch test.txt || {
    echo "Failed to create file."
    exit 1
}

echo "Directory and file created successfully."
```

**Run the script:**

```bash
chmod +x safe_script.sh
./safe_script.sh
```

**Output:**

```text
Directory and file created successfully.
```

### Verify the Result

```bash
ls -l /tmp/devops-test
```

Expected file:

```text
test.txt
```

### Key Learnings

- `set -e` makes a script exit when an unhandled command fails in many common situations.
- `||` executes the following command or block when the preceding command fails.
- `mkdir -p` avoids failure when the directory already exists.
- Explicit error handling makes scripts easier to troubleshoot.

## 6. Run All Scripts

Make the scripts executable:

```bash
chmod +x for_loop.sh count.sh countdown.sh greet.sh args_demo.sh install_packages.sh safe_script.sh
```

Run the practice scripts:

```bash
./for_loop.sh
./count.sh
./countdown.sh
./greet.sh Sonali
./args_demo.sh Linux Docker AWS
./safe_script.sh
```

Run the package installation script separately with administrator privileges:

```bash
sudo ./install_packages.sh
```

## 7. What I Learned

1. Learned to automate repetitive tasks using `for` and `while` loops.
2. Practiced command-line arguments and input validation in Bash scripts.
3. Learned basic error handling, root privilege checks, and package installation automation.

## Conclusion

Day 17 helped me strengthen my Bash scripting fundamentals through loops, command-line arguments, package management, and error handling. These skills are useful for automating routine Linux administration tasks and building a foundation for DevOps automation.

**Challenge:** 90 Days of DevOps  
**Day:** 17 – Shell Scripting: Loops, Arguments & Error Handling

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
