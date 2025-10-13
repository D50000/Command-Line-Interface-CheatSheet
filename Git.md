# ===============  git cli  ===============  
Detail:  
https://git-scm.com/docs

- Clone the source
```
git clone <url> // Generic clone.
git clone https://$userAccount@github.com/xxxxxx/xxxxxxx.git  // Use $userAccount to clone the git file.
git clone --mirror https://github.com/D50000/xxxxxxx.git // Fully clone with detail repository, branches, tags, reference. 
```

- Pull the source down and replace the local source **(pull = fetch + merge)**
```
git pull <repository> <refspec>
```

- Simple load the remote source down
```
git fetch <repository> <refspec>
```

- Merge 'newBranch' to 'master'
```
// git Checkout and switch to master branch
git merge newBranch
```

- Cancel the in progress merge task.
```
git merge --abort
```

- Switch to others branch 'branch01' or 'commitId'
```
git checkout branch01
git checkout 8955e93
```

- Create new branches
```
# Create and switch to new branch 'new_b'
git checkout -b new_b
# Just create new branch 'rescue-before-undo'
git branch rescue-before-undo
```

- Rename the branch name
```
git branch -m newBranchName
```

- Delete the branch 'branch_remove'
```
git branch -d branch_remove
```

- Show the branches
```
# With commits detail.
git show-branch
# Simple branches.
git branch
```

- List out tags
```
# List all tags
git tag
# Search for "v1.8.5*" prefix
git tag -l "v1.8.5*"
```

- Create tags
```
# Add light-weight tag (simple tag attache on commit)
git tag v1.4
# Add normal tag (additional annotation)
git tag -a v1.4
# Add normal tag with comment
git tag -a v1.4 -m "my_version 1.4"
# Add tag on history commit
git tag -a v1.4 9fceb02
```

- Show tag info (date, author, comment)
```
# Show v1.4 tag info
git show v1.4
```

- Push the tag to remote server
```
# Push single tag
git push origin [tag_name]
# Push all local tags
git push origin --tags
```

- Delete tags
```
git tag -d [tag1] [tag2]
git push --delete origin [tag1] [tag2]
```

- Update the local code and rebase the comparing point to the latest version. (Rebase will omit a `merge` commit point)
```
git pull --rebase
```

- Rebase other branch to current branch.  ([Detail](https://medium.com/starbugs/git-%E6%88%91%E4%BB%A5%E7%82%BA%E7%9A%84-git-rebase-%E8%88%87%E5%92%8C-git-merge-%E5%81%9A%E5%90%88%E4%BD%B5%E5%88%86%E6%94%AF%E7%9A%84%E5%B7%AE%E7%95%B0-cacd3f45294d))
```
git rebase masterBranch
```

- Undo and abort the rebase progress.
```
git rebase --abort
```

- Rebase Interactive Mode.  ([Detail](https://dotblogs.com.tw/wasichris/2016/05/04/re))
```
git rebase -i 069f5ac # Support modify multiple commit logs.
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

- Compare the different. (Use `log.diff` file to view the diff)
```
# Compare the "code" content.
git diff [lastCommit] [newCommit]
# Compare the "path" of two commit and export to 'diff.txt' file.
git diff-tree -r --no-commit-id --name-status --text --diff-filter=ACDMRT [lastCommit] [newCommit] > ./log.diff
```

- Discard code from **staged**
```
git reset HEAD -- [path]/[to]/[file]
```

- git commit the change
```
git commit
git commit -m "add new page" // Shortcut for comment.
```

- Fix the previous commit comment
```
git commit --amend
```

- Update the previous commit with new code change
```
# Add the file to stage and commit it
git add ./codeChange.file
git commit --amend
```

- Check the commit log
```
git log
git log --oneline # Show the short log.
git log --graph  # Show the log graph.
git log --graph --oneline --all --decorate # one line log.
git log --stat   # Change files.
git log <xxx branch> # Show only xxx branch log.
git log --author="xxx user" # Show the xxx user commit.
```

- Push the commit to remote
```
git push <repository> <refspec>
# example
git push origin HEAD:refs/for/master
# Push complete repository detail into new remote repository.
git push --mirror

# Create a new branch 'newBranch' at upstream and push/refs it from local.
# ex1
git push --set-upstream origin newBranch 
# ex2
git push -u origin newBranch
# ex3 Force push to replace the remote branch.
git push --force
```

- Revert all change back to last commit.  
  `--soft`: Keep both **Staging Area** and **Working Directory** different.  
  `--mixed`: Delete **Staging Area**, but keep **Working Directory** different.  
  `--hard`: Delete both **Staging Area** and **Working Directory** different.  
```
git reset HEAD^
git reset --soft <commit-hash>  # Reset all commit back to commit id.
git reset --hard <commit-hash>  # Reset all commit back to commit id. (Not same as detached) 
git reset --hard origin/<branch_name>  # Reset commit back to remote origin branch commit. (Discard all local commit)
```

- Revert back with specific commit hash
```
git revert c0d0001      # Normal commit. 
git revert c0d0002 -m 1 # Merge commit "-m 1" means commit parent 1.
```

- Save current status (**save** can be omitted)
```
git stash save
git stash push ../file  # Stash specific file
git stash push -m "my_stash_name"  # Stash with title.
git stash -u  # Stash all the file include untracked. (-u == --include-untracked)
```

- Display **stash** data
```
git stash show // Show last detail stash.
git stash list // List out all stash data.
```

- Restore the **stash**
```
git stash pop  # Restore the data and drop the stash history
git stash pop stash@{n} # To pop (i.e. apply and drop) the `n` stash.
git stash apply  # Keep the stash history, stash will keep store in list.
```

- Delete the latest **stash**
```
git stash drop
```

- Delete all the **stash**
```
git stash clear
```

- Backup git log temporary.
# If git object haven't GC, it can get back to any comments, branches and CLI history.
```
git reflog
```

- Cherry-pick: Merge a commit '99daed2' from other branch to master branch.
  It also can pick the commit from the current branch to the top commit. ([Detail](https://backlog.com/git-tutorial/tw/stepup/stepup7_4.html))
```
$ git checkout master
Switched to branch 'master'
$ git cherry-pick 99daed2
error: could not apply 99daed2... commit
hint: after resolving the conflicts, mark the corrected paths
hint: with 'git add <paths>' or 'git rm <paths>'
hint: and commit the result with 'git commit'
```
