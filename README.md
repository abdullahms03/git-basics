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

