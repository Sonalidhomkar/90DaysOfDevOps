# Day 28 – Revision Day: Days 1 to 27

## Objective
Today's goal was to revise previously learned DevOps concepts, identify knowledge gaps, strengthen practical skills, and improve my understanding through hands-on practice.

## 1. Topics Revised

### Linux Administration
- Linux architecture and file system hierarchy
- Basic Linux commands and file management
- Process and service management
- Users, groups, permissions and ownership
- Disk management and LVM
- System monitoring and troubleshooting

### Networking
- IP addressing and subnetting
- DNS resolution
- Common network ports
- Network troubleshooting using ping, curl, ss and dig

### Shell Scripting
- Variables and user input
- Conditional statements and loops
- Functions and command-line arguments
- Error handling using `set -euo pipefail`
- Cron jobs and automation
- Backup scripts and log analyzer

### Git & GitHub
- Repository initialization and commits
- Branching and merging
- Merge vs rebase
- Git stash and cherry-pick
- Git reset and revert
- GitFlow, GitHub Flow and Trunk-Based Development
- GitHub CLI commands

### GitHub Profile
- Profile README
- Repository organization
- Developer branding

## 2. Quick-Fire Questions and Answers

**1. What does chmod 755 script.sh do?**

It gives the owner read, write and execute permissions, while the group and others get read and execute permissions.

**2. What is the difference between a process and a service?**

A process is a running instance of a program. A service is a background program designed to provide functionality, often managed by systemd.

**3. How do you find which process is using port 8080?**

```bash
sudo ss -tulpn | grep :8080
```

**4. What does set -euo pipefail do?**

- `-e`: Exit when a command fails.
- `-u`: Treat unset variables as errors.
- `-o pipefail`: Detect failures in pipeline commands.

**5. Difference between git reset --hard and git revert?**

`git reset --hard` moves the current branch pointer and discards uncommitted changes. `git revert` creates a new commit that reverses an earlier commit.

**6. Which branching strategy is suitable for a team of five developers shipping weekly?**

GitHub Flow is a good choice because it supports feature branches, pull requests, code reviews and frequent deployments.

**7. What does git stash do?**

It temporarily saves uncommitted changes so that I can switch branches or work on another task without committing incomplete work.

**8. How do you schedule a script to run every day at 3 AM?**

```bash
0 3 * * * /path/to/script.sh
```

**9. Difference between git fetch and git pull?**

`git fetch` downloads changes from the remote repository without merging them. `git pull` fetches and integrates changes into the current branch.

**10. What is LVM?**

Logical Volume Management allows flexible disk space management by combining physical storage into volume groups and creating logical volumes that can be resized when needed.

## 3. Teach It Back – Git Branching

Git branching allows developers to work on different features independently without affecting the main project.

A branch is like a separate workspace for a developer.

Developers can create branches for new features or bug fixes.

They can make changes and test their work independently.

Once the work is complete, the branch can be merged into the main branch.

This makes teamwork easier and helps maintain a clean codebase.

Git branching is an important skill for collaborative software development and DevOps workflows.

## 4. Key Learnings

- Revised important Linux administration commands.
- Strengthened understanding of networking fundamentals.
- Reviewed shell scripting and automation concepts.
- Practiced Git and GitHub workflows.
- Improved understanding of troubleshooting and version control.
- Identified areas that need more hands-on practice.

## 5. Conclusion

Day 28 was a valuable revision day. It helped me revisit important concepts, evaluate my understanding, and identify areas for improvement.

I believe consistent revision and practical implementation are essential for becoming a confident DevOps Engineer.

**Learning continues! 🚀**

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
