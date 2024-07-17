### Working with `git reset`

The `git reset` command is used to undo changes by moving the current `HEAD` to a specified commit. It has three modes:

1. **Soft Reset**:
   - Moves the `HEAD` to a specified commit but leaves changes in the staging area.
   - Example:
     ```sh
     git reset --soft [commit_id]
     ```

2. **Mixed Reset** (default mode):
   - Moves the `HEAD` to a specified commit, clears the staging area, but leaves the working directory unchanged.
   - Example:
     ```sh
     git reset --mixed [commit_id]
     ```

3. **Hard Reset**:
   - Moves the `HEAD` to a specified commit and discards all changes in the staging area and working directory.
   - Example:
     ```sh
     git reset --hard [commit_id]
     ```
----
### Working with `git revert`

The `git revert` command is used to reverse changes by creating a new commit that inverts the specified changes. This approach preserves the commit history.

- Example:
  ```sh
  git revert [commit_id]
  ```
----
### Working with `.gitignore`

A `.gitignore` file specifies which files and directories to ignore in a Git repository. You can create multiple `.gitignore` files in different directories within your repository.

- Example:
  ```
  # .gitignore
  *.log
  /node_modules
  /build
  ```
----
### Working with `git diff`

The `git diff` command is used to display the differences between various Git data sources (e.g., files, commits, branches).

- Example:
  ```sh
  git diff
  ```
----
### Working with `git HEAD`

`HEAD` is a reference to the last commit in the current checked-out branch. It is like a pointer to any reference.

- **View the latest commit**:
  ```sh
  git show HEAD
  ```

- **Switch branches**:
  When you switch branches with `checkout`, the `HEAD` is updated to point to the new branch.

  ```sh
  git checkout [branch_name]
  ```
  ----

### Deletion of GitHub Repository
To delete a GitHub repository:
1. Go to the repository on GitHub.
2. Go to "Settings" > "Options".
3. Scroll down to the "Danger Zone" section and click "Delete this repository".
----
### Overview of Feature Branching Strategy
- Feature branches are created from the development branch.
- Once development on the feature branch is completed by developers, they merge the feature branch into the development branch.
- Subsequently, the code from the development branch is deployed to lower environments.
- If everything functions correctly, the changes are merged into the master branch.
- The master branch is then deployed to production.
- If an issue is detected in the master branch, a hotfix branch is created from it


### Overview of Release Branching Strategy
- A release branch is created from the master branch or another release branch.
- Once development on the release branch is completed by developers, the code is deployed to lower environments.
- If everything is functioning correctly, it is then merged into the master branch.
- The master branch is subsequently deployed to production.
- If an issue is detected in the master branch, a hotfix branch is created from it.


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
