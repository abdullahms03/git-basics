### Three state architecture of git
- Working directory
- Staging area
- Commit state (commit history) 

### Initialize a repository  

```bash
git init
```
This creates an empty repository with .git directory 

### Check the current status of the repository  
This displays the list of files added/modified
```bash
git status
```

### Adding/Staging the changes to commit
*staging changes, not files*  

after adding/staging the changes, if there are any more changes to the same file, it still remains untracked unless added(staged) again
#### Add a file
*means add the change in the file at that time*
```bash
git add <file>
```
#### Add multiple files
```bash
git add <file1> <file2>

OR

git add .
```

### Commit the changes

```bash
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
