### Working with `git reset` command
- **git reset**: Resets the current HEAD to a specified state.

Example:
```bash
# Reset staged changes (keep modifications)
git reset --soft HEAD^

# Reset staged changes and modifications
git reset --hard HEAD^
```

### Working with `git revert` command
- **git revert**: Reverts specified commits by creating a new commit.

Example:
```bash
# Revert the last commit
git revert HEAD

# Revert a specific commit
git revert <commit_hash>
```

### Working with `.gitignore` file
`.gitignore` file specifies files to ignore in Git operations.

Example content:
```
# Ignore .log files
*.log

# Ignore directory
logs/
```

### Working with `git diff` & `git HEAD`
- **git diff**: Shows changes between commits, commit and working tree, etc.
- **git HEAD**: Points to the most recent commit in the current branch.

Example:
```bash
# Show changes between HEAD and working tree
git diff HEAD

# Show changes between two commits
git diff commit1 commit2
```

### Deletion of GitHub Repository
To delete a GitHub repository:
1. Go to the repository on GitHub.
2. Go to "Settings" > "Options".
3. Scroll down to the "Danger Zone" section and click "Delete this repository".

### Overview of Feature Branching Strategy
Feature branching involves creating a separate branch for each new feature or change. This isolates development work and facilitates collaboration.

### Overview of Release Branching Strategy
Release branching involves creating a branch dedicated to preparing a release version of the software. It allows stabilization and last-minute changes before deployment.

### Creation of GitLab Account
1. Visit [GitLab](https://gitlab.com/users/sign_in) and click "Register".
2. Follow the prompts to create your GitLab account.

### GitLab Dashboard Overview
After logging in, GitLab dashboard provides access to projects, issues, merge requests, pipelines, and settings.

### Creation of Git Repository in GitLab
To create a new Git repository in GitLab:
1. Navigate to your GitLab dashboard.
2. Click on "New Project" and follow the prompts to set up your repository.

### Deletion of GitLab Repository
To delete a GitLab repository:
1. Go to the repository in GitLab.
2. Go to "Settings" > "General" > "Advanced settings".
3. Scroll down to the "Danger Zone" section and click "Remove repository".
