# Useful Command Line Stuff

### Table of contents
- [Alias](#alias)
- [Compression](#compression)
- [Copy](#copy)
- [Create](#create)
- [Cron](#cron)
- [Download](#download)
- [ENV](#env)
- [Information](#information)
- [Keys](#keys)
- [Navigate](#navigate)
- [Ownership](#ownership)
- [Remove](#remove)
- [Search](#search)
- [Symlink](#symlink)
- [Tail](#tail)



<a name="alias">
## Alias

#### See all alias
```
alias
```

#### Add an alias
```
vim ~/.bash_profile
alias work='cd <pathname>'
```

#### Activate/reload changes in current cli
```
source ~/.bash_profile
```

#### Alias syntax (in ~/.bash_profile)
```
alias work='cd <pathname>'
alias pictures='cd <pathname>'
```



<a name="compression">
## Compression

#### Untar a tar
```
tar xvzf latest.tar.gz
```

```
tar -xzf latest.tar.gz
```

#### Untar a rar to a directory
```
tar -C <pathname> -xvf <filename>.tar
```

#### Tar a file
```
tar -cvzf <filename>.tar.gz <filename_to_compress>
```

#### Compress jpg files only in a directory
```
tar -cvzf <filename>.tar.gz <pathname>*.jpg
```



<a name="copy">
## Copy

#### Copy a folder and sub directories
```
cp -R <pathname>/* <pathname>
```



<a name="create">
## Create

#### Make directory and create parents without error if they don't exist
```
mkdir -p <pathname>
```

#### Make directory and create child folders
```
mkdir -p <pathname>/{js,css,lib,img,views}
```

#### Make files in a directory
```
touch <pathname>/{filters.js,controllers.js,directives.js}
```



<a name="cron">
## Cron

#### Crontab
```
crontab -e
```

#### Tail the cron error log
```
tail -f /var/log/cron
```



<a name="download">
#### Download
```
wget <url>
```



<a name="env">
## Env

#### Add env
```
export MY_ENV=value
```

#### Show env
```
echo MY_ENV
```



<a name="information">
## Information

#### Find file
```
locate <pathname>
```

#### Get directory path of file
```
dirname <filepath>
```

#### Disk Free will show the free space on each of the mounted file systems.
```
df -h 
```

#### Size of folder
```
du -hs <pathname>
```

#### File sizes of directories
```
du -h <pathname> | grep '[0-9]G'
```

#### Grep the process
```
sudo ps -ef | grep <process>
```

#### Kill process
```
kill -9 <pid>
```

#### What is using a port number
```
sudo lsof -i :<port_number>
```

#### Find path of executable
```
which <executable>
```

#### Username
```
whoami
```

#### Computer information
```
uname -a
```

##### 32-bit example
- Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

##### 64-bit examples
- Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
- Darwin MacBookPro 14.4.0 Darwin Kernel Version 14.4.0: Thu May 28 11:35:04 PDT 2015; root:xnu-2782.30.5~1/RELEASE_X86_64 x86_64



<a name="keys">
## Keys

#### Copy public key to clipboard
```
pbcopy < ~/.ssh/id_rsa.pub 
```

#### Add your SSH key to the ssh-agent:
```
ssh-add ~/.ssh/id_rsa
```

<a name="navigate">
## Navigate

#### Perform previous command
```
!!
```

#### Run previous n command
```
!-1
```

#### Search and execute
```
!string
```

#### Cli history
```
history
```

#### Go back to previous directory
```
cd —
```

#### Current directory
```
pwd
```


#### Reset/clear cli
```
cmd + k
```

```
reset
```



<a name="ownership">
## Ownership

#### Set ownership to current user
```
sudo chown `id -u` <pathname>
```

#### Recursively set folder ownership
```
sudo chown -R <user>:<group> <pathname>
```



<a name="remove">
## Remove

#### Remove directory
```
rm -rf <pathname>
```

#### Remove contents of directory
```
rm -rf <pathname>/*
```



<a name="search">
## Search

#### Reverse search history (mac)
```
ctrl + R
```

#### Grep
```
grep <string> <filename>
```

```
grep <string> <filename1> <filename2> <filename3>
```

#### Search directory
```
grep -nr <string> <directory>
```

#### Find string in file (do not include .svn files)
```
grep -rl <string> <pathname> | grep .svn -v
```

#### Find file
```
find <pathname> -name <filename>
```

#### Search for filename, not in a location, Loop through results and echo directory name
```
find . -name package.json | grep -v node_modules | while read line; do echo $(dirname $line); done
```

#### Search 
> *filename* not in *pathname_1*, narrow results only in *pathname_2*, then loop, cd into directory, run command then go back to original location

```
find . -iname bower.json | grep -v <pathname_1> | grep <pathname_2> | while read line; do cd $(dirname $line); bower install; cd -; done
```

#### Search 
> *filename* not in *pathname_1* or *pathname_2*, narrow results only in *pathname_3*

```
find . -iname <filename> | grep -v <pathname_1> | grep -v <pathname_2> | grep <pathname_3> 
```



<a name="sym_link">
## Sym Link

#### Sym link
```
ln -s <filename> <sym_link>
```



<a name="tail">
## Tail
```
tail -f <filename>
```

#### Tail 100 lines from end
```
tail -100f <filename>
```

#### Tail with grep
```
tail -100f <filename> | grep 'not found'
```