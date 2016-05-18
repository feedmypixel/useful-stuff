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

#### Add files to the previous commit by:
```
git add -p
```
add files

```
git commit --amend
```

files will be added to previous commit


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

#### Remove remote branches already merged
```
git branch --merged | grep -v "\*" | grep -v master | xargs -n 1 git branch -d
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

#### Checkout a previous commit
```
git co <commit_sha>
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
git commit -p
```

#### Commit a hunk of code conditionally with a message
```
git commit -pm 'Commit message'
```

#### Add interactively
```
git add -i
```

#### Hunk options 
> When in patch or interactive mode

Yes, add this hunk

```
y
```

No, don’t add this hunk

```
n
```

No, don’t add this hunk and all other remaining hunks

```
d
```

Quit

```
q
```

Split the hunk into smaller hunks

```
s
```

Manually edit the hunk

```
e
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
## Merge

#### Pull master
```
git pull origin master
```

#### Show merge conflict(s) then fix conflicts in files
```
git st 
```

#### Add merge conflict file
```
git add <filename>
```

#### Commit
```
git ci
```

#### Accept merge message

#### Push to branch
```
git push origin <branchName>
```

#### Merge local branch onto current branch
```
git merge <branchName>
```

<a name="rebase">
## Rebase

#### Rebase a pull onto current branch
```
g pull --rebase
```

#### Rebase back to previous commit
```
git rebase -ip HEAD~3
```

#### Rebase master onto a branch
```
git rebase master <your branch name>
```


#### Rebase first and second commit.
```
git rebase -i --root master
```

#### Operate on non-consecutive commits 
You can rebase non consecutive commits together this is just a matter of working bottom up (oldest is at the top) and taking the latest/last commit back to the first/oldest commit you wish to fixup/squash with. I would backup your branch and experiment. Remember to fixup/squah at same time as moving the line of the commit in rebase.


#### Rebase order
<pre>
----- old commit

----- other commit

----- other commit

----- latest commit
</pre>


#### To merge `rebase -ip` then place commits together, you must move your latest to oldest otherwise commits in-between get removed.

#### Move commits around
<pre>
----- old commit

fixup latest commit

----- other commit

----- other commit
</pre>

#### When a rebase goes wrong
```
git reflog
```

```
git reset <sha> --hard
```


<a name="remote">
## Remote

#### Show origin
```
git remote show origin
```

or
```
git remote -v
```

#### Add remote
```
git remote add <remote_name> <remote_url>
```

#### Change remote url
```
git set-url origin <remote_name> <remote_url>
```

#### Remove remote
```
git remote rm <destination>
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

#### Undo last commit (handy to recommit W.I.P)
```
git reset --soft HEAD^
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
git tag <tag_name>
```

#### Show tags
```
git tag
```

#### Checkout tags
```
git checkout tags/<tag_name>
```

#### Push tags
```
git push --tags
```

#### Remove Tags
```
git tag -d <tag_name>
```

#### Remote remove tags
```
git push origin :refs/tags/<tag_name>
```

#### Rename tag
```
git tag <new_tag_name> <old_tag_name>
git tag -d <old_tag_name>
git push origin :refs/tags/<old_tag_name>
git push --tags
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