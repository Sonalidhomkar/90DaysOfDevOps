# Day 26 – GitHub CLI: Manage GitHub from Your Terminal

## Overview

Today, I explored GitHub CLI (`gh`), a powerful command-line tool that allows developers to interact with GitHub directly from the terminal without constantly switching to the browser.

GitHub CLI simplifies repository management, issue tracking, pull requests, GitHub Actions workflows, releases, and API interactions.

## 1. Installation and Authentication

GitHub CLI can be installed on Linux, Windows, and macOS.

### Verify Installation

```bash
gh --version
```

### Authenticate with GitHub

```bash
gh auth login
```

### Check Authentication Status

```bash
gh auth status
```

### Check Active Account

```bash
gh api user --jq .login
```

**Authentication Methods Supported:**
- Web browser authentication using OAuth.
- Personal Access Token (PAT) authentication.
- Environment-based authentication using `GH_TOKEN` or `GITHUB_TOKEN`.

## 2. Working with Repositories

### Create a New Public Repository

```bash
gh repo create day-26-gh-cli-practice --public --add-readme
```

### Clone a Repository

```bash
gh repo clone OWNER/REPOSITORY
```

### View Repository Details

```bash
gh repo view OWNER/REPOSITORY
```

### List All Repositories

```bash
gh repo list
```

### Open Repository in Browser

```bash
gh repo view --web
```

### Delete a Test Repository

```bash
gh repo delete OWNER/day-26-gh-cli-practice --yes
```

**Note:** Repository deletion is permanent. Always verify the repository name before deleting.

## 3. Working with Issues

### Create an Issue

```bash
gh issue create --repo OWNER/REPOSITORY \
  --title "Day 26: GitHub CLI Practice" \
  --body "Practicing GitHub issue management using GitHub CLI." \
  --label "documentation"
```

### List Open Issues

```bash
gh issue list --repo OWNER/REPOSITORY
```

### View a Specific Issue

```bash
gh issue view ISSUE_NUMBER --repo OWNER/REPOSITORY
```

### Close an Issue

```bash
gh issue close ISSUE_NUMBER --repo OWNER/REPOSITORY
```

**Automation Use Case:**

`gh issue` can be used in shell scripts to automatically create issues when a deployment fails, track bugs, list open tasks, and close issues after successful fixes.

## 4. Working with Pull Requests

### Create a Branch

```bash
git switch -c feature/day-26-practice
```

### Make Changes and Commit

```bash
git add .
git commit -m "Add Day 26 GitHub CLI practice"
```

### Push the Branch

```bash
git push -u origin feature/day-26-practice
```

### Create a Pull Request

```bash
gh pr create --fill
```

### List Open Pull Requests

```bash
gh pr list --repo OWNER/REPOSITORY
```

### View Pull Request Details

```bash
gh pr view PR_NUMBER --repo OWNER/REPOSITORY
```

### Check PR Status and Reviewers

```bash
gh pr view PR_NUMBER --json state,reviewRequests,statusCheckRollup
```

### Check PR Status Checks

```bash
gh pr checks PR_NUMBER --repo OWNER/REPOSITORY
```

### Merge Pull Request

```bash
gh pr merge PR_NUMBER --squash
```

**Merge Methods Supported:**
- Merge commit (`--merge`)
- Squash merge (`--squash`)
- Rebase merge (`--rebase`)

**How to Review Someone Else's PR:**

1. List available pull requests using `gh pr list`.
2. View the PR using `gh pr view PR_NUMBER`.
3. Check the code changes using `gh pr diff PR_NUMBER`.
4. Review the changes using `gh pr review PR_NUMBER`.
5. Approve, comment, or request changes as appropriate.

## 5. GitHub Actions and Workflows

### List Workflow Runs

```bash
gh run list --repo OWNER/REPOSITORY
```

### View a Specific Workflow Run

```bash
gh run view RUN_ID --repo OWNER/REPOSITORY
```

### Check Workflow Run Logs

```bash
gh run view RUN_ID --log --repo OWNER/REPOSITORY
```

### List Available Workflows

```bash
gh workflow list --repo OWNER/REPOSITORY
```

### Run a Workflow Manually

```bash
gh workflow run WORKFLOW_NAME.yml --repo OWNER/REPOSITORY
```

**CI/CD Use Cases:**

- `gh run` helps monitor automated builds, tests, and deployments.
- It helps identify failed workflow runs and inspect execution logs.
- `gh workflow` helps list, manage, and manually trigger workflows.
- These commands can be integrated into shell scripts for CI/CD automation and monitoring.

## 6. Useful GitHub CLI Commands

### GitHub API

```bash
gh api user
gh api repos/OWNER/REPOSITORY
```

`gh api` allows direct interaction with GitHub REST and GraphQL APIs.

### GitHub Gist

```bash
gh gist create notes.txt
gh gist list
```

Gists are useful for sharing code snippets and small files.

### GitHub Releases

```bash
gh release list
gh release view
```

Useful for viewing and managing project releases.

### GitHub Aliases

```bash
gh alias set prs 'pr list'
gh prs
```

Aliases help create shortcuts for frequently used commands.

### Search GitHub Repositories

```bash
gh search repos "devops"
```

Useful for discovering open-source projects and learning resources.

## 7. Important Observations

1. GitHub CLI makes GitHub operations easier directly from the terminal.
2. It reduces the need to switch between the terminal and browser.
3. It simplifies repository, issue, and pull request management.
4. It provides useful commands for monitoring GitHub Actions.
5. JSON output makes GitHub CLI useful for scripting and automation.
6. It can be integrated into DevOps workflows to improve productivity.

## 8. Conclusion

Day 26 helped me understand how GitHub CLI simplifies GitHub operations and supports DevOps automation.

I learned how to manage repositories, work with issues and pull requests, inspect GitHub Actions workflows, and explore useful commands such as `gh api`, `gh gist`, and `gh alias`.

**Learning Goal:** Manage GitHub more efficiently through the terminal and build a foundation for automating GitHub operations in DevOps workflows.

#90DaysOfDevOps #GitHubCLI #DevOps #GitAndGitHub
