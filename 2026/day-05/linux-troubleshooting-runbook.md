
## Target Service / Process

**Target:** SSH (`sshd`)

Today I practiced a basic Linux troubleshooting drill by checking system health, resources, network connectivity, and service logs.

## Environment Basics

### `uname -a`

**Purpose:**  
To check Linux kernel, hostname, architecture, and system information.

**Observation:**  
The command displayed the current Linux system and kernel details.

### `cat /etc/os-release`

**Purpose:**  
To identify the Linux distribution and version.

**Observation:**  
The output confirmed the Linux distribution and version running on the system.

## Filesystem Sanity

### `mkdir /tmp/runbook-demo`

**Purpose:**  
To create a temporary directory for testing.

**Observation:**  
The directory was created successfully.

### `cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo`

**Purpose:**  
To test file copying and verify the copied file.

**Observation:**  
The file was copied successfully and its permissions were verified.

## CPU & Memory

### `top`

**Purpose:**  
To monitor running processes, CPU usage, and memory usage.

**Observation:**  
I reviewed CPU and memory usage and checked for processes consuming unusually high resources.

### `free -h`

**Purpose:**  
To check available and used memory.

**Observation:**  
The system memory usage was reviewed and no immediate memory pressure was observed.

## Disk & I/O

### `df -h`

**Purpose:**  
To check filesystem disk usage.

**Observation:**  
I checked the available disk space and reviewed filesystem usage.

### `du -sh /var/log`

**Purpose:**  
To check the size of the system log directory.

**Observation:**  
The log directory size was checked for excessive log growth.

## Network

### `ss -tulpn`

**Purpose:**  
To check listening TCP/UDP ports and associated processes.

**Observation:**  
I reviewed the active listening ports and verified the services running on the system.

### `curl -I http://localhost`

**Purpose:**  
To check whether a local HTTP service is responding.

**Observation:**  
I used the command to verify local HTTP connectivity and response status.

## Logs Reviewed

### `journalctl -u ssh -n 50`

**Purpose:**  
To review the latest SSH service logs.

**Observation:**  
I checked recent SSH logs for errors, warnings, and authentication-related events.

## Quick Findings

- Checked Linux system and environment information.
- Reviewed CPU and memory utilization.
- Verified filesystem and log directory usage.
- Checked active network listening ports.
- Reviewed recent SSH service logs.
- Practiced collecting evidence before taking corrective action.

## If This Worsens

If the service or system starts showing problems, I would:

1. Check the service status and recent logs.
2. Investigate CPU, memory, disk, and network usage.
3. Collect deeper troubleshooting information using tools such as `strace` when required.
4. Restart the service only after collecting sufficient evidence.
5. Verify the service after taking corrective action.

## Key Learning

Today I learned that troubleshooting should be **evidence-based rather than guess-based**.

A simple troubleshooting flow I practiced:

**Check → Collect Evidence → Analyze → Act → Verify**

This drill helped me build a repeatable Linux troubleshooting routine that can be useful in real DevOps environments.

**Day 05: Practicing Linux troubleshooting by checking system resources, network status, and service logs.**
