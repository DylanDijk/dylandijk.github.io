---
title: Git Commands - Cheat Sheet
date: 2023-01-03 12:10:00 +0000
categories: [Git, Cheat sheet]
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

Another option to create git aliases is to actually make Linux aliases. This can be done by adding them to the `.bashrc` file. The git aliases that I use are given [here](https://dylandijk.github.io/posts/linux-aliases/).  
For example:

```shell
alias gs='git status'
```

 I can now just write `gs` in the linux terminal to run `git status`.

***

## Terminology

- **origin** is an alias  _on your system_ for a **particular remote repository**. It's not actually a property of that repository.
- A **remote repository** in Git, also called a **remote**, is a Git repository that's hosted on the Internet or another network
	- You can see what URL belongs to each remote by using: `git remote -v`
- `HEAD` can be thought of as a pointer where commits are added to.
- You are in a **detached head state** when your `HEAD` is pointing at a commit and not a branch. [This video](https://www.youtube.com/watch?v=GN36mrrM12k) explains it well.

## Common commands
- If there are changes on remote repo you can use `git fetch` command which downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on.
To then merge these changes with your local repo you use `git pull` command.


## Going back

- You have made a commit, but realised its bad and you want to go back to state of previous commit **permanently**.
	- `git revert` will create a commit that you can think of as the inverse of the previous commit. This is useful as it brings you back to the state of the previous commit, whilst retaining the history of the bad commit.
	- `git revert a867b4af`  
	Where the code here is the commit you want to revert.
	You can revert a revert in the same way, by just using the commit code of the revert.
	- `git revert --no-commit` to revert but not commit. Can then do `git commit -m " "`.
	- Can revert multiple commits see [here](https://stackoverflow.com/questions/1463340/how-can-i-revert-multiple-git-commits/1470452#1470452).
	- To get commit codes can use `git log .` to view all commits.  
	`git log --pretty=oneline` to view all commits in one line.

***

- You want to **view** the state of previous commit but not to go back to it permanently.
	- `git checkout a867b4af`  
	Where the code here is the commit you want to view.

***

- You have added a file to the staging area with `git add`, but now want to remove it from the staging area.
	- `git restore --staged <filename>` will remove the file from the staging area. 

## Branches
- list local branches `git branch`
- list remote branches with `git branch -r`
- create a new branch `git checkout -b your_new_branch`
	- if you want to push the branch to github, use the command `git push -u origin your_new_branch`
- Can create new branch then go back to original branch and then revert changes look [here](https://stackoverflow.com/questions/2816715/branch-from-a-previous-commit-using-git/31783383#31783383) but use git revert instead of `git reset`.
- `git branch -vv` to view all tracking branches
- After merging a branch you may want to delete it, you can do this with  `git branch -d <Branch Name>`. This deletes the local branch.
- To delete a remote branch you can run `git push <remote_name> --delete <branch_name>`


## Merge
- if you want to merge branch 2 into branch 1, first make sure you are in branch 1 do this by using the command `git switch branch 1`. Then `git merge branch 2` .
- If there are conflicts I recommend opening the folder in **VScode**, so that you can visualise the conflicts.
	- After deciding on changes you just do the usual git add, git commit
	- If you just wanted to cancel the git merge, then run `git merge --abort`.
- If there are conflicts with binary files, then can no longer fix with VScode. To keep changes of the branch that you are merging into, in this case the changes in branch 1, then run `git checkout --ours <filename>`. To keep changes of the branch that you are merging from, branch 2, then run `git checkout --theirs <filename>`. Then add and commit changes.

## Tags 

- When releasing software it is useful to label a specific commit that is an important milestone in the project. For example, you may want to tag the commit that is the first release of the software to the public. 
- To view all tags `git tag`
- View tags and their descriptions `git tag -n`
- View detailed information regarding a specific tag `git show <tagname>`
- To create a tag for a specific commit you run `git tag -a v1.0.0 74202f7 -m "message here"`. Where `v1.0.0` is the tag name, `74202f7` is the commit code and `-m` is the message.  
Use `git log --pretty=oneline` to view the commit codes.
- To push the tag to the remote repo you run `git push origin v1.0.0`. Where `v1.0.0` is the tag name.
- You can then use the tags to publish new releases on the GitHub repo.
- Can checkout a tag, for example `git checkout v1.0.1`.
	- Afterwards to return to an undetached HEAD state run `git checkout main` or `git checkout master`.




## Ignoring
- File change keeps appearing in git status even though it has been added to `.gitignore`
	- This is because the file has already been tracked by git. To stop tracking the file you need to run `git rm --cached <file>`. Then commit the changes.
- You want git to ignore certain files, but want to avoid using the `.gitignore` file.  
For example, if you have forked a repo and made personal notes that you do not want to be included in a pull request, and you also do not want a modified `.gitignore` file to appear in the pull request.  
A solution is to list the files in the `.git/info/exclude` file within your local repo.


## Useful Things

- Renaming a file on local Git Repo
[Instruction on GitHub](https://docs.github.com/en/repositories/working-with-files/managing-files/renaming-a-file#renaming-a-file-using-the-command-line)
  - use `git mv OLD-FILENAME NEW-FILENAME`
  - can also use this to move file to new folder
  - then commit changes

- If you want to add all files apart from one file then can use the following: `git add --all -- ':!<filename>'` For example: `git add --all -- ':!R/get_create_features.R'`
- You may have made changes that have not been committed, and then want to view exactly what these changes are. Running `git diff` shows which files have changes and which lines have been changed.
	- You may see that some lines have been removed and added these are probably due to changes in spaces, to run git diff without taking into account white space you can run `git diff -w`.
- You have made local changes that you realise are "bad" and you do not want to commit them
  - Running `git reset --hard` will delete these changes and you will be in the state of your last commit. But note that all of that work will be deleted.
  - Not specifying a commit will reset to the commit pointed to by `HEAD`.


- The `git checkout` command lets you navigate between the branches created by `git branch`. Checking out a branch updates the files in the working directory to match the version stored in that branch, and it tells Git to record all new commits on that branch. Think of it as a way to select which line of development you’re working on.

- you have made uncommited changes on your main branch, and you realised that this work should be on another branch:
	- whilst on main branch use `git stash`
	- switch to new branch `git checkout -b new-branch-name`
	- move the uncommited changes to this new branch `git stash pop`



