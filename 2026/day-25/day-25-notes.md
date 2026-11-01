# Day 25 – Git Reset vs Revert & Branching Strategies

## 1. Introduction

Git provides different ways to undo mistakes and manage changes in a project. Two important commands are `git reset` and `git revert`.

In this task, I learned how these commands work, their differences, and how different branching strategies are used in real-world software development.

---

## 2. Task 1: Git Reset – Hands-On

### What is Git Reset?

`git reset` is used to move the current branch pointer to an earlier commit. Depending on the option used, it can also change the staging area and working directory.

### Types of Git Reset

**1. Git Reset --soft**

```bash
git reset --soft HEAD~1
```

- Moves HEAD back by one commit.
- Keeps changes in the staging area.
- Changes are not lost.
- Useful when you want to modify or combine commits.

**2. Git Reset --mixed**

```bash
git reset --mixed HEAD~1
```

- Moves HEAD back by one commit.
- Removes changes from the staging area.
- Keeps changes in the working directory.
- This is the default reset option.

**3. Git Reset --hard**

```bash
git reset --hard HEAD~1
```

- Moves HEAD back by one commit.
- Removes changes from the staging area.
- Discards tracked working-directory changes.
- Can permanently lose uncommitted work.

### Answers

**Q1. What is the difference between soft, mixed, and hard reset?**

- Soft: Keeps changes staged.
- Mixed: Keeps changes unstaged.
- Hard: Discards changes from the working directory and staging area.

**Q2. Which reset is destructive and why?**

`git reset --hard` is destructive because it discards tracked uncommitted changes. Recovery may be difficult or impossible.

**Q3. When would you use each one?**

- Soft: To edit the previous commit or combine commits.
- Mixed: To unstage files while keeping changes.
- Hard: To discard unwanted local changes when I am absolutely sure.

**Q4. Should you use Git Reset on already pushed commits?**

Generally, no. Reset changes commit history and can cause problems for other collaborators. For shared branches, `git revert` is usually safer.

---

## 3. Task 2: Git Revert – Hands-On

### What is Git Revert?

`git revert` is used to undo the changes introduced by a particular commit without deleting that commit from the existing history.

### Command

```bash
git log --oneline
git revert <commit-id>
```

To revert a middle commit, Git creates a new commit that reverses its changes.

### Answers

**Q1. What happens when commit Y is reverted?**

Git creates a new commit that reverses the changes introduced by commit Y. The existing commit history is preserved.

**Q2. Is commit Y still in the history?**

Yes. Commit Y remains in the history, and a new revert commit is added.

**Q3. How is Git Revert different from Git Reset?**

Git Reset moves the branch pointer backward, whereas Git Revert creates a new commit that reverses previous changes.

**Q4. Why is Git Revert safer for shared branches?**

It preserves existing commit history and does not rewrite commits already shared with other developers.

**Q5. When would you use Revert vs Reset?**

- Revert: When undoing changes in shared or pushed branches.
- Reset: When correcting local commits that have not been shared.

---

## 4. Task 3: Git Reset vs Git Revert

| Comparison | Git Reset | Git Revert |
|---|---|---|
| What it does | Moves the branch pointer to an earlier commit | Creates a new commit to undo changes |
| Removes commit from current branch history? | Yes, commits after the target are removed from the branch's visible history | No, original commit remains |
| Safe for shared/pushed branches? | Generally not recommended | Yes, usually safer |
| When to use | Correcting local commit history | Undoing changes in shared projects |

---

## 5. Task 4: Git Branching Strategies

### A. GitFlow

**How it works:**

GitFlow uses different branches for development, features, releases, and emergency fixes.

Main branches:
- `main`: Contains production-ready code.
- `develop`: Contains ongoing development changes.
- `feature`: Used to develop new features.
- `release`: Used to prepare a release.
- `hotfix`: Used to fix urgent production issues.

**Workflow:**

```text
main
 |
develop
 |
feature/login
 |
Merge into develop
 |
release/v1.0
 |
Merge into main and develop
 |
Production
```

**Where it is used:**

Projects that follow scheduled releases and need structured release management.

**Advantages:**
- Clear separation of development and production.
- Supports planned releases.
- Provides dedicated hotfix branches.

**Disadvantages:**
- More branches to maintain.
- More complicated workflow.
- Can slow down frequent releases.

### B. GitHub Flow

**How it works:**

GitHub Flow is a simple branching strategy that uses one main branch and short-lived feature branches.

**Workflow:**

```text
main
 |
feature-branch
 |
Make changes
 |
Commit and Push
 |
Pull Request
 |
Code Review
 |
Merge into main
 |
Deploy
```

**Where it is used:**

Web applications, startups, and teams that deploy frequently.

**Advantages:**
- Simple and easy to understand.
- Encourages code reviews.
- Supports continuous deployment.
- Reduces branch management complexity.

**Disadvantages:**
- Requires good testing practices.
- Main branch must remain stable.
- Not ideal for every scheduled-release workflow.

### C. Trunk-Based Development

**How it works:**

Developers frequently integrate small changes into a shared main branch called the trunk. Short-lived feature branches may be used.

**Workflow:**

```text
       Developer A
            |
       Small Changes
            |
Developer B -----> Main / Trunk
            |
       Automated Tests
            |
         Deploy
```

**Where it is used:**

Organizations practicing continuous integration and continuous delivery (CI/CD).

**Advantages:**
- Frequent code integration.
- Reduces long-running merge conflicts.
- Faster feedback.
- Supports continuous delivery.

**Disadvantages:**
- Requires strong automated testing.
- Requires disciplined development.
- Incomplete features need feature flags or other controls.

---

### Answers: Branching Strategies

**Q1. Which strategy would you use for a startup shipping fast?**

I would choose GitHub Flow because it is simple, supports frequent deployments, and makes collaboration easier through pull requests.

**Q2. Which strategy would you use for a large team with scheduled releases?**

I would choose GitFlow because it provides separate branches for development, release preparation, and production fixes.

**Q3. Which strategy does an open-source project use?**

Example: Kubernetes uses a main development branch and dedicated release branches. Its development and release processes are documented in the Kubernetes community repository.

Reference: https://github.com/kubernetes/kubernetes

---

## 6. Task 5: Git Commands Reference (Days 22–25)

### A. Setup and Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list
git init
```

### B. Basic Git Workflow

```bash
git status
git add .
git add filename
git commit -m "Commit message"
git log
git log --oneline
git diff
git diff --staged
```

### C. Branching Commands

```bash
git branch
git branch branch-name
git checkout branch-name
git checkout -b new-branch
git switch branch-name
git switch -c new-branch
git branch -d branch-name
```

### D. Remote Repository Commands

```bash
git remote -v
git remote add origin <repository-url>
git clone <repository-url>
git fetch origin
git pull origin main
git push origin main
git push -u origin branch-name
```

**Fork:** Creates your own GitHub copy of another user's repository. Forking is performed on GitHub.

### E. Merge and Rebase

```bash
git merge branch-name
git rebase main
git rebase --continue
git rebase --abort
```

### F. Stash Commands

```bash
git stash
git stash list
git stash pop
git stash apply
git stash drop
```

### G. Cherry-Pick

```bash
git cherry-pick <commit-id>
```

Cherry-pick applies the changes from a specific commit to the current branch.

### H. Reset Commands

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
```

### I. Revert Commands

```bash
git revert <commit-id>
git revert HEAD
```

### J. Git Reflog

```bash
git reflog
```

Reflog displays recent movements of HEAD and helps locate previous commit positions after accidental resets.

---

## 7. Important Observations

1. Git Reset and Git Revert are both useful for undoing mistakes.
2. Soft reset keeps changes staged.
3. Mixed reset keeps changes unstaged.
4. Hard reset discards tracked uncommitted changes.
5. Revert preserves the original commit history.
6. GitHub Flow is suitable for simple and frequent deployments.
7. GitFlow is useful for structured release management.
8. Trunk-Based Development encourages frequent integration.
9. Git Reflog can help recover previous commit positions.

---

## 8. Conclusion

Day 25 helped me understand how to safely undo Git changes and manage branches in software development.

I learned the practical differences between Git Reset and Git Revert, explored three important branching strategies, and updated my Git command reference.

These concepts are important for version control, teamwork, and real-world DevOps workflows.

**Learning Progress: 90 Days of DevOps – Day 25 Completed.**
