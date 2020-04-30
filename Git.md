# ==================  git bash  ==================  
Detail:  
https://website-proxy.backlogtool.com/git-tutorial/tw/reference/

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

- Add code to **staged** prepare for commit
```
git add file_path
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