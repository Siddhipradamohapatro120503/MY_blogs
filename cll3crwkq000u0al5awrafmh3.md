---
title: "Day 10 : Advance Git & GitHub for DevOps Engineers"
datePublished: Wed Aug 09 2023 06:32:10 GMT+0000 (Coordinated Universal Time)
cuid: cll3crwkq000u0al5awrafmh3
slug: day-10-advance-git-github-for-devops-engineers
tags: github, advanced, 90daysofdevops, wemakedevs, tws

---

Welcome back, DevOps enthusiasts! In today's blog, we are diving deep into the world of Git and GitHub, specifically focusing on advanced concepts that are essential for DevOps engineers. Our main highlights for today's task include Git branching, Git revert and reset, and Git rebase and merge. So, let's jump right in and explore these concepts step by step.

## **Git Branching: Isolating Development Work**

Branching is a fundamental concept in Git that allows developers to work on separate features, bug fixes, or experiments in a contained environment without affecting the main codebase. Each repository has a default branch (usually called `master` or `main`) and can have multiple other branches created from it. One of the key benefits of branching is the ability to merge changes from one branch into another using pull requests.

To demonstrate this, let's walk through Task 1:

### **Task 1: Working with Branches and Commits**

1. **Creating a New Branch:** Start by adding a text file called `version01.txt` inside the `Devops/Git/` directory. This file will contain the text "This is the first feature of our application." To create a new branch from `master`, use the command:
    
    ```bash
    git checkout -b dev
    ```
    
2. **Committing Changes:** Switch to the `dev` branch and commit your changes with a relevant message:
    
    ```bash
    git checkout dev
    git add Devops/Git/version01.txt
    git commit -m "Added new feature"
    ```
    
3. **Pushing Changes:** Push your local changes to the remote repository for review:
    
    ```bash
    git push origin dev
    ```
    
4. **Adding More Commits:** Next, add more content to the `version01.txt` file and commit these changes:
    
    ```bash
    # Add content to version01.txt as instructed
    git add Devops/Git/version01.txt
    git commit -m "Added feature2 in development branch"
    git commit -am "Added feature3 in development branch"
    git commit -am "Added feature4 in development branch"
    ```
    
5. **Restoring to Previous Version:** To revert the file to a previous version, you can use `git reset` or `git revert` based on your preference and knowledge. Let's say you want to use `git reset`:
    
    ```bash
    git log  # Find the commit hash of the version you want to revert to
    git reset <commit_hash> Devops/Git/version01.txt
    ```
    

### **Task 2: Branches and Merging**

Now, let's explore the concept of branches further by working with multiple branches and merging them:

1. **Creating Additional Branches:** Create two or more branches from the `dev` branch:
    
    ```bash
    git checkout -b feature1 dev
    git checkout -b feature2 dev
    ```
    
2. **Making Changes and Merging:** Add some changes to the `feature1` branch and merge it into the `master` branch:
    
    ```bash
    git checkout feature1
    # Make changes to files
    git commit -am "Made changes in feature1 branch"
    git checkout master
    git merge feature1
    ```
    
3. **Exploring Git Rebase:** Experiment with `git rebase` to understand its differences compared to regular merging. Start by creating a new branch and adding changes, then try rebasing it onto the `master` branch:
    
    ```bash
    bashCopy codegit checkout -b feature3 dev
    # Make changes to files
    git commit -am "Made changes in feature3 branch"
    git checkout master
    git rebase feature3
    ```
    

## **Conclusion**

Congratulations, you've successfully tackled advanced Git concepts for DevOps engineers! In this blog, we delved into Git branching, demonstrated the use of `git revert` and `git reset` to manage code changes, and explored the differences between `git rebase` and `git merge`. These skills are crucial for efficient collaboration and version control in a DevOps environment.

Remember, mastering Git and GitHub is a continuous journey. By understanding these advanced techniques, you're better equipped to handle complex development scenarios and contribute effectively to your team's projects.

Stay tuned for more DevOps adventures and keep honing your skills. Happy coding and branching! 🚀🌿