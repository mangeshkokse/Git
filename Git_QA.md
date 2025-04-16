# Git

## Q. What is Git?

Git is a distributed version control system (VCS) that allows multiple developers to work on a project simultaneously while tracking and managing changes to the project's codebase.

- **Version Control**: Git tracks changes to files and maintains a history of modifications, allowing you to revert to previous versions if needed.
- **Distributed System**: Every developer working with Git has a complete copy of the project’s repository, including its full history, on their local machine. This allows them to work independently and offline.
- **Branching and Merging**: Git allows you to create separate branches for different features or bug fixes. These branches can be merged back into the main codebase once the changes are complete and tested.

## Q. How Git Works
- Git manages your code as a series of snapshots stored in a local repository. Each time you "commit", Git saves the current state of your local project.

## How to Initialize a new Git repository.
1. Create your project folder
```sh
cd path/to/your/project
```
2. Initialize Git
```sh
git init
```
- Creates a hidden .git/ directory
- This is where Git stores all the version history, configs, and metadata.

## Which are the Common Git Commands?

- **`git init`**: Initializes a new Git repository.
- **`git clone <repo-url>`**: Clones an existing repository to your local machine.
- **`git add <file>`**: Stages changes for the next commit.
- **`git commit -m "message"`**: Commits the staged changes with a descriptive message.
- **`git pull`**: Fetches the latest changes from the remote repository and merges them with your local code.
- **`git push`**: Pushes your local commits to the remote repository.
- **`git branch`**: Lists branches or creates a new branch.
- **`git checkout <branch>`**: Switches to a different branch.
- **`git merge <branch>`**: Merges another branch into the current branch.

## Q. What is a git repository?

A **Git repository** is a storage space where **Git** keeps all the files, version history, and configurations of a project. It tracks changes to the files over time, allowing developers to **collaborate**, **manage versions**, and **revert to previous versions** of the project.

## Q. What Does the Command `git config` Do? 
- The git config command is used to configure Git settings for your user or repository.
- It allows you to set your **username**, **email**

### 1. **Global Configuration**:
- Global configuration applies to all repositories on your machine. Use the `--global` flag to set options globally.

- **Set global user information** (name and email) for commits:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```
- **Set the global default editor for Git commands:**
  ```bash
  git config --global core.editor "vim"
  ```
### 2. **Repository-Specific Configuration**:  
- Repository-specific configuration applies only to the current repository. You don't need to use the `--global` flag in this case.
```bash
git config user.name "Repo-Specific Name"
git config user.email "repo-specific@example.com"
```
- Set the default editor for a specific repository:
- This command sets nano as the default text editor for the current repository only. So, when you perform tasks like writing commit messages or resolving merge conflicts, Git will open nano instead of the default editor (e.g., Vim or Emacs).
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

## Q. What is HEAD in Git?

- In Git, **HEAD** points to the **latest commit** or **snapshot** that your working directory points to. It is the `latest commit` in the currently checked-out branch. When you make changes or commits, those changes are added on top of the commit that `HEAD` is pointing to.
- A Git repository can have multiple branch heads (one for each branch).
- To go or checkout to the 1st commit before the latest commit, we use git checkout `HEAD~1`
- To check where `HEAD` is pointing, you can use the following command:
```bash
git log --oneline -1
```
This will show the latest commit `HEAD` is pointing to.
 
## Q. What is a Conflict in Git? 
- A conflict in Git happens when two different changes are made to the same part of a file, and Git doesn’t know which version to keep.
- Git Conflicts Occurs
  - Merging branches
  - Rebasing
  - Cherry-picking
  - Pulling changes from remote when local changes get conflict
- Conflicts need manual intervention to resolve so that Git can successfully complete the merge or rebase process.

## Q. Define “Index”.
- Before making commits to the changes done, the developer is given provision to format and review the files and make the changes. All these are done in the common area which is known as `Index` or `Staging Area`.

## Q. What does git add command do?
- This command adds files and changes to the Staging Area of the existing directory.
- You can add all changes at once using `git add .` command.
- You can add files one by one specifically using `git add <file_name>` command.
- You can add the contents of a particular folder by using `git add /<folder_name>/` command.

## Q. What is Squash.
In Git, "squash" means combining multiple commits into a single commit. This process helps to get up commit history by merging the changes of several commits into one, making the history cleaner and easier to understand.

## Q. How would you recover a branch that has already pushed changes in the central repository but has been accidentally deleted from every team member’s local machines?
To recover a branch that has been pushed to a central repository but deleted locally, follow these 
steps:
### 1. Fetch all branches from the remote:
```bash
git fetch origin
```
### 2. List all remote branches to find the deleted branch:
```bash
git branch -r
```
Look for the branch in the list (e.g., `origin/branch-name`).

### 3. Restore the deleted branch locally: 
Once you identify the branch, check it out from the remote:
```bash
git checkout -b branch-name origin/branch-name
```
This will recreate the branch on your local machine, and you can now continue working with it.

## Q. What is `git reflog`?
- `git reflog` is a command that shows a log of where your `HEAD` and branch references have been, even if those commits are no longer visible through `git log`.

**Key points about `git reflog`**:
- **Local history**: `git reflog` is stored locally, and it doesn't get pushed to the remote repository. It's useful for recovering lost commits or branches that you might have deleted accidentally.
- **Recovery tool**: If you reset a branch or lose a commit, you can use git reflog to find the commit hash and recover it.
```bash
git reflog
```
This command shows you a list of recent changes to the `HEAD`, including commit hashes, actions, and messages.
- **Example output**:
```bash
c3d5e2a HEAD@{0}: reset: moving to HEAD^
91a5b89 HEAD@{1}: commit: added a new feature
e8c29f1 HEAD@{2}: checkout: moving from main to feature-branch
```
By using `git reflog`, you can identify where your commits or changes were lost and recover them by checking out or resetting to the relevant commit hash.

## Q. what is the stash in Git
- In `git stash` is like a temporary shelf where you can save your uncommitted changes without committing them,x so you can work on something else, then come back later and pick them up.
- How it works
  - Run `git stash` In the current working directory in the middle of code changes.
  - Now, Work on something else or switch branches: `git checkout feature-branch`
  - Come back and apply it: `git stash apply`

## Q. What does `git annotate` command do?
The `git annotate` command, also known as `git blame`, shows line-by-line details about who last modified each line in a file, along with the corresponding commit. It's useful for tracking changes and understanding the history of a file.

```bash
git annotate <filename>
```
or
```bash
git blame <filename>
```
This will show you, for each line in the file, who last modified it, in which commit, and when. It's commonly used to trace the history of specific code changes.

## Q. What is the difference between git stash apply vs git stash pop command?
1. `git stash apply`:
- This command applies the stashed changes to your working directory but keeps the stash intact.
- The stash remains available for future use.
- Use it if you want to apply the changes without removing the stash.
  
2. `git stash pop`:
- This command applies the stashed changes to your working directory and removes the stash after applying it.
- It's a combination of `git stash apply` and `git stash drop` (which deletes the stash).
- Use it if you want to apply the changes and no longer need to keep the stash.

# Q. Difference between `git pull` and `git fetch`
1. `git fetch` - Check for changes only
   - It downloads the latest changes from the remote repo.
   - But it doesn’t apply them to your current branch.
   - After git fetch, you still need to run git merge or git rebase to update your branch.

2. `git pull` - Download + apply changes
   - It does both: fetch + merge in one step.
   - It updates your current branch with remote changes immediately.
   - Your branch is now up to date with the remote.

## Q. What is the diff betn git merge and git rebase ?
Think of Branches Like Two Lanes of Work, You're working on a feature branch, and there's also the main branch. Now you want to bring changes from main into your feature branch. 

**You have two ways:**
1. git merge -  (Combine, keep history)
   - Merges the changes from one branch into another and creates a merge commit.
   - Keeps full history of both branches (shows where they diverged).
   ```bash
   git checkout feature
   git merge main
   ```
2. git rebase - (Rewrite history, linear)   
   - What it does: Moves your commits on top of another branch as if they were written after it.
   - Creates a cleaner, linear history.
   ```bash
   git checkout feature
   git rebase main
   ```

## Q. what is the command to fixed the broken commit ?
- A "broken commit" refers to a commit that introduces issues or mistakes into the codebase. These issues could be anything from a bug, incorrect logic, or a failed test to incorrect commit messages or missing files.

```bash
git commit --amend
```
- It works like 
```bash
git add <file>
git commit --amend
```
- Then, Replace the commit entirely:
```bash
git commit --amend -m "New fixed message"
```

## Q. Git commands

1. git init
Initializes a new Git repository in the current directory.
Example: git init
2. git clone
Copies a remote repository to the local machine.
Example: git clone https://github.com/user/repo.git
3. git status
Displays the state of the working directory and staging area.
Example: git status
4. git add
Adds changes to the staging area.
Example: git add file.txt
5. git commit
Records changes to the repository.
Example: git commit -m "Initial commit"
6. git config
Configures user settings, such as name and email.
Example: git config --global user.name "Your Name"
