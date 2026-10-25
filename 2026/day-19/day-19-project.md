# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## Objective

The objective of this project is to apply Bash scripting concepts to real-world system administration tasks, including log rotation, automated backups, server health checks, and scheduled maintenance using cron.

## 1. Log Rotation Script

**File:** `log_rotate.sh`

### Features
- Accepts a log directory as a command-line argument.
- Compresses `.log` files older than seven days using `gzip`.
- Deletes `.gz` files older than 30 days.
- Displays the number of compressed and deleted files.
- Validates the input directory.

### Usage

```bash
./log_rotate.sh /tmp/test-logs
```

### Sample Output

```text
Compressed: /tmp/test-logs/app.log
Deleted: /tmp/test-logs/old.log.gz
Log rotation completed.
Files compressed: 1
Files deleted: 1
```

*Note: Sample output is illustrative. Actual results depend on the files present in the directory.*

## 2. Server Backup Script

**File:** `backup.sh`

### Features
- Accepts a source directory and backup destination.
- Creates a timestamped `.tar.gz` archive.
- Verifies the archive by listing its contents.
- Displays the archive path and size.
- Deletes matching backups older than 14 days.
- Exits with an error if the source directory does not exist.

### Usage

```bash
./backup.sh /tmp/test-source /tmp/test-backups
```

### Sample Output

```text
Backup created successfully.
Archive: /tmp/test-backups/backup-2026-10-25_03-00-00.tar.gz
Size: 12K
```

*Note: The timestamp, archive size, and output depend on the execution environment.*

## 3. Server Health Check

**File:** `health_check.sh`

### Features
- Displays the current date and hostname.
- Shows disk usage.
- Displays memory usage.
- Shows system load information.

### Usage

```bash
./health_check.sh
```

## 4. Crontab Scheduling

Cron allows Linux commands and scripts to execute automatically at scheduled times.

### Cron Syntax

```text
MINUTE HOUR DAY_OF_MONTH MONTH DAY_OF_WEEK COMMAND
```

### Example Cron Entries

```cron
# Log rotation every day at 2:00 AM
0 2 * * * /absolute/path/day-19/log_rotate.sh /var/log/myapp

# Backup every Sunday at 3:00 AM
0 3 * * 0 /absolute/path/day-19/backup.sh /var/www/myapp /var/backups/myapp

# Health check every five minutes
*/5 * * * * /absolute/path/day-19/health_check.sh

# Combined maintenance every day at 1:00 AM
0 1 * * * LOG_DIR=/var/log/myapp SOURCE_DIR=/var/www/myapp BACKUP_DIR=/var/backups/myapp /absolute/path/day-19/maintenance.sh
```

Replace `/absolute/path/day-19/` with the actual absolute path to the scripts.

These entries are examples for documentation and should not be activated until the scripts, permissions, directories, and environment have been checked.

## 5. Scheduled Maintenance

**File:** `maintenance.sh`

The maintenance script runs log rotation and backup operations sequentially. It records output and timestamps in `/var/log/maintenance.log`.

### Usage

```bash
sudo ./maintenance.sh
```

Configure the source, log, and backup directories before running the script. The executing user must have the required file permissions.

## 6. What I Learned

1. **Bash Automation:** How to use command-line arguments, conditions, loops, and error handling to automate system administration tasks.
2. **Backup and Log Management:** How to compress old logs, create timestamped archives, verify backups, and implement retention policies.
3. **Cron Scheduling:** How to schedule recurring tasks and combine multiple scripts into a maintenance workflow.

## Conclusion

This project provided hands-on practice with Linux automation, log management, backup operations, and cron scheduling. These skills are useful for routine system administration and DevOps maintenance tasks.

**Challenge:** 90 Days of DevOps  
**Day:** 19  
**Topics:** Shell Scripting | Log Rotation | Backup Automation | Crontab
