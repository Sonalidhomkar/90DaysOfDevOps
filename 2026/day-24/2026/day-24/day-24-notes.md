# Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick

## Overview

Today, I learned advanced Git concepts that help manage branches, maintain clean commit history, save unfinished work, and apply specific commits across branches.

## 1. Git Merge

**What is Git Merge?**

Git Merge combines changes from one branch into another branch.

**Types of Merge:**

- **Fast-Forward Merge:** Happens when the target branch has no new commits since the feature branch was created. Git simply moves the branch pointer forward.
- **Three-Way Merge:** Happens when both branches have new commits. Git combines their changes and creates a merge commit.

**What is a Merge Conflict?**

A merge conflict occurs when Git cannot automatically combine changes, usually because the same part of a file was modified differently in two branches.

**Commands:**
```bash
git switch main
git merge feature-login
git log --oneline --graph --all
```

To resolve a conflict:
1. Open the conflicted file.
2. Review both changes.
3. Edit and keep the correct content.
4. Save the file.
5. Stage and commit the resolved changes.

```bash
git add .
git commit
```

## 2. Git Rebase

**What is Git Rebase?**

Git Rebase moves or replays commits from one branch on top of another branch.

**Rebase vs Merge:**

- Merge preserves the original branch history and may create a merge commit.
- Rebase replays commits and creates a more linear history.
- Rebase changes commit hashes because it creates new commits.

**Why should we avoid rebasing shared commits?**

Rebasing commits that have already been pushed and shared with others rewrites history. It can create confusion and integration problems for collaborators.

**Commands:**
```bash
git switch feature-dashboard
git rebase main
git log --oneline --graph --all
```

**When to use:**
- Use Merge when you want to preserve branch history.
- Use Rebase when you want a clean, linear history for local or private work.

## 3. Squash Merge vs Regular Merge

**What is Squash Merge?**

Squash Merge combines multiple commits from a feature branch into one new commit on the target branch.

**Command:**
```bash
git switch main
git merge --squash feature-profile
git commit -m "Add profile feature"
```

**Difference:**

- Squash Merge: Adds one combined commit to the target branch.
- Regular Merge: Integrates the branch history and may create a merge commit.

**When to use:**
- Squash Merge: When a feature branch contains many small development commits.
- Regular Merge: When you want to preserve individual commits and branch history.

**Trade-off:**

Squashing creates a cleaner history, but individual commits from the feature branch are not preserved in the target branch's history.

## 4. Git Stash

**What is Git Stash?**

Git Stash temporarily saves uncommitted changes so that you can switch branches and work on another task without committing unfinished work.

**Important Commands:**
```bash
git stash
git stash push -m "Work in progress"
git stash list
git stash apply
git stash pop
git stash apply stash@{1}
```

**Difference between Pop and Apply:**

- `git stash pop`: Applies the saved changes and removes that stash entry if successful.
- `git stash apply`: Applies the saved changes but keeps the stash entry.

**Real-world use:**

Stash is useful when you are working on a feature and suddenly need to switch to another branch to fix an urgent bug.

## 5. Git Cherry Pick

**What is Cherry Pick?**

Cherry Pick allows us to apply a specific commit from another branch to the current branch without merging the entire branch.

**Commands:**
```bash
git log --oneline feature-hotfix
git switch main
git cherry-pick <commit-hash>
git log --oneline
```

**Real-world use:**

Cherry-picking is useful when a particular bug fix needs to be applied to another branch without bringing all the changes from the original branch.

**Possible Problems:**
- Cherry-pick conflicts.
- Duplicate changes or commits.
- Dependencies on other commits may be missing.

## 6. Important Git Commands Learned

| Command | Purpose |
|---|---|
| `git merge` | Combines branches |
| `git rebase` | Replays commits on another base |
| `git merge --squash` | Combines changes into one commit |
| `git stash` | Temporarily saves changes |
| `git stash list` | Lists saved stashes |
| `git stash pop` | Applies and removes a stash |
| `git stash apply` | Applies but keeps a stash |
| `git cherry-pick` | Applies a specific commit |
| `git log --oneline --graph --all` | Visualizes commit history |

## 7. Key Learnings

- Understood the difference between Fast-Forward and Three-Way Merge.
- Learned how to identify and resolve merge conflicts.
- Understood how Rebase creates a linear commit history.
- Learned the difference between Squash Merge and Regular Merge.
- Practiced saving unfinished changes using Git Stash.
- Understood how to apply specific commits using Cherry Pick.

## Conclusion

Day 24 helped me understand advanced Git workflows and how they are used in real-world development. These concepts are important for effective collaboration, branch management, and maintaining clean project history.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
