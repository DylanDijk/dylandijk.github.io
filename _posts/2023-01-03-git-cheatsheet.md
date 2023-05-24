---
title: Git Commands - Cheat Sheet
date: 2023-01-03 12:10:00 +0000
categories: [Cheat sheet, Git]
tags: [Git, GitHub, Cheat sheet]     # TAG names should always be lowercase
---

# Git


## Setting up
- [**Already have local directory**](https://kbroman.org/github_tutorial/pages/init.html) and want to create remote GitHub repository
	- If you have a local directory you need to run `git init` to create a git repository.
	- Then you can link this with a remote repo.
- Want to clone repo form GitHub onto local machine:
	- [Linux](https://m.youtube.com/watch?v=4u6qzxj37h4&list=LL&index=4): `git clone <https key>`
- Switching from a `<https key>` to `<SSH key>` [documentation](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#switching-remote-urls-from-https-to-ssh)

### Setting up [git aliases](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

Run `git config --global alias.aa 'add -A'`, This makes the following two commands equivalent:

```terminal
$ git aa
$ git add -A
```

The git aliases are stored in the `.gitconfig` file, usually in your home folder.

Another option to create git aliases is to actually make Linux aliases. This can be done by adding them to the `.bashrc` file. For example:

```shell
alias gs='git status'
```

 I can now just write `gs` in the linux terminal to run `git status`.

***
- **origin** is an alias  _on your system_ for a **particular remote repository**. It's not actually a property of that repository.
- A **remote repository** in Git, also called a **remote**, is a Git repository that's hosted on the Internet or another network
- You can see what URL belongs to each remote by using: `git remote -v`



- If there are changes on remote repo you can use `git fetch` command which downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on.
To then merge these changes with your local repo you use `git pull` command.

***
- `git restore --staged <file>`to remove files from staging area
- `git restore --staged .` for all files in staging area

***
- The `git checkout` command lets you navigate between the branches created by `git branch`. Checking out a branch updates the files in the working directory to match the version stored in that branch, and it tells Git to record all new commits on that branch. Think of it as a way to select which line of development you’re working on.

- `HEAD` can be thought of as a pointer where commits are added to.

- You are in a detached head state when your `HEAD` is pointing at a commit and not a branch. [This video](https://www.youtube.com/watch?v=GN36mrrM12k) explains it well.
***
### Renaming a file on local Git Repo
[Instruction on GitHub](https://docs.github.com/en/repositories/working-with-files/managing-files/renaming-a-file#renaming-a-file-using-the-command-line)
- use `git mv OLD-FILENAME NEW-FILENAME`
- can also use this to move file to new folder
- then commit changes



## Going back to previous commit
- `git revert a867b4af` Where the code here is the commit you want to revert.
With Git, revert has a very specific meaning: create a commit with the reverse patch to cancel it out. This way you don't rewrite any history.
You can revert a revert in the same way, by just using the commit code of the revert.
- `git revert --no-commit` to revert but not commit. Can then do `git commit -m " "`.
- Can revert multiple commits see [here](https://stackoverflow.com/questions/1463340/how-can-i-revert-multiple-git-commits/1470452#1470452).
- To get commit codes can use `git log .` to view all commits.

## Branches
- list local branches `git branch`
- list remote branches with `git branch -r`
-  create a new branch `git checkout -b your_new_branch`
- Can create new branch then go back to original branch and then revert changes look [here](https://stackoverflow.com/questions/2816715/branch-from-a-previous-commit-using-git/31783383#31783383) but use git revert instead of `git reset`.
- `git branch -vv` to view all tracking branches
- After merging a branch you may want to delete it, you can do this with  `git branch -d <Branch Name>`. This deletes the local branch.
- To delete a remote branch you can run `git push <remote_name> --delete <branch_name>`

## Merge
- if you want to merge branch 2 into branch 1, first make sure you are in branch 1 do this by using the command `git switch branch 1`. Then `git merge branch 2` .
- If there are conflicts I recommend opening the folder in **VScode**, so that you can visualise the conflicts.
	- After deciding on changes you just do the usual git add, git commit
	- If you just wanted to cancel the git merge, then run `git merge --abort`.

## Useful Things
- If you want to add all files apart from one file then can use the following: `git add --all -- ':!<filename>'` For example: `git add --all -- ':!R/get_create_features.R'`
- You may have made changes that have not been committed, and then want to view exactly what these changes are. Running `git diff` shows which files have changes and which lines have been changed.
	- You may see that some lines have been removed and added these are probably due to changes in spaces, to run git diff without taking into account white space you can run `git diff -w`.
- You have made local changes that you realise are "bad" and you do not want to commit them
  - Running `git reset --hard` will delete these changes and you will be in the state of your last commit. But note that all of that work will be deleted.
  - Not specifying a commit will reset to the commit pointed to by `HEAD`.