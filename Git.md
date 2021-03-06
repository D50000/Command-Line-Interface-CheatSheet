# ===============  git bash  ===============  
Detail:  
https://git-scm.com/docs

- Clone the source
```
git clone <url>
```

- Pull the source down and replace the local source **(pull = fetch + merge)**
```
git pull <repository> <refspec>
```

- Simple load the remote source down
```
git fetch <repository> <refspec>
```

- Merge <branch> to <master>
```
git merge <branch>
```

- Update the local code and rebase the comparing point to the latest version
```
git pull --rebase
```

- Check and compare the local / remote source
```
git status
```

- Remove untracked files from the working tree. (ex: -dfx = directory, file, .gitignore config)
```
git clean -dfx
```

- Add code to **staged** prepare for commit
```
git add file_path
```

- Remove code from **staged**
```
git reset HEAD -- [path]/[to]/[file]
```

- git commit the change
```
git commit
```

- Fix the previous commit comment
```
git commit --amend
```

- Check the commit log
```
git log
```

- Push the commit to remote
```
git push <repository> <refspec>
```

- Revert all change back to last commit
```
git reset HEAD^
```

- Save current status
```
git stash save
```

- List the current **stash** data
```
git stash list
```

- Restore the **stash**
```
git stash pop
```