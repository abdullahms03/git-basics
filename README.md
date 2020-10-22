# Git Basics

<!--TOC-->
+ [Three state architecture](#Three-state-architecture-of-git)
+ [Local Repo](#Local-Repo)   
    - [Initialize a repo](#Initialize-a-repository)
    - [Check the current status](#Check-the-current-status-of-the-repository)
    - [Adding/Staging the changes to commit](#Adding/Staging-the-changes-to-commit)
        * [Add a file](#Add-a-file)
        * [Add multiple files](#Add-multiple-files)
    - [Commit the changes](#Commit-the-changes)
    - [View the commits](#View-the-commits)
    - [Git checkout](#Git-checkout)
        * [With file name](#With-file-name)
        * [Multiple files](#Multiple-files)
        * [Checkout a branch](#Checkout-a-branch)
        * [Switch to a older commit](Switch-to-a-older-commit)
    - [Git restore](#Git-restore)
    - [Git amend](#Git-amend)
    - [Git diff](#Git-diff)
    - [Git ignore](#Git-ignore)
    - [Git branch](#Git-branch)
    - [Git merge](#Git-merge)
        * [Fast-forward merge](#Fast-forward-merge)
        * [Recursive merge](#Recursive-merge)
        * [Merge conflicts](#Merge-conflicts)
    - [Delete branch](#Delete-branch)
    - [Git rebase](#Git-rebase)
+ [Remote Repository](#Remote-Repository)
    - [Clone a remote repository](#Clone-a-remote-repository)
    - [Git push](#Git-push)
    - [Git pull](Git-pull)
    - [Link between local and remote](#Link-between-local-and-remote)
    - [Git fetch](#Git-fetch)
+ [GitHub](#GitHub)
    - [Add existing repo to GitHub](#Add-existing-repo-to-GitHub)
    - [Update remote Url](#Update-remote-Url)
    - [Check remote repo](#Check-remote-repo)
    - [Fork](#Fork)
    - [Pull request](#Pull-request)


<!--TOC-->
## Local Repo
### Three state architecture of git
- Working directory
- Staging area
- Commit state (commit history)

### Initialize a repository  

```
git init
```
This creates an empty repository with .git directory 

### Check the current status of the repository  
This displays the list of files added/modified
```
git status
```

### Adding/Staging the changes to commit
*staging changes, not files*  

after adding/staging the changes, if there are any more changes to the same file, it still remains untracked unless added(staged) again
#### Add a file
*means add the change in the file at that time*
```
git add <file>
```
#### Add multiple files
```
git add <file1> <file2>

OR

git add .
```

### Commit the changes

```
git commit -m "<commit message>"

OR

git commit
```
git commit will open the editor to add commit message, it can be too long, can be mutiple lines

Stage(add) the files and commit
```
git commit -a -m "<commit message>"
```

a commit has
- the snapshot of the changes
- metadata(eg., user details) and
- link to the previous commit

commit hash is the unique id generated with the combination of the above commit contents

### View the commits
```
git log
```
mutiple options available to filter the commits - by name, by status, by count etc...
```
git log -2 
git log n -3
git log --author "<author>"
git log --name-only
git log --name-status
```
to view the changes in the commits
```
git log -p
```
To view the commits with a graphical illustration across branches
```
git log --graph
```

### Git checkout

Update the working directory with some other state
(branch or file or commit)

eg., checkout the state of change from last commit
#### With file name
```
git checkout -- <file>
```
#### Multiple files
```
git checkout -- .
```
#### Checkout a branch
```
git checkout <branchname>
```
Create a new branch and checkout
```
git checkout -b <branchname>
```
#### Switch to a older commit
```
git checkout <commitId>
```
This is moving the HEAD to point to the older commit, this Will result in detatched HEAD state.\
The current branch will still point to the latest commit, it will not be impacted.

New branch can be created from the older commit and checked out to proceed with further changes on it. This will drop the detatched HEAD state.

### Git restore

To unstage a file 
```
git restore --staged <file>
```
Also to restore to the previous commit's state(similar to git checkout)
```
git restore <file>
```

### Git amend
To update the last commit with additional changes.\
Stage the recent change. then, 
```
git commit --amend 
```
To update only the commit message,\
just run the above command and update the message, without staging any additional changes

### Git diff
To view the difference on what changed in the local directory
```
git diff
```
To view the diff after staging
```
git diff --staged
```

### Git ignore
To ignore specific files or directories\
Add .gitignore file to the root directory and add the file name that needs to be ignored\
File extension, directory, wildcard can be used herer

### Git branch
To view the current branch
```
git branch
```
To create a new branch
```
git branch <branchname>
```
This will create a new branch (with the name specified) from the latest commit of current branch

**Current branch always points to the latest commit**

**HEAD always points to the latest commit of current checked-out branch**

### Git merge
To merge branches
```
git merge <branchname>
```
#### Fast-forward merge
If the branch from which the new branch is created doesn't have any further changes after the new branch creation, it is just some commits behind the new branch.\
Moving the pointer of current branch to the latest commit of branch(new branch) which is ahead

#### Recursive merge
If the branch from which new branch is created has some additional changes post new branch creation, then it would undergo recursive merge.

#### Merge conflicts
If there are any changes to the same piece of code in both the current branch and the branch to be merged, auto-merging will fail. Details of the conflicts will be displayed in the files with HEAD and incoming changes.
User has to manually fix the conflicts and commit the changes.

### Delete branch
```
git branch -d <branchname>
```
can not delete a branch which is currently checked out, as HEAD is pointing to the latest commit of that branch

### Git rebase
To avoid merge commits.
The new branch which was created and changes are made can be rebased with the parent branch, so that if there are any new changes to the parent branch that gets applied to the new branch. 
The parent branch still points to it's latest commit.
```
git rebase <parentbranch>
```
rebase command to be run from the branch which needs to be merged to parent branch.\
Once rebase is successfully completed, switch to parent branch and run merge command, it now works as a fast-forward merge.\
**No merge commits introduced in this case.**

## Remote Repository

Git remote repository will have a .git url\
*e.g. https://github.com/abdullahms03/git-basics.git*

### Clone a remote repository
To get the repository to the local directory
```
git clone <githubrepourl>
```
This will create replica of master branch and also to establish the link, it creates\
*origin/master\
origin/{branch1}\
origin/{branch2}*

If origin/master is checked out, it will be detatched HEAD state as, local HEAD is pointing to a remote branch and there is no local branch.
To resolve, create a local branch HEAD will not point to the commit in the local branch

### Git push 
push the local changes to remote repo
```
git push
```

### Git pull
To get the remote changes to local
```
git pull
```
This will fetch all the changes to remote reference first and merge it to the local branch from which the operation is performed.

```
git pull --rebase
```
fetch the changes from remote, apply to local branch, even if the local is ahead of the remote, merge commit will not happen. Both will be considered as separate commits. (rebase concept applied along with pull)

### Link between local and remote
The link is the pointer to remote,\
to identify the remote pointer
```
git remote
```
This would give the remote name, default name is *origin*. This can be changed as required.

To view remote branches
```
git branch -a
```
remote branches will be displayed in the below format\
*remotes/origin/{branchname}*
These are clones of the remote repo

To view any new branches created after cloning the repo. This will show all the branches, but not update the local repo with the new branch
```
git remote show origin
```

### Git fetch
To get all the new branches and commits to local. Updates the remote references of all the remote branches in the local copy.\
*Will not harm the local branches*
```
git fetch
```
The actual local branch will not be impacted with git fetch.\
To get the changes to the local branch itself, merge the changes in the remote reference branch to the local branch
```
git merge origin/{branchname}
```
The above can be same branch of different branch.\
If same branch, then the process is completed.\
If merge it from a different branch, then the local branch will now be ahead of the actual remote reference. So, additional push is required here to sync the branch to remote.

***git pull does both in a single step***
## GitHub
### Add existing repo to GitHub
Create a repository in GitHub
```
git remote add origin <githubrepourl>

git push -u origin master
```
### Update remote Url
```
git remote set-url origin <githubrepourl>
```
### Check remote repo
```
git remote -v
```

### Fork
For a repository is getting own copy of any repository in GitHub.

### Pull request
Make any changes to the forked repository and raise a pull request to get it merged to the original repo.
