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