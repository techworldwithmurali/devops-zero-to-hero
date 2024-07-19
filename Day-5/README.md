#### INSTRUCTOR DETAILS

|  Information             | Details                                                                      |
|----------------------    |------------------------------------------------------------------------------|
| **Name**                 | Moole Muralidhara Reddy                                                      |
| **Email**                | techworldwithmurali@gmail.com                                                |
| **Website**              | https://www.techworldwithmurali.com               |
| **LinkedIn profile**     | [Moole Muralidhara Reddy](https://www.linkedin.com/in/moole-muralidhara-reddy) |


### What is Git 

Git is an open-source source code management tool and a distributed version control system designed to handle projects of all sizes with speed and efficiency.

### Advantages of Git
- **Open-Source and Free**: Git is freely available for use.
- **Flexibility**: It can be used for various workflows and project sizes.
- **Security**: Provides robust security for codebase management.
- **Cross-Platform Support**: Available on Linux, Windows, macOS, etc.
- **Branching and Merging**: Supports complex branching and merging strategies, making it easier to collaborate on projects.
----
### Types of Version Control Systems (VCS)
- **GIT**: Distributed version control system.
- **SVN (Subversion)**: Centralized version control system.
- **TFS (Team Foundation Server)**: Centralized version control system provided by Microsoft.
----
### Installation of Git

#### On CentOS 7
To install Git on CentOS 7:
```bash
yum install git -y
```
To check if Git is installed:
```bash
git --version
```
----
#### On Ubuntu
1. **Update the Package Index**:
   ```bash
   sudo apt update
   ```
2. **Install Git**:
   ```bash
   sudo apt install git
   ```
3. **Verify the Installation**:
   ```bash
   git --version
   ```
   This command should display the installed version of Git.
----
#### On Windows (GitBash)
1. **Download GitBash for Windows**: Go to the [Git for Windows download page](https://gitforwindows.org/).
2. **Start the Installer**: Once the download is complete, open the installer.
3. **Git Setup Wizard**: When the installer starts, you will see the Git Setup wizard screen.
4. **Follow the Prompts**: Click "Next" through the prompts to continue with the installation.
5. **Default Options**: The default options are suitable for most users. Click "Finish" to complete the installation.
----
### Git Workflow
![Git Workflow - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-5/images/Day%20%205-%20Git%20Workflow%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)

Git workflow typically involves:
- **Working Directory**: Where you modify files.
- **Index (Staging Area)**: Where you stage changes before committing.
- **Local Repository**: Your local copy of the Git repository.
- **Remote Repository**: A shared repository (like GitHub) where your project is stored.
----
### working with git init

- **git init** command is used to creates a new Git repository. 
- It can be used to convert an existing, unversioned project to a Git repository or initialize a new, empty repository. 
- Most other Git commands are not available outside of an  initialized repository, so this is usually the first command you'll run in a new project.
Examples:
```bash
# Initialize a new Git repository
git init
```
----
### Working with `git config` commands
- **git config** command is a convenience function that is used to set Git configuration values on a global or local project level.

Examples:
```bash
# Configure Git username and email
git config --global user.name "Your Name"
git config --global user.name "Muralidhara Reddy"
git config --global user.email "your.email@example.com"
git config --global user.email  "techworldwithmurali@gmail.com"
```
----
### Working with Git Branches

- A branch in Git is a version of the repository that diverges from the main working project.
- It allows you to work on different parts of a project simultaneously. The default branch is usually named `master`, but many projects now use `main` as the default.

#### Common Branch Commands
- **Check Existing Branches**:
  ```bash
  git branch
  ```
- **Create a New Branch**:
  ```bash
  git branch [branchname]
  ```
- **Switch to a Branch**:
  ```bash
  git checkout [branchname]
  ```
- **Create and Switch to a New Branch**:
  ```bash
  git checkout -b [branchname]
  ```
- **Delete a Branch**:
  ```bash
  git branch -d [branchname]
  ```
----
### Working with Git Merge

Merging in Git combines the changes from different branches into a single branch. This is usually done when you want to integrate changes from a feature branch into the main branch.

#### Example of Merging
1. **Switch to the Branch You Want to Merge Into**:
   ```bash
   git checkout master
   ```
2. **Merge the Feature Branch**:
   ```bash
   git merge [feature-branch]
   ```
----
### Working with Git Rebase

Rebasing is another way to integrate changes from one branch into another. It moves or combines a sequence of commits to a new base commit. Rebasing is useful for maintaining a clean, linear project history.

#### Example of Rebasing
1. **Switch to the Branch You Want to Rebase**:
   ```bash
   git checkout [feature-branch]
   ```
2. **Rebase onto Another Branch**:
   ```bash
   git rebase master
   ```
   ----
### Difference Between Git Merge and Git Rebase

- **Commit History**:
  - **Merge**: Preserves the complete history of both branches, resulting in a merge commit that has two parents.
  - **Rebase**: Rewrites the commit history to create a linear progression of commits.
  
- **Workflow Impact**:
  - **Merge**: Keeps the project history as is, showing when branches diverged and merged.
  - **Rebase**: Makes the project history cleaner and linear but can potentially rewrite shared commit history, leading to complications if others are working on the same branch.
  
- **Conflict Resolution**:
  - **Merge**: Conflicts are resolved once, during the merge commit.
  - **Rebase**: Conflicts may need to be resolved at each commit being rebased.

### When to Use
- **Git Merge**:
  - When you want to preserve the context of feature branches and see the complete history.
  - When working in a team where preserving the commit history is important.

- **Git Rebase**:
  - When you want a clean, linear history without merge commits.
  - When working on a feature branch that you want to update with the latest changes from the main branch before merging.
