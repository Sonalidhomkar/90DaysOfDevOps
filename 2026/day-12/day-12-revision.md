## Goal

The goal of Day 12 is to revise and consolidate the Linux fundamentals learned during Days 01–11 of my 90 Days of DevOps Challenge.

Today, I focused on reviewing Linux processes, services, file operations, permissions, user management, and essential troubleshooting commands.

## 1. Mindset & Learning Plan

- My goal is to build a strong foundation in Linux, Git & GitHub, networking, shell scripting, Docker, AWS, and CI/CD.
- I am focusing on hands-on practice and understanding the real-world use of commands.
- I will continue documenting my learning progress and practical exercises on GitHub.
- My long-term goal is to become a DevOps and Cloud Engineer.

## 2. Processes & Services

### Commands Used

```bash
ps
ps aux
systemctl status ssh
journalctl -u ssh -n 20
```

### Key Learnings

- `ps` displays processes associated with the current terminal session.
- `ps aux` displays a detailed list of running processes.
- `systemctl status ssh` checks the status of the SSH service.
- `journalctl -u ssh -n 20` displays the latest 20 log entries for the SSH service.

**Observation:** These commands help inspect running processes, check service status, and investigate service-related issues.

Note: The SSH service name and availability depend on the Linux environment.

## 3. File Operations & Permissions

### Commands Used

```bash
mkdir -p ~/day-12-practice
cd ~/day-12-practice

touch revision.txt
echo "Day 12 Linux Revision" > revision.txt
cat revision.txt

cp revision.txt revision-backup.txt
ls -l
chmod 640 revision.txt
ls -l revision.txt
```

### Key Learnings

- `mkdir -p` creates a directory and any missing parent directories.
- `touch` creates an empty file if it does not exist.
- `echo` writes text to a file.
- `cat` displays file contents.
- `cp` copies a file.
- `ls -l` displays file permissions and ownership.
- `chmod 640` changes file permissions.

### Understanding Permission 640

| Category | Permission | Numeric Value |
|---|---|---:|
| Owner | Read and write | 6 |
| Group | Read only | 4 |
| Others | No permissions | 0 |

### Understanding Permission 755

| Category | Permission | Numeric Value |
|---|---|---:|
| Owner | Read, write, execute | 7 |
| Group | Read and execute | 5 |
| Others | Read and execute | 5 |

## 4. User & Group Verification

### Commands Used

```bash
id
ls -l revision.txt
```

### Key Learnings

- `id` displays the current user's UID, GID, and group memberships.
- `ls -l` helps verify file ownership and permissions.
- `chown` changes file ownership and may require administrator privileges.

Example:

```bash
sudo chown user1:group1 revision.txt
ls -l revision.txt
```

Replace `user1` and `group1` with valid user and group names before running this command. Change ownership only when necessary.

## 5. Five Essential Troubleshooting Commands

| Command | Purpose |
|---|---|
| `ps aux` | Inspect running processes |
| `top` | Monitor processes and resource usage |
| `df -h` | Check filesystem disk space |
| `free -h` | Check memory usage |
| `journalctl -u ssh -n 20` | Review recent SSH service logs |

These commands help investigate common process, resource, storage, and service-related issues.

## 6. Mini Self-Check

### Q1. Which three commands save you the most time right now, and why?

1. `ps aux` – Helps identify running processes.
2. `df -h` – Helps check available disk space.
3. `systemctl status ssh` – Helps check the SSH service state.

### Q2. How do you check if a service is healthy?

I would start with these commands:

```bash
systemctl status ssh
journalctl -u ssh -n 20
ps aux
```

The first command checks the service state, the second helps investigate recent logs, and the third displays running processes. Additional connectivity or application-specific checks may be required to confirm complete service health.

### Q3. How do you safely change ownership and permissions without breaking access?

I first inspect the current ownership and permissions using `ls -l`. Then I apply only the required change and verify the result.

Example:

```bash
chmod 640 revision.txt
ls -l revision.txt
```

This gives the owner read/write access, the group read access, and others no access. I avoid unnecessary permission or ownership changes.

### Q4. What will you focus on improving in the next three days?

- Practicing Linux file permissions and ownership.
- Improving my understanding of processes, services, and logs.
- Strengthening Git and GitHub command-line skills.
- Continuing hands-on practice and documenting my results.

## 7. Key Takeaways

- Revision strengthens my understanding of Linux fundamentals.
- Combining commands helps with systematic troubleshooting.
- File permissions and ownership must be managed carefully.
- Verifying command output is an important part of practical learning.
- Consistent practice helps build confidence in Linux administration.

## Conclusion

Day 12 was dedicated to revising and consolidating the Linux fundamentals learned during Days 01–11 of my 90 Days of DevOps Challenge.

I will continue developing my DevOps skills through regular hands-on practice, troubleshooting, and documentation.

**Challenge:** 90 Days of DevOps  
**Day:** 12 – Breather & Revision

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
