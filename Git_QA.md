# Q. What is Git?

**Git** is a **distributed version control system (VCS)** that allows multiple developers to work on a project simultaneously while tracking and managing changes to the project's codebase. It keeps a history of all changes made to files, enabling collaboration, tracking of code versions, and easy recovery of previous states.

## Key Features of Git

- **Version Control**: Git tracks changes to files and maintains a history of modifications, allowing you to revert to previous versions if needed.
- **Distributed System**: Every developer working with Git has a complete copy of the project’s repository, including its full history, on their local machine. This allows them to work independently and offline.
- **Branching and Merging**: Git allows you to create separate branches for different features or bug fixes. These branches can be merged back into the main codebase once the changes are complete and tested.
- **Collaboration**: Git enables multiple developers to collaborate on a project simultaneously without overwriting each other’s changes. Teams can efficiently manage code contributions through repositories.

## Why is Git Used?

1. **Collaboration**: Git makes it easy for multiple developers to work on the same project simultaneously without conflicts. By using branches, each developer can work independently on features, bug fixes, or experiments, and then merge their changes back into the main project.

2. **Version Control**: Git allows you to track every change made to your code. You can view who made what changes, revert to a previous version if something breaks, and compare different versions of your code.

3. **Branching and Experimentation**: With Git, you can create branches for new features or fixes, work on them without affecting the main project, and merge them when ready. This makes experimenting and working on different features in parallel very efficient.

4. **Backup and Security**: Since Git is distributed, every developer has a complete copy of the project on their local machine. Even if the central repository goes down, no data is lost as it can be restored from any developer’s local copy.

5. **Integration with CI/CD Pipelines**: Git integrates with many tools for **continuous integration** (CI) and **continuous deployment** (CD). This allows code changes to be automatically tested, built, and deployed as part of a larger DevOps workflow.

6. **Open Source and Widely Adopted**: Git is free and open-source, making it accessible to anyone. It is also the most popular version control system, widely used in open-source projects and by companies of all sizes.

## How Git Works

- **Repository**: A Git repository is a directory that tracks your project files and their history. Repositories can be local (on your machine) or remote (on services like GitHub, GitLab, etc.).
- **Commit**: A commit is a snapshot of your project at a specific point in time. Every change you make is recorded as a commit with a message describing the change.
- **Branch**: Branches allow you to work on different versions of a project in parallel. The `main` branch is usually the default, but you can create new branches for features or fixes.
- **Merge**: Merging is the process of integrating changes from one branch into another.
- **Pull and Push**: Pulling fetches the latest changes from a remote repository, while pushing sends your local commits to the remote repository.

## Common Git Commands

- **`git init`**: Initializes a new Git repository.
- **`git clone <repo-url>`**: Clones an existing repository to your local machine.
- **`git add <file>`**: Stages changes for the next commit.
- **`git commit -m "message"`**: Commits the staged changes with a descriptive message.
- **`git pull`**: Fetches the latest changes from the remote repository and merges them with your local code.
- **`git push`**: Pushes your local commits to the remote repository.
- **`git branch`**: Lists branches or creates a new branch.
- **`git checkout <branch>`**: Switches to a different branch.
- **`git merge <branch>`**: Merges another branch into the current branch.

## Summary

Git is a powerful, distributed version control system used by developers and teams to manage changes in a project's codebase, collaborate on projects, and keep a history of the work done. It’s widely used in software development because of its flexibility, efficiency, and ability to handle complex projects with multiple contributors.

# Q. What is a git repository?

A **Git repository** is a storage space where **Git** keeps all the files, version history, and configurations of a project. It tracks changes to the files over time, allowing developers to **collaborate**, **manage versions**, and **revert to previous versions** of the project.

## Key Points:
- **Version Control**: A Git repository stores the entire **history** of a project, including all commits, branches, and changes.
- **Local or Remote**: Git repositories can be **local** (on your machine) or **remote** (hosted on services like GitHub, GitLab, etc.).
- **Two Types**: A Git repository can either be **bare** (only version control data, no working files) or a **working directory** (where you can modify and work on files).

## Basic Commands:

- **Initialize a repository**:
  ```bash
  git init
  ```
This creates a new Git repository in the current directory.

- **Clone a repository**:
```bash
git clone <repository-url>
```
- With perticular branch
```
git clone -b <branch name> <repository-url>
```
This copies a remote repository to your local machine.
A Git repository is essential for version control, collaboration, and managing changes in a project.

# Q. What Does the Command `git config` Do? 

The `git config` command is used to **configure Git settings**. It allows you to set your **username**, **email**, and other preferences for Git's behavior. You can configure these settings either globally (for all repositories on your machine) or locally (for a specific repository).

## Key Use Cases:

### 1. **Global Configuration**:
Global configuration applies to all repositories on your machine. Use the `--global` flag to set options globally.

- **Set global user information** (name and email) for commits:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```
- Set the global default editor for Git commands:
  ```bash
  git config --global core.editor "vim"
  ```
### 2. **Repository-Specific Configuration**:  
Repository-specific configuration applies only to the current repository. You don't need to use the `--global` flag in this case.
- Set user information (name and email) for a specific repository:
```bash
git config user.name "Repo-Specific Name"
git config user.email "repo-specific@example.com"
```
- Set the default editor for a specific repository:
```bash
git config core.editor "nano"
```
### 3. **View Configuration Settings**:
- List all configuration settings (global and local):
```bash
git config --list
```
- View only global configuration:
```bash
git config --global --list
```

# Q. What is HEAD in Git?

In Git, **HEAD** refers to the **current commit** or **snapshot** that your working directory points to. It represents the **latest commit** in the currently checked-out branch. When you make changes or commits, those changes are added on top of the commit that `HEAD` is pointing to.

## Key Points:

- **HEAD usually points to a branch**: In most cases, `HEAD` points to the latest commit of the branch you are currently working on (e.g., `main` or `develop`).
- **Detached HEAD**: Sometimes, `HEAD` can point directly to a specific commit (e.g., when you check out a past commit or tag). This is known as a **detached HEAD** state.

## Example:

To check where `HEAD` is pointing, you can use the following command:

```bash
git log --oneline -1
```
This will show the latest commit `HEAD` is pointing to.

## Number of Heads in a Repository:
A repository can have **multiple heads** in the form of branches. Each branch represents a different line of development and has its own HEAD. However, at any given moment, there is only one active `HEAD` for your working directory, which points to the current branch or commit you're working on.
In summary:
- A Git repository can have multiple branch heads (one for each branch).
- There is only one active HEAD at a time in your working directory, pointing to the current branch or commit.

**Usage**:-
- To go or checkout to 1 commit before the latest commit, we use git checkout `HEAD~1`
- To uncommit the last 3 commits without losing the changes, we first run git reset `HEAD~3`. Then we can see the changes made in the last 3 commits and then update it manually and commit it finally.
- In order to uncommit the last 3 commits and also remove the changes, we can run the command: `git reset --hard HEAD~3`. This command will completely remove all the changes.
- To look into the changes made in the last 3 commits, we can run `git diff HEAD~3`
- - To make a new commit by reverting the last 3 commits, we can run the command: `git revert --no-commit HEAD~3...HEAD`
 
# Q. What is a Conflict in Git? 

A **conflict** in Git occurs when **two or more changes** are made to the same part of a file in different branches or commits, and Git cannot automatically merge them. Conflicts typically happen during **merge** or **rebase** operations, where changes from different branches or commits need to be combined, but the changes are incompatible.

## Key Points:
- Conflicts occur when **multiple changes** affect the same lines in a file.
- Git marks the conflicting areas and asks you to manually **resolve** the conflict by choosing which changes to keep.
- After resolving the conflict, you need to **stage** the file and **commit** the resolution.

Conflicts need manual intervention to resolve so that Git can successfully complete the merge or rebase process.

# Q. What does git status command do?
- `git status` command is used for showing the difference between the working directory and the index which is helpful for understanding git in-depth and also keep track of the tracked and non-tracked changes.

# Q. Define “Index”.
Before making commits to the changes done, the developer is given provision to format and review the files and make innovations to them. All these are done in the common area which is known as `Index` or `Staging Area`.

# Q. What does git add command do?
- This command adds files and changes to the index of the existing directory.
- You can add all changes at once using `git add .` command.
- You can add files one by one specifically using `git add <file_name>` command.
- You can add contents of a particular folder by using `git add /<folder_name>/` command.
