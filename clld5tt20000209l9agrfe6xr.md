---
title: "Day:11 Advance Git & GitHub for DevOps Engineers: Part 2 🍎🍏🍎"
datePublished: Wed Aug 16 2023 03:15:24 GMT+0000 (Coordinated Universal Time)
cuid: clld5tt20000209l9agrfe6xr
slug: day11-advance-git-github-for-devops-engineers-part-2
tags: github, git, 90daysofdevops, wemakedevs, tws

---

Welcome back to the second part of our series on "Advance Git & GitHub for DevOps Engineers." The previous article explored branching, merging, and rebasing techniques. Today, we'll dive deeper into some more advanced Git features that are crucial for DevOps engineers: Git Stash, Cherry-Pick, and Conflict Resolution. 🚀🔥

## **Git Stash: A Handy Tool for Temporary Changes 🛠️**

As a DevOps engineer, you often find yourself juggling between different tasks and branches. Git stash comes to your rescue when you need to set aside your current changes without committing them. This is particularly useful when you're in the middle of something but need to switch gears temporarily.

Here's how you can use Git stash:

1. **Create a New Branch and Make Changes:** Begin by creating and making changes to a new branch.
    
2. **Stash Your Changes:** When you need to switch to a different branch before committing your changes, use the command `git stash`. This action will stash away your changes and revert your working directory to the last commit.
    
3. **Switch and Commit:** Move to the desired branch, make changes, and commit them as needed.
    
4. **Apply Stashed Changes:** To apply your stashed changes, use `git stash pop`. This will reapply the stashed changes on top of your new commits. 🎉
    

Remember, you can list your stashes using `git stash list`, delete a stash with `git stash drop`, or clear all stashes using `git stash clear`. 🗑️

## **Selective Changes with Git Cherry-Pick 🍒**

Sometimes, you might need to apply specific commits from one branch to another selectively. Git cherry-pick comes in handy for this precise task.

Here's how you can use Git cherry-pick:

1. **Create Two New Branches:** Start by creating two new branches and making commits to them.
    
2. **Cherry-Pick Commits:** If you want to apply certain commits from one branch to another, use `git cherry-pick <commit_hash>`. This will copy the selected commit(s) onto the target branch. 🌟
    

## **Mastering Conflict Resolution 🛡️**

Conflicts are inevitable when merging or rebasing branches that have diverged. As a DevOps engineer, you need to be skilled in resolving these conflicts effectively.

Here's a brief guide to conflict resolution:

1. **Check Status:** Use `git status` to identify files with conflicts.
    
2. **Analyze Differences:** Utilize `git diff` to understand the conflicting changes.
    
3. **Resolve Conflicts:** Open the conflicted files, locate the conflicting sections, and manually resolve the differences. Edit the files to keep the desired changes.
    
4. **Mark Resolved Files:** After resolving conflicts, use `git add` to mark the resolved files as ready for the next step. ✅
    

With these advanced Git techniques under your belt, let's move on to some practical tasks to solidify your understanding.

### **Task-01: Stash and Apply Changes 📦**

1. Create a new branch and make some changes.
    
2. Stash these changes using `git stash`.
    
3. Switch to a different branch, make changes, and commit them.
    
4. Apply the stashed changes using `git stash pop`. 🔄
    

### **Task-02: Syncing Commit Messages with Rebase 🔄**

1. Edit `version01.txt` in the development branch, adding the specified lines and making corresponding commits.
    
2. Ensure the commit messages are reflected in the Production branch using rebase.
    

### **Task-03: Cherry-Pick and Optimize 🍒**

1. Cherry-pick the commit "Added feature2.2 in development branch" into the Production branch.
    
2. Add the specified lines to the commit message as instructed, emphasizing optimization. 🚀