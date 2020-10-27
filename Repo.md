# ===========  Repo Command   ===========  
Detail:  
https://source.android.com/setup/develop/repo


- This creates a **.repo/** directory with Git repositories for the Repo source code and the standard Android manifest files.
```
repo init -u url [options]
```

- It synchronizes the project files
```
repo sync [project-list] -j1 
```

- Begins a new branch for development, starting from the revision specified in the manifest.
```
repo start -all [branch-name] [project-list]
```

- Compares the working tree to the staging area (index) and the most recent commit on this branch (HEAD) in each project specified.
```
repo status [project-list]
```

- Downloads the specified change from the review system and makes it available in your project's local working directory.
```
repo download [target revision]
```

- Executes the given shell command for all repo project. (ex: repo forall -c git reset --hard HEAD)
```
repo forall [project-list] -c [command]
```