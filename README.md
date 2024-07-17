### What is GitHub
- GitHub is a web-based platform used for version control and collaborative software development.
- It is built around the Git version control system and provides a range of features to facilitate code sharing, collaboration, and project management. 

### Creation of GitHub Account
1. Visit [GitHub](https://github.com/) and click on "Sign up".
2. Follow the prompts to create your GitHub account with a username, email, and password.

### GitHub Dashboard Overview
After logging in, the GitHub dashboard provides access to repositories, pull requests, issues, and settings.

----

### Push code from a local repository to a remote GitHub repository:

1. **Create a Repository on GitHub**:
   - Go to [GitHub](https://github.com/) and log in.
   - Click on the "+" icon in the top right corner and select "New repository".
   - Fill in the repository details (name, description, visibility, etc.) and click "Create repository".

2. **Add the GitHub Remote URL to Your Local Repository**:
   - In your local project directory, open a terminal or command prompt.
   - Add the remote URL using the following command:
     ```sh
     git remote add origin [git-url]
     ```
   - Replace `[git-url]` with the URL of your GitHub repository (which can be found on the GitHub repository page).

3. **Push Code to the Remote Repository**:
   - Use the following command to push your local code to the remote repository:
     ```sh
     git push -u origin main
     ```
   - If your local branch is named something other than `main`, replace `main` with the name of your branch.

Note: If the repository is private, you will be prompted to enter your GitHub username and password to authenticate and push the code to the remote repository.

----
### Changing Existing Remote URL in Local
To change the remote URL in your local Git repository:

```bash
git remote set-url origin new_remote_url
```
----

### Cloning the Repository from Remote to Local
To clone a repository from GitHub to your local machine:

```bash
git clone https://github.com/username/repository.git
```
----

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
