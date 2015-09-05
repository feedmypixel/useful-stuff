# Useful Git Stuff

A list of useful git commands.

### Table of contents
- [Amend](#amend)
- [Branch](#branch)
- [Changes](#changes)
- [Conditionally](#conditionally)
- [Config](#config)
- [Duplicate](#duplicate)
- [Merge](#merge)
- [Rebase](#rebase)
- [Remote](#remote)
- [Reset](#reset)
- [Search](#search)
- [Shortcuts](#shortcuts)
- [Stash](#stash)
- [Tag](#tag)
- [Update](#update)



<a name="amend">
## Amend 

#### Amend last message
```
git commit --amend
```

#### Rename branch
```
git br -m <newname>
```

#### Change a filename capitalisation
```
git mv --force myfile MyFile
```



<a name="branch">
## Branch

#### Show remote branches
```
git branch -a
```

#### Create branch and check it out
```
git co -b <branchName>
```

#### Create local branch on remote
```
git push -u origin <local branch name>
```

#### Remove remote branch
```
git push origin :bc-name-log-fix
```

#### Create branch and switch to it
```
git checkout -b branchName
```

#### Delete a local branch
```
git br -D <branchName>
```

#### Checkout a new branch
```
git fetch
git co <branchName>
```


<a name="changes">
## Changes

#### Show staged changes
```
git diff --cached
```

#### File names of whats been changed
```
git whatchanged
```

#### For diff
```
git whatchanged -p
```



<a name="conditionally">
## Conditionally

#### This tells git to automatically stage tracked files -- including deleting the previously tracked files.
```
git add -u
```

#### Add lines of code conditionally
```
git add -p
```

#### Commit code conditionally
```
git co -p
```

#### Add interactively
```
git add -i
```



<a name="config">
## Config

#### Show username
```
git config user.name
```

#### Show all config
```
git config --list
```



<a name=“duplicate”>
## Duplicate

####
Duplicate repo
Make a clone of the repo

```
git clone --bare <repository_to_duplicate>
```

Push to a new repository
```
cd <repository_to_duplicate>.git  
git push --mirror <new_repository>
```



<a name="merge">
# Merge

##### Pull master
```git pull origin master```

##### Show merge conflict(s) then fix conflicts in files
```
git st 
```

##### Add merge conflict file
```
git add <filename>
```

##### Commit
```
git ci
```

##### Accept merge message

##### Push to branch
```
git push origin <branchName>
```


<a name="rebase">
## Rebase

#### Rebase back to previous commit
```
git rebase -ip HEAD~3
```

#### Rebase master onto a branch
```
git rebase master <your branch name>
```

#### Operate on non-consecutive commits 
You can rebase non consecutive commits together this is just a matter of working bottom up (oldest is at the top) and taking the latest/last commit back to the first/oldest commit you wish to fixup/squash with. I would backup your branch and experiment. Remember to fixup/squah at same time as moving the line of the commit in rebase.


##### Rebase order
<pre>
----- old commit

----- other commit

----- other commit

----- latest commit
</pre>


##### To merge `rebase -ip` then place commits together, you must move your latest to oldest otherwise commits in-between get removed.

##### Move commits around
<pre>
----- old commit

mixup latest commit

----- other commit

----- other commit
</pre>


<a name="remote">
## Remote

#### Show origin
```
git remote show origin
```



<a name="reset">
## Reset

#### Remove all files from staging area
```
git reset HEAD
```

#### Remove specific file from staging
```
git reset HEAD <file>
```

#### Revert file (or checkout a file from a repo)
```
git checkout <branch> <file>
```

#### Undo last commit
```
git reset --soft 'HEAD^'
```

#### Reset checkout git wise
```
git clean -f -d -x
```

#### Reset last commit
```
git reset --soft HEAD~1
```

#### Abort merge
```
git reset --hard HEAD
```

#### Revert last commit
```
git reset --soft HEAD~1
```

#### Clear out all changes
```
git co .
```

#### Reset files
```
git reset HEAD
```

#### Revert all files
```
git reset --hard
```

#### Remove branches that have been merged already remotely
```
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```

#### Go back to previously checkout branch
```
git co -
```

#### Reset fork on github
```
git remote add upstream git://<repo>.git
git fetch upstream
git branch backup
git reset --hard upstream/master
git push --force
```


<a name="search">
## Search

#### Search logs for string (-p switch shows the commit diff as well)
```
git log -p -S string
```

#### Search logs for a file
```
git log --all -- '**/my_file.png'
```

#### Show specific commit 
```
git show <commit sha>
```



<a name="shortcuts">
## Shortcuts

#### Shortcuts, can be set via .gitconfig
<pre>
br = branch
ci = commit
co = checkout
df = diff
g  = grep -I
lg = log -p
pb = publish-branch
rb = rbranch
rc = rank-contributors
rv = review
sm = show-merges
st = status
</pre>


<a name="stash">
## Stash

#### Git stash list, all stashes
```
git stash list
```

#### Drop a specific stash
```
git stash drop stash@{0}
```

#### Apply stash
```
git stash apply
```

#### Apply a stash and remove it from the stash list
```
git stash pop stash@{n}
```

#### Apply a stash and keep it in the stash cache
```
git stash apply stash@{n}
```

#### Clear all stash
```
git stash clear
```

#### Show whats in stash
```
git stash show -p
```



<a name="tag">
## Tag
#### Add a tag
```
git tag <tag name>
```

#### Show tags
```
git tag
```



<a name="update">
## Update

#### update local branch only
```
git merge --ff-only @{u}
```

#### Update and prune
```
git fetch -p
```

#### Download the latest commits
```
git remote update -p
```

#### Fetch latest changes
```
git fetch
```

#### Fetch and merge latest changes
```
git pull
```