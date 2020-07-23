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