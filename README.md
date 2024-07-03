### Creation of GitHub Account
1. Visit [GitHub](https://github.com/) and click on "Sign up".
2. Follow the prompts to create your GitHub account with a username, email, and password.

### GitHub Dashboard Overview
After logging in, the GitHub dashboard provides access to repositories, pull requests, issues, and settings.

### Push Code from Local to Remote
To push code from your local repository to GitHub:

```bash
# Add files to staging area
git add .

# Commit changes
git commit -m "Your commit message"

# Push changes to remote (origin)
git push origin main  # Replace `main` with your branch name if different
```

### Changing Existing Remote URL in Local
To change the remote URL in your local Git repository:

```bash
git remote set-url origin new_remote_url
```

### Cloning the Repository from Remote to Local
To clone a repository from GitHub to your local machine:

```bash
git clone https://github.com/username/repository.git
```

### Difference between `git pull` and `git fetch`
- **git pull**: Fetches from and integrates with another repository or a local branch. It's a combination of `git fetch` followed by `git merge`.
  
  Example:
  ```bash
  git pull origin main
  ```

- **git fetch**: Fetches changes from a remote repository without merging them into your current branch. Use `git merge` or `git rebase` to integrate fetched changes.

  Example:
  ```bash
  git fetch origin
  ```

### Working with `git merge` & `git rebase`
- **git merge**: Integrates changes from one branch into another. Creates a new commit with merged changes.

  Example:
  ```bash
  git checkout main
  git merge feature-branch
  ```

- **git rebase**: Moves or combines a sequence of commits to a new base commit. Rewrites commit history.

  Example:
  ```bash
  git checkout feature-branch
  git rebase main
  ```
