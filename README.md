# Git Branching, Merging, Rebasing, and Pull Requests Guide

## Introduction
Welcome to the Git learning repository! This guide will help you understand how to create branches, merge changes, rebase your commits, and submit pull requests effectively.

## Prerequisites
Before starting, ensure you have Git installed. You can check by running:
```sh
git --version
```
If you don't have Git installed, follow the instructions [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

---
## 1. Branching in Git
Branches allow you to work on new features or fixes without affecting the main codebase.

### **Creating a New Branch**
```sh
git branch feature-branch
```

### **Switching to a Branch**
```sh
git checkout feature-branch
```
*(or in newer Git versions: `git switch feature-branch`)*

### **Creating and Switching in One Command**
```sh
git checkout -b feature-branch
```
*(or: `git switch -c feature-branch`)*

### **Viewing Branches**
```sh
git branch
```

---
## 2. Merging Branches
Once your feature is complete, merge it back into the `main` branch.

### **Merge a Branch into Main**
1. Switch to the main branch:
   ```sh
   git checkout main
   ```
2. Merge the feature branch:
   ```sh
   git merge feature-branch
   ```

### **Handling Merge Conflicts**
If Git detects conflicts, it will prompt you to resolve them manually in the affected files. After resolving conflicts:
```sh
git add <file>
git commit -m "Resolve merge conflict"
```

---
## 3. Rebasing a Branch
Rebasing allows you to integrate changes from one branch into another while keeping a clean commit history.

### **Rebasing a Feature Branch Onto Main**
1. Switch to the feature branch:
   ```sh
   git checkout feature-branch
   ```
2. Rebase onto `main`:
   ```sh
   git rebase main
   ```

### **Handling Rebase Conflicts**
If conflicts occur:
1. Resolve them in the affected files.
2. Continue the rebase:
   ```sh
   git rebase --continue
   ```
3. If you want to cancel the rebase:
   ```sh
   git rebase --abort
   ```

### **Pushing a Rebased Branch**
Since rebase rewrites history, you may need to force push:
```sh
git push --force
```
**Use this carefully! It rewrites history and may cause issues for collaborators.**

---
## 4. Creating a Pull Request (PR)
Pull Requests (PRs) are used to propose and review changes before merging them into the main branch.

### **Steps to Create a Pull Request:**
1. Push your feature branch to the remote repository:
   ```sh
   git push origin feature-branch
   ```
2. Go to your repository on GitHub/GitLab/Bitbucket.
3. Click on the **Pull Requests** tab and select **New Pull Request**.
4. Choose the base branch (`main`) and compare it with your feature branch.
5. Add a title and description for your PR, explaining the changes made.
6. Submit the PR and request reviews from team members.

### **Reviewing and Merging a PR:**
- Team members can review your PR, comment, and suggest changes.
- Once approved, merge the PR via the GitHub UI or using Git:
  ```sh
  git checkout main
  git merge feature-branch
  ```
- After merging, delete the branch:
  ```sh
  git branch -d feature-branch
  git push origin --delete feature-branch
  ```

---
## 5. Deleting Branches
Once your feature is merged, delete the branch to keep your repo clean.

### **Delete a Local Branch**
```sh
git branch -d feature-branch
```

### **Force Delete a Branch (if not merged yet)**
```sh
git branch -D feature-branch
```

### **Delete a Remote Branch**
```sh
git push origin --delete feature-branch
```

---
## 6. Summary of Commands
| Task | Command |
|------|---------|
| Create a branch | `git branch branch-name` |
| Switch branches | `git checkout branch-name` or `git switch branch-name` |
| Merge branch into main | `git checkout main` → `git merge branch-name` |
| Rebase branch onto main | `git checkout branch-name` → `git rebase main` |
| Create a pull request | Push branch → Open PR on GitHub/GitLab/Bitbucket |
| Merge a pull request | Approve and merge via UI or `git merge branch-name` |
| Delete a branch | `git branch -d branch-name` |

Happy coding! 🚀
