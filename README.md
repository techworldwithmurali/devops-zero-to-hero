Git is an open-source source code management tool and a distributed version control system designed to handle projects of all sizes with speed and efficiency.

### Advantages of Git
- **Open-Source and Free**: Git is freely available for use.
- **Flexibility**: It can be used for various workflows and project sizes.
- **Security**: Provides robust security for codebase management.
- **Cross-Platform Support**: Available on Linux, Windows, macOS, etc.
- **Branching and Merging**: Supports complex branching and merging strategies, making it easier to collaborate on projects.

### Types of Version Control Systems (VCS)
- **GIT**: Distributed version control system.
- **SVN (Subversion)**: Centralized version control system.
- **TFS (Team Foundation Server)**: Centralized version control system provided by Microsoft.

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

#### On Windows (GitBash)
1. **Download GitBash for Windows**: Go to the [Git for Windows download page](https://gitforwindows.org/).
2. **Start the Installer**: Once the download is complete, open the installer.
3. **Git Setup Wizard**: When the installer starts, you will see the Git Setup wizard screen.
4. **Follow the Prompts**: Click "Next" through the prompts to continue with the installation.
5. **Default Options**: The default options are suitable for most users. Click "Finish" to complete the installation.

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
