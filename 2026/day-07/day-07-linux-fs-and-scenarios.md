# Day 07 – Linux File System Hierarchy and Scenario-Based Practice

## File System Hierarchy

### 1. Check the Root Directory

```bash
ls -l /
```

The `/` directory is the starting point of the entire Linux file system.

### 2. Check the Home Directory

```bash
ls -la ~
```

The `/home` directory contains the home directories of regular users. The `~` symbol represents the current user's home directory.

### 3. Check the Root User Directory

```bash
ls -la /root
```

The `/root` directory is the home directory of the root user.

### 4. Check Configuration Files

```bash
ls -l /etc
cat /etc/hostname
```

The `/etc` directory contains system configuration files. The `cat` command displays the system hostname.

### 5. Check Log Files

```bash
ls -l /var/log
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```

The `/var/log` directory contains system and application logs. The second command displays the five largest entries by size among the items listed in `/var/log`.

### 6. Check the Temporary Directory

```bash
ls -l /tmp
```

The `/tmp` directory stores temporary files created by applications and users.

### 7. Check Essential Commands

```bash
ls -l /bin
ls -l /usr/bin
```

The `/bin` and `/usr/bin` directories contain executable commands and utilities on many Linux systems. On some distributions, `/bin` is a symbolic link to another directory.

### 8. Check Optional Applications

```bash
ls -l /opt
```

The `/opt` directory is commonly used to store optional or third-party applications.

## Scenario-Based Practice

### 1. Service Not Starting

**Problem:** The `myapp` service fails to start after a server reboot.

```bash
systemctl status myapp
journalctl -u myapp -n 50 --no-pager
systemctl is-enabled myapp
systemctl --failed
```

These commands help check the service status, investigate recent logs, verify whether it is enabled at boot, and identify failed services.

### 2. High CPU Usage

**Problem:** The application server is running slowly.

```bash
top
ps aux --sort=-%cpu | head -10
```

The `top` command monitors CPU usage in real time. The `ps` command lists processes sorted by CPU usage, helping identify resource-intensive processes.

### 3. Find Service Logs

**Problem:** A developer wants to check the Docker service logs.

```bash
systemctl status docker
journalctl -u docker -n 50 --no-pager
journalctl -u docker -f
```

These commands check the Docker service status, display the latest 50 log entries, and follow new logs in real time. Press `Ctrl+C` to stop following logs.

### 4. File Permission Issue

**Problem:** The `backup.sh` script displays a `Permission denied` error.

```bash
ls -l /home/user/backup.sh
chmod +x /home/user/backup.sh
ls -l /home/user/backup.sh
/home/user/backup.sh
```

The `ls -l` command checks file permissions. The `chmod +x` command adds execute permission, and the final command attempts to run the script.

Replace `/home/user/backup.sh` with the actual script path.

## Mini Troubleshooting Flow

When troubleshooting a Linux system:

1. Check the relevant file, process, or service.
2. Inspect the service status using `systemctl`.
3. Analyze logs using `journalctl`.
4. Identify the root cause of the problem.
5. Apply the appropriate fix and verify the result.

## Key Learning

Today I learned about the Linux file system hierarchy and practiced commands to inspect important directories, analyze logs, identify high CPU usage, check service failures, and troubleshoot file permission issues.

Understanding Linux directories and following a systematic troubleshooting process are important skills for DevOps engineers.
