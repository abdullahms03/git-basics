### Three state architecture of git
- Working directory
- Staging area
- Commit state (commit history) 

### Initialize a repository  
This creates an empty repository with .git directory 
```bash
git init
```

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
```
