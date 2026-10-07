# Day 04 – Linux Practice: Processes and Services

## Process Checks

### 1. Check running processes

```bash
ps
```

The `ps` command shows the processes running in the current session.

### 2. Check detailed running processes

```bash
ps aux
```

The `ps aux` command shows detailed information about running processes.

## Service Checks

### 3. Check service status

```bash
systemctl status ssh
```

This command shows whether the SSH service is running or stopped.

### 4. Check running services

```bash
systemctl list-units --type=service --state=running
```

This command lists the services that are currently running.

## Log Checks

### 5. Check SSH service logs

```bash
journalctl -u ssh -n 20
```

This command shows the latest 20 logs of the SSH service.

### 6. Check recent system logs

```bash
journalctl -n 20
```

This command shows the latest system log entries.

## Mini Troubleshooting Flow

If a service is not working:

1. Check the process using `ps`.
2. Check the service using `systemctl status`.
3. Check the logs using `journalctl`.
4. Identify the error.
5. Take the required action.

## Key Learning

Today I practiced Linux processes, services, and logs. I learned how to check running processes, inspect services, and use logs for basic troubleshooting.
