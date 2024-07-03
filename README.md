### Git Overview
Git is a distributed version control system used for tracking changes in source code during software development. It allows multiple developers to collaborate on projects efficiently.

### Installation of Git in Linux
To install Git on Linux (e.g., CentOS, Debian, Ubuntu):

```bash
# For Debian/Ubuntu
sudo apt update
sudo apt install git

# For CentOS/RHEL
sudo yum install git
```

### Installation of GitBash in Windows
GitBash provides a Linux-like command-line interface for Git on Windows:

1. Download GitBash from [git-scm.com](https://git-scm.com/download/win).
2. Run the installer and follow the prompts. Default settings are usually sufficient.

### Overview of Git Workflow
Git workflow typically involves:
- **Working Directory**: Where you modify files.
- **Index (Staging Area)**: Where you stage changes before committing.
- **Local Repository**: Your local copy of the Git repository.
- **Remote Repository**: A shared repository (like GitHub) where your project is stored.

Common workflow steps:
1. Modify files in the working directory.
2. Stage changes using `git add`.
3. Commit changes to the local repository using `git commit`.
4. Push changes to a remote repository using `git push`.

### Working with `git init` & `git config` commands
- `git init`: Initializes a new Git repository.
- `git config`: Sets configuration options for Git.

Examples:
```bash
# Initialize a new Git repository
git init

# Configure Git username and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Creation and deletion of Git branches
- **Creation**: Use `git branch` followed by `git checkout` or `git switch`.
- **Deletion**: Use `git branch -d` to delete a local branch.

Examples:
```bash
# Create a new branch
git branch new-feature
git checkout new-feature  # or git switch new-feature

# Delete a branch
git branch -d branch-name
```
