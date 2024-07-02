# Curriculum

## Day 1: Introduction to Methodologies and AWS Basics

- **What is Waterfall & Agile Methodology**
- **DevOps Overview**
- **Lab Session:**
  - Creation of AWS account
  - Creation of Linux EC2 instance
  - Downloading PuTTY and PuTTYgen
  - Connecting to the Linux server
  - Create and Connect to the Ubuntu server
  - Create and Connect to the Windows server

## Day 3: Linux Basics

- **Linux Overview**
- **Lab Session:**
  - Linux Basic commands with examples
  - Linux directory structure
  - Working with files
  - Working with directories
  - Working with `cp` & `mv` commands
  - Working with soft, hard links, and inode numbers
  - Working with file permissions
  - Working with file ownership

## Day 4: Advanced Linux

- **Lab Session:**
  - Working with `rm` command
  - Creating and deleting users
  - Creating and deleting groups
  - Working with `head` & `tail`
  - Working with `top` & `free` commands
  - Working with `yum` command
  - Working with `rpm`

## Day 5: Linux Utilities

- **Lab Session:**
  - Working with `find` command
  - Working with `df`, `du`, `kill`, `ps` commands
  - Working with `echo`, `env`, `tac` commands
  - Working with `sleep`, `exit`, `host`, `diff` commands
  - Working with `scp`, `ssh` commands
  - Working with `crontab` & `sed` commands
  - Working with `telnet` & `netstat` commands
  - Working with `nslookup` & `ifconfig`

## Day 7: Introduction to Git

- **Git Overview**
- **Lab Session:**
  - Installation of Git in Linux
  - Installation of Git in Ubuntu
  - Installation of GitBash in Windows
  - Overview of Git Workflow
  - Working with `git init` & `git config` commands
  - Creation and deletion of Git branches

## Day 8: Working with GitHub

- **Lab Session:**
  - Creation of GitHub account
  - GitHub Dashboard Overview
  - Push code from local to remote
  - Changing the existing remote URL in local
  - Cloning the repository from remote to local
  - Difference between `git pull` and `git fetch`
  - Working with `git merge` & `git rebase`

## Day 9: Advanced Git

- **Lab Session:**
  - Working with `git reset` command
  - Working with `git revert` command
  - Working with `.gitignore` file
  - Working with `git diff` & `git HEAD`
  - Deletion of GitHub repository

## Day 10: Introduction to GitLab and Bitbucket

- **Lab Session:**
  - Creation of GitLab account
  - GitLab Dashboard Overview
  - Creation of Git repository in GitLab
  - Deletion of GitLab repository
  - Creation of Bitbucket account
  - Bitbucket Dashboard Overview
  - Overview of feature branching strategy
  - Overview of release branching strategy

## Day 11: Maven Basics

- **What is a Build Tool**
- **What is Maven**
- **Lab Session:**
  - Download MobaXterm in Windows
  - Installation of Maven in Linux
  - Installation of Maven in Windows
- **What is `pom.xml`**
- **What is `settings.xml`**
- **Types of Maven Repository**

## Day 12: Working with Maven

- **Lab Session:**
  - Creation of Java application using Maven
  - Maven Build Lifecycles
  - Creation of web application using Maven
  - Explain about skip test cases & JaCoCo plugin
  - Explore `pom.xml` options

## Day 13: Nexus

- **Nexus Overview**
- **Lab Session:**
  - Installation of Nexus in Linux
  - Setup Nexus as a service in Linux
  - Installation of Nexus in Windows
- **Nexus Dashboard Overview**
- **Lab Session:**
  - Creation of users and roles in Nexus
  - Integrating Nexus in Maven

## Day 14: JFrog Artifactory

- **JFrog Artifactory Overview**
- **Lab Session:**
  - Installation of JFrog Artifactory in Linux
  - Installation of JFrog Artifactory in Windows
- **JFrog Artifactory Dashboard Overview**
- **Lab Session:**
  - Creation of users and groups in JFrog Artifactory
- **JFrog Repository Management**
- **Lab Session:**
  - Integrating JFrog in Maven

## Day 15: SonarQube

- **SonarQube Overview**
- **Lab Session:**
  - Installation of SonarQube in Linux
  - Setup Sonar as a service in Linux
- **SonarQube Dashboard Overview**
- **Lab Session:**
  - Creation of user in SonarQube
  - Integrating SonarQube in Maven

## Day 16: Tomcat

- **What is Tomcat**
- **Types of roles available in Tomcat**
- **Lab Session:**
  - Installation of Tomcat in Amazon Linux
  - Tomcat Dashboard Overview
  - Setup Tomcat as a service in Linux
  - Deploy WAR file in Tomcat

## Day 17: Jenkins Basics

- **Jenkins Overview**
- **Ways to install Jenkins in Linux**
- **Lab Session:**
  - Installation of Jenkins using `yum`
  - Install Jenkins to deploy WAR file in Tomcat
  - Installation of Jenkins using WAR file
- **Jenkins Dashboard Overview**
- **Exploring the options under Manage Jenkins**

## Day 18: Working with Jenkins

- **Lab Session:**
  - Creation of a Jenkins job
  - How to reset Jenkins admin user's password
  - Setup Maven project in Jenkins
  - Integrating Nexus in Jenkins

## Day 19: Jenkins Integration

- **Lab Session:**
  - Integrating JFrog with Jenkins
  - Integrating SonarQube with Jenkins
  - Deploying WAR file in Tomcat using Jenkins
  - Exploring build periodically, poll SCM, webhook
  - Creation of Slack account
  - Send notifications from Jenkins to Slack

## Day 20: Jenkins User Management

- **Lab Session:**
  - Creation of users in Jenkins
  - Setting up role-based authorization strategy in Jenkins
  - Backup and restore Jenkins
  - Restart, safe restart, copy, and move jobs
  - Upstream and downstream jobs
  - Setting up build pipeline
- **What is master and slave node**
- **Lab Session:**
  - Setting up the Linux slave node in Jenkins
  - Setting up the Windows slave node in Jenkins

## Day 22: Jenkins Pipeline

- **Jenkins Pipeline Overview**
- **Fields available in declarative pipeline**
- **Exploring the options in declarative pipeline**
- **Lab Session:**
  - Jenkins pipeline build & push to JFrog Artifactory
  - Jenkins pipeline build & deploy to Tomcat

## Day 23: Ansible Basics

- **Ansible Overview**
- **Lab Session:**
  - Installation of Ansible in Linux
  - Ansible Workflow
  - Overview of Ansible ad-hoc with examples
- **SSH Overview**
- **Lab Session:**
  - Setting up the SSH connection manually
- **Ansible Modules Overview**

## Day 24: Working with Ansible Playbooks

- **Ansible Playbook Overview**
- **Lab Session:**
  - Installation of `httpd` & Git using Ansible playbook
  - Exploring `with_items`
  - Exploring variables
  - Exploring tags
  - Installation of Tomcat using Ansible playbook
  - Explore Ansible playbook options

## Day 25: Ansible Roles

- **Ansible Role Overview**
- **Ansible Role Directory Structure**
- **Lab Session:**
  - Installation of `httpd` using Ansible role
  - Working with Ansible role
- **Overview of Ansible Vault**
- **Lab Session:**
  - Working with Ansible Vault

## Day 26: Introduction to Docker

- **Difference between containerization and virtual machines**
- **Docker Overview**
- **Exploring the available Docker components**
- **Lab Session:**
  - Installation of Docker in Linux
  - Installation of Docker in Ubuntu
  - Installation of Docker in Windows
- **Dockerfile Overview**
- **Lab Session:**
  - Creating a Dockerfile

## Day 27: Docker Hub and Images

- **What is DockerHub**
- **Lab Session:**
  - Creation of DockerHub account
- **What is Docker storage**
- **What is Docker image**
- **Lab Session:**
  - Docker image commands with examples

## Day 28: Docker Containers and Networking

- **What is Docker container**
- **Lab Session:**
  - Docker container commands with examples
- **What is Docker network**
- **Lab Session:**
  - Working with Docker network
- **What is Docker volume**
- **Lab Session:**
  - Working with Docker volume

## Day 30: Real-Time Project

- **What is a Shared Library in Jenkins**
- **Difference Between Without and With Jenkins Shared Library**
- **Getting Started With Shared Libraries**
  - Clone
