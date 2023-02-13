# Git Cheat Sheet

### Clone from remote repository
```
git clone <remote-repository-url>
```
### Create a branch
```
git checkout -b <new-branch-name>
```

Check to make sure that new branch is active
```
git branch
```

### set remote branch tracking
```
git push -u origin <new-branch-name>
```
or
```
git push --set-upstream origin <new-branch-name>
```

### check if remote has any updates
```
git fetch --dry-run
```

### Create a branch from tag
```
git checkout -b <new-branch-name> <tag>
```

### Switch to a remote branch
```
git checkout remote_branch_name
```

### Get Remote URL
```
git config --get remote.origin.url
```

### Rename a branch
Rename the local branch to the new name
```
git branch -m <old_name> <new_name>
```
Delete the old branch on remote - where <remote> is (for example `origin`)
```
git push <remote> --delete <old_name>
```
Push the new branch to remote
```
git push <remote> <new_name>
```
Reset the upstream branch for the new_name local branch
```
git push <remote> -u <new-name>
```

### Diff two branches
```
git diff b1..b2
```
**Note**: This command uses two dots

### Merge branch
Switch to the branch you want to merge changes into
```
git fetch origin        # gets you up to date with origin
git merge origin/main   # merge changes from main branch
```

### Delete remote-tracking branches locally
```
git remote prune origin
```

### Delete local branch
```
git branch -d branch_name
```
Force delete local branch
```
git branch -D branch_name
```

## Tags
Like most VCSs, Git has the ability to tag specific points in a repository’s history as being important. Typically, people use this functionality to mark release points (v1.0, v2.0 and so on). 

Although a tag may appear similar to a branch, a tag, however, does not change. It points directly to a specific commit in the history and will not change unless explicitly updated.

### Create annotated tag with comment
```
git tag -a <tag-name> -m "Comment related to tag"
git push origin <tag-name>   # push the tag to remote
```

### List all the tags along with annotations & 3 lines of message for every tag
```
git tag -n3
```
  
### Log user out using CLI
```
git config --global --unset credential.helper
```
