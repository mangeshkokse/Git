# Git

## Q. What is Git?

Git is a distributed version control system (VCS) that allows multiple developers to work on a project simultaneously while tracking and managing changes to the project's codebase. It keeps a history of all changes made to files, enabling collaboration, tracking of code versions, and easy recovery of previous states.

## Q. Key Features of Git

- **Version Control**: Git tracks changes to files and maintains a history of modifications, allowing you to revert to previous versions if needed.
- **Distributed System**: Every developer working with Git has a complete copy of the project’s repository, including its full history, on their local machine. This allows them to work independently and offline.
- **Branching and Merging**: Git allows you to create separate branches for different features or bug fixes. These branches can be merged back into the main codebase once the changes are complete and tested.
- **Collaboration**: Git enables multiple developers to collaborate on a project simultaneously without overwriting each other’s changes. Teams can efficiently manage code contributions through repositories.

## Q. Why is Git Used?

1. **Collaboration**: Git makes it easy for multiple developers to work on the same project simultaneously without conflicts. By using branches, each developer can work independently on features, bug fixes, or experiments, and then merge their changes back into the main project.

2. **Version Control**: Git allows you to track every change made to your code. You can view who made what changes, revert to a previous version if something breaks, and compare different versions of your code.

3. **Branching and Experimentation**: With Git, you can create branches for new features or fixes, work on them without affecting the main project, and merge them when ready. This makes experimenting and working on different features in parallel very efficient.

4. **Backup and Security**: Since Git is distributed, every developer has a complete copy of the project on their local machine. Even if the central repository goes down, no data is lost as it can be restored from any developer’s local copy.

5. **Integration with CI/CD Pipelines**: Git integrates with many tools for **continuous integration** (CI) and **continuous deployment** (CD). This allows code changes to be automatically tested, built, and deployed as part of a larger DevOps workflow.

6. **Open Source and Widely Adopted**: Git is free and open-source, making it accessible to anyone. It is also the most popular version control system, widely used in open-source projects and by companies of all sizes.

## Q. How Git Works

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

## Q. What is a git repository?

A **Git repository** is a storage space where **Git** keeps all the files, version history, and configurations of a project. It tracks changes to the files over time, allowing developers to **collaborate**, **manage versions**, and **revert to previous versions** of the project.

### Key Points:
- **Version Control**: A Git repository stores the entire **history** of a project, including all commits, branches, and changes.
- **Local or Remote**: Git repositories can be **local** (on your machine) or **remote** (hosted on services like GitHub, GitLab, etc.).
- **Two Types**: A Git repository can either be **bare** (only version control data, no working files) or a **working directory** (where you can modify and work on files).

## Q. What Does the Command `git config` Do? 

The `git config` command is used to **configure Git settings**. It allows you to set your **username**, **email**, and other preferences for Git's behavior. You can configure these settings either globally (for all repositories on your machine) or locally (for a specific repository).

### Key Use Cases:

### 1. **Global Configuration**:
Global configuration applies to all repositories on your machine. Use the `--global` flag to set options globally.

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

## Q. What is HEAD in Git?

In Git, **HEAD** refers to the **current commit** or **snapshot** that your working directory points to. It represents the **latest commit** in the currently checked-out branch. When you make changes or commits, those changes are added on top of the commit that `HEAD` is pointing to.

### Key Points:

- **HEAD usually points to a branch**: In most cases, `HEAD` points to the latest commit of the branch you are currently working on (e.g., `main` or `develop`).
- **Detached HEAD**: Sometimes, `HEAD` can point directly to a specific commit (e.g., when you check out a past commit or tag). This is known as a **detached HEAD** state.

### Example:

To check where `HEAD` is pointing, you can use the following command:

```bash
git log --oneline -1
```
This will show the latest commit `HEAD` is pointing to.

### Number of Heads in a Repository:
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
 
## Q. What is a Conflict in Git? 

A **conflict** in Git occurs when **two or more changes** are made to the same part of a file in different branches or commits, and Git cannot automatically merge them. Conflicts typically happen during **merge** or **rebase** operations, where changes from different branches or commits need to be combined, but the changes are incompatible.

### Key Points:
- Conflicts occur when **multiple changes** affect the same lines in a file.
- Git marks the conflicting areas and asks you to manually **resolve** the conflict by choosing which changes to keep.
- After resolving the conflict, you need to **stage** the file and **commit** the resolution.

Conflicts need manual intervention to resolve so that Git can successfully complete the merge or rebase process.

## Q. What does git status command do?
- `git status` command is used for showing the difference between the working directory and the index which is helpful for understanding git in-depth and also keep track of the tracked and non-tracked changes.

## Q. Define “Index”.
Before making commits to the changes done, the developer is given provision to format and review the files and make innovations to them. All these are done in the common area which is known as `Index` or `Staging Area`.

## Q. What does git add command do?
- This command adds files and changes to the index of the existing directory.
- You can add all changes at once using `git add .` command.
- You can add files one by one specifically using `git add <file_name>` command.
- You can add contents of a particular folder by using `git add /<folder_name>/` command.

## Q. What is Squash.
In Git, "squash" means combining multiple commits into a single commit. This process helps tidy up commit history by merging the changes of several commits into one, making the history cleaner and easier to understand.

## Q. What has to be run to squash multiple commits (last N) into a single commit?
To squash the last N commits into a single commit in Git, follow these steps:
1. **Run an interactive rebase**: Use the following command, replacing `N` with the number of commits you want to squash:
```bash
git rebase -i HEAD~N
```
2. **Mark commits to squash**: This opens an editor with a list of the last `N` commits. The first commit will be marked as `pick`, and for the rest, change `pick` to `squash` (or s for short). This combines those commits into the first one.
3. **Edit the commit message (optional)**: After squashing, Git will ask you to edit the commit message. You can either keep the original commit messages or rewrite them into a single message.
4. **Finalize the rebase**: Once you save and close the editor, Git will squash the commits into one.
5. **Force-push the changes (if necessary)**: If you're working on a remote branch, you may need to force-push the changes:
```bash
git push --force
```
This will combine the last N commits into a single.

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

## Q. Can you tell something about `git reflog`?
`git reflog` (reference log) is a Git command that tracks and records changes to the `HEAD` and branch references in your repository. It allows you to see a history of all the actions that have moved or updated your `HEAD` pointer, such as commits, checkouts, rebases, resets, or merges.

**Key points about `git reflog`**:
- **Local history**: `git reflog` is stored locally, and it doesn't get pushed to the remote repository. It's useful for recovering lost commits or branches that you might have deleted accidentally.
- **Recovery tool**: If you reset a branch or lose a commit, you can use git reflog to find the commit hash and recover it.
- **Usage**:
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
In Git, a stash is a temporary storage area where you can save your uncommitted changes (both tracked and untracked files) without committing them to the repository. This allows you to clean your working directory and switch to a different task or branch, while keeping your current changes saved for later use.

## Q. What does `git annotate` command do?
The `git annotate` command, also known as `git blame`, shows line-by-line details about who last modified each line in a file, along with the corresponding commit. It's useful for tracking changes and understanding the history of a file.

When you run `git annotate` (or `git blame`), it displays:
1. The commit hash that introduced each line.
2. The author of the change.
3. The timestamp of the change.
4. The actual content of each line.

Example usage:
```bash
git annotate <filename>
```
or

```bash
git blame <filename>
```
This will show you, for each line in the file, who last modified it, in which commit, and when. It's commonly used to trace the history of specific code changes.

## Q. What is the difference between git stash apply vs git stash pop command?
The difference between `git stash apply` and `git stash pop` lies in how they handle the stash after applying the changes:
1. `git stash apply`:
- This command applies the stashed changes to your working directory but keeps the stash intact.
- The stash remains available for future use.
- Use it if you want to apply the changes without removing the stash.
```bash
git stash apply
```
2. `git stash pop`:
- This command applies the stashed changes to your working directory and removes the stash after applying it.
- It's a combination of `git stash apply` and `git stash drop` (which deletes the stash).
- Use it if you want to apply the changes and no longer need to keep the stash.
```bash
git stash pop
```

# Q. Difference between `git pull` and `git fetch`

The difference between `git pull` and `git fetch` lies in how they handle retrieving changes from a remote repository and integrating them into your local repository:

## 1. `git fetch`:
- **Fetches remote changes**: It downloads new commits, branches, and tags from the remote repository **without merging** them into your local branches.
- **Local state remains unchanged**: It only updates the remote-tracking branches (like `origin/main`) but doesn't affect your current working directory or the local branches.
- **Manual merge required**: After fetching, you need to manually merge the fetched changes into your local branch if desired (using `git merge`).
- **Usage**:
  ```bash
  git fetch
  ```
  - **Typical workflow**: Fetching is used when you want to see what changes exist on the remote repository before deciding to integrate them.
## 2. `git pull`:
- **Fetches and merges**: It performs a `git fetch` followed by a merge of the fetched changes into your current local branch.
- **Immediate integration**: After downloading the changes, it automatically attempts to merge the remote branch into your local branch.
- **Potential conflicts**: Since it merges the changes right away, conflicts may arise that you need to resolve during the pull process.
```bash
git pull
```
- **Typical workflow**: Pulling is used when you want to immediately bring your local branch up to date with the remote branch.

### Summary:
- `git fetch`: Only downloads changes; no changes to your local working directory or branch.
- `git pull`: Downloads and merges changes into your current local branch.

