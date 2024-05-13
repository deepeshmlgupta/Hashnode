---
title: "Git Commands"
datePublished: Mon May 13 2024 18:00:45 GMT+0000 (Coordinated Universal Time)
cuid: clw59s8qp000k09lc5bv30vfn
slug: git-commands
tags: git, devops, git-commands, deepeshmlgupta

---

### **What Git is?**

Git is an open-source version control system that works locally to help developers work together on software projects that matter.

### Initializing

Starting up Git within a project and getting it connected.

1. Initializes (or starts) your current working directory (folder) as a Git repository (repo).
    
    ```plaintext
    git init
    ```
    
2. Copies an existing Git repo hosted remotely.
    
    ```plaintext
    git clone https://www.github.com/username/repo-name
    ```
    
3. Shows your current Git directory’s remote repo. Use the **\-v flag** for more info.
    
    ```plaintext
    git remote or git remote -v
    ```
    
4. Adds the Git upstream to a URL
    
    ```plaintext
    git remote add upstream https://www.github.com/username/repo-name
    ```
    

### Branching

**Means:** Isolating work and managing feature development in one place.

1. Lists all current branches. An asterisk (**\***) will appear next to your currently active branch.
    
    ```plaintext
    git branch
    ```
    
2. Creates a new branch. You will remain on your currently active branch until you switch to the new one.
    
    ```plaintext
    git branch new-branch
    ```
    
3. Switch to any existing branch and checks it out into your current working directory.
    
    ```plaintext
    git checkout another-branch
    ```
    
4. Consolidates the creation and checkout of a new branch.
    
    ```plaintext
    git checkout -b new-branch
    ```
    
5. Deletes a branch.
    
    ```plaintext
    git branch -d branch-name
    ```
    

### Staging

**Means:** Creating files staged after modifying a file and marking it ready to go in the next commit.

1. Checks the status of your Git repo, including files added that are not staged.
    
    ```plaintext
    git status
    ```
    
2. Stages modified files. If you make changes that you want to be included in the next commit, you can run add again. Use `git add .` for all files to be staged, or specify specific files by name.
    
    ```plaintext
    git add .
    ```
    
    or
    
    ```plaintext
    add my_script.js
    ```
    
3. Removes a file from staging while retaining changes within your working directory
    
    ```plaintext
    git reset my_script.js
    ```
    

### Committing

**Means:** Recording changes made to the repo.

1. Commits staged files with a meaningful commit message so that you and others can track commits.
    
    ```plaintext
    git commit -am "Commit message
    ```
    
2. Condenses all tracked files by committing them in one step.
    
    ```plaintext
    git commit -m "Commit message
    ```
    
3. Modifies your commit message.
    
    ```plaintext
    git commit --amend -m New commit message
    ```
    

### Collaborating and Sharing

**Means:** Downloading changes from another repository or sharing changes with the larger codebase.

1. Pushes or sends your local branch commits to the remote repo.   Note: some repos use master instead of main in their commands.
    
    ```plaintext
    git push origin main
    ```
    
2. Fetches and merges any commits from the tracking remote branch.
    
    ```plaintext
    git pull
    ```
    
3. Merges the fetched commits.
    
    ```plaintext
    git merge upstream/main
    ```
    

### Showing Changes

**Means:** See changes between commits, branches, and more.

1. Compares modified files that are in the staging area.
    
    ```plaintext
    git diff --staged
    ```
    
2. Displays the difference between what is in a-branch but is not in b-branch.
    
    ```plaintext
    git diff a-branch..b-branch
    ```
    
3. Uses commit id to show the diff between two specific commits.
    
    ```plaintext
    git diff 61ce3e6..e221d9c
    ```