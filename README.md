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
#### Add a file
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
