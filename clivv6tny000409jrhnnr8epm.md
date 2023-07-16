---
title: "About Git and Git-Hub"
datePublished: Wed Jun 14 2023 15:26:05 GMT+0000 (Coordinated Universal Time)
cuid: clivv6tny000409jrhnnr8epm
slug: about-git-and-git-hub
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686756076529/8d4fbea4-e169-42d5-9c24-44867ab0a5ff.png
tags: artificial-intelligence, cloud, aws, github, git

---

# **What is Git?**

Git is a version control system that means a way to track all the new changes that are being done in the project which is been placed in the central repository.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*6QepBYu3NwhEcQPY3Egp6A.png align="center")

# **Workflow of Git**

While working with Git on Linux distributions like **CentOS, Debian, Fedora, Ubuntu, Amazon Linux**…etc. We have to follow command modules such as **apt, apt-get, and yum** according to the particular flavours of Linux.

Here we will be having a look at commands used in the CentOS flavour of Linux i.e. yum module:

Below we will check commands used.

1. A command used to install Git
    
    \*#\****yum install git***
    
2. A command used to initialize a project
    
    **#git init**
    
3. A command used to check the version of Git
    
    **#git -version**
    
4. A command used to create a file
    
    **#mkdir &lt;filename&gt;**
    
5. A command used to add a file to the staging area
    
    **#gitadd &lt;filename&gt;**
    
6. A command used to commit a file to the local repo
    
    **#git commit -m “&lt;your\_msg&gt;”**
    
7. A command used to add and commit a file to the local repo
    
    **#git commit -am &lt;filename&gt;**
    
8. A command used to check the log of commits
    
    **#git log**
    
9. A command used to check log in one line
    
    **#git log-oneline**
    
10. A command used to move all files into the staging area
    
    **#git add**
    

# **Staging area**

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*h4gTZ2aPPkhYe8bs3FlDEw.png align="center")

Staging area is files that are going to be a part of the next commit, which lets git know what changes in the file are going to occur for the next commit.

# **Branching**

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*-tY7VTEC3B9CCY7r7fn12Q.png align="center")

Branching allows you to duplicate the source code for yourself. You will then work on your own branch so your edits do not immediately affect the original source code.

# **Merging**

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*jDO0ADqu_fbvm4DPRSoG4Q.png align="center")

The process of joining your branch with the original source code after complete testing.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*T_5r30TttAVCb4qLMxa0lA.png align="center")

# **User-Configuration**

**#git config** [**user.name**](http://user.name) **”&lt;name&gt;”**

**#git config** [**user.email**](http://user.email) **”&lt;mail&gt;”**

# **For Global Configuration**

**#git config — global** [**user.name**](http://user.name) **”&lt;name&gt;”**

**#git config — global** [**user.email**](http://user.email) **”&lt;email&gt;”**

# **Branching Commands**

**To list the branches**

#git branch

**To create a branch**

#git branch &lt;branch name&gt;

**To switch to another branch**

#git checkout &lt;switching branch name&gt;

**To merge branch to master**

#git merge &lt;branch name&gt;

# **Conflict Merge, Rebase, Cherry-Pick Commands**

**\_To compare future branches with existing branches**

#git config — global merge.tool vimdiff

#git config — global merge.conflictstyle diff3

#git config — global mergetool.prompt false

#git mergetool

**\_To Rebase**

#git rebase master

**\_To Pick a specific commit of file**

#git cherry-pick &lt;id&gt;

**\_To remove a file**

#rm &lt;filename&gt;

# **What is Git-Hub?**

GitHub is a cloud-based Git repository hosting service,similar to Dropbox or Google Drive.

It lets individuals and teams host their projects, work together on projects. GitHub works with Git to add more functionality. For example, store these Git repositories on their servers.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*6QepBYu3NwhEcQPY3Egp6A.png align="center")

**GitHub essentials are:**

* Repositories
    
* Branches
    
* Commits
    
* Pull Requests
    

# **\_Commands used to communicate git with GitHub**

**\_To connect the remote repo to the local repo**

#git remote add &lt;repo name&gt;&lt;repo link from github&gt;

**\_To push code from local repo to remote repo**

#git push &lt;repo name&gt; &lt;master repo&gt; or

#git push -u origin master

**origin -&gt; remote repo name**

**master -&gt; local repo**

**\_To pull from the remote repo**

#git pull origin master

**\_To copy code as a local file**

#git clone &lt;repo link&gt;

**\_To hold a file in the staging area before committing to the local repo**

#git stash

**\_To revert the changes**

#git revert

**\_To revert a particular commit**

#git revert &lt;commit&gt;