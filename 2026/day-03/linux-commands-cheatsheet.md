# Day 03 – Linux Commands Cheat Sheet

Today I practiced useful Linux commands for process management, file system operations, and networking troubleshooting.

## 1. Process Management

| Command | Usage |
|---|---|
| `ps` | Displays currently running processes |
| `ps aux` | Shows detailed information about all running processes |
| `top` | Shows real-time process and resource usage |
| `htop` | Interactive process monitoring tool |
| `pstree` | Shows processes in a parent-child tree |
| `pgrep` | Finds the PID of a process by name |
| `kill` | Terminates a process using its PID |
| `pkill` | Terminates processes by name |
| `jobs` | Shows jobs running in the current shell |
| `free -h` | Shows memory usage in a human-readable format |

## 2. File System Commands

| Command | Usage |
|---|---|
| `pwd` | Shows the current working directory |
| `ls` | Lists files and directories |
| `ls -la` | Lists all files including hidden files |
| `cd` | Changes the current directory |
| `mkdir` | Creates a new directory |
| `touch` | Creates a new empty file |
| `cp` | Copies files or directories |
| `mv` | Moves or renames files and directories |
| `rm` | Removes files or directories |
| `cat` | Displays the contents of a file |
| `less` | Views a file page by page |
| `head` | Displays the beginning of a file |
| `tail` | Displays the end of a file |
| `grep` | Searches for a pattern inside text or files |
| `find` | Searches for files and directories |

## 3. Networking Commands

| Command | Usage |
|---|---|
| `ping` | Checks connectivity to another host |
| `ip addr` | Displays IP addresses and network interfaces |
| `dig` | Performs DNS lookups |
| `curl` | Tests HTTP/HTTPS endpoints and transfers data |
| `ss` | Displays network connections and listening ports |

## 4. Useful Troubleshooting Commands

### Check a running process

```bash
ps aux
```

### Search for a specific process

```bash
ps aux | grep nginx
```

### Check the last lines of a log file

```bash
tail -f /var/log/syslog
```

### Check IP address

```bash
ip addr
```

### Test network connectivity

```bash
ping google.com
```

### Check DNS resolution

```bash
dig google.com
```

### Test a website or API

```bash
curl https://example.com
```

## What I Learned Today

Today I practiced Linux commands that can help me inspect processes, manage files, and troubleshoot basic networking issues.

I learned that these commands are important tools for a DevOps engineer because many server and application problems can be investigated directly from the Linux command line.

## Day 03 Takeaway

The more comfortable I become with Linux commands, the more confidently I can troubleshoot servers and applications.

**Day 03: Building my Linux command-line confidence for my DevOps journey.**
