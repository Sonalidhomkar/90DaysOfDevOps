# Day 06 – Linux Fundamentals: Read and Write Text Files

## About Me

I am a BBA(CA) graduate and a fresher who is building my career in DevOps and Cloud Engineering. I have basic knowledge of AWS, Linux, Git & GitHub, networking, and shell scripting.

## My Understanding of Linux File Operations

Linux file operations help users create, read, write, and manage files using commands in the terminal.

Commands such as `cat`, `head`, and `tail` help read file contents, while output redirection using `>` and `>>` helps write and append data to files.

The `tee` command allows us to display output on the terminal and save it to a file at the same time.

## Commands I Practiced

### 1. Create a File

```bash
touch notes.txt
```

Creates an empty file named `notes.txt`.

### 2. Write Data Using `>`

```bash
echo "Line 1: Learning Linux file operations" > notes.txt
```

The `>` operator writes data to a file and overwrites existing content.

### 3. Append Data Using `>>`

```bash
echo "Line 2: Practicing file redirection" >> notes.txt
echo "Line 3: Reading text files" >> notes.txt
```

The `>>` operator adds new content without removing existing lines.

### 4. Read the File Using `cat`

```bash
cat notes.txt
```

Displays the complete contents of the file.

### 5. Read the First Two Lines Using `head`

```bash
head -n 2 notes.txt
```

Displays the first two lines of the file.

### 6. Read the Last Two Lines Using `tail`

```bash
tail -n 2 notes.txt
```

Displays the last two lines of the file.

### 7. Display and Save Output Using `tee`

```bash
echo "Practicing Linux with DevOps" | tee -a notes.txt
```

Displays the text in the terminal and appends it to `notes.txt`.

## What I Learned Today

- How to create text files in Linux.
- The difference between `>` and `>>`.
- How to read files using `cat`, `head`, and `tail`.
- How to display and save output using `tee`.
- How Linux file operations support everyday system administration tasks.

## Why This Matters for DevOps

File operations are useful for managing configuration files, reading logs, writing scripts, and troubleshooting Linux systems. These fundamentals help build a strong foundation for DevOps and automation.

## My Day 06 Takeaway

Today, I learned how to create, write, append, and read text files using Linux commands. I will continue practicing these commands to strengthen my Linux fundamentals.

**Day 06: Learning Linux one command at a time!**
