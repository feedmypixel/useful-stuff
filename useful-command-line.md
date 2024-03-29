# Useful Command Line Stuff

### Table of contents
- [Alias](#alias)
- [Append](#append)
- [base64](#base64)
- [Compression](#compression)
- [Copy](#copy)
- [Count](#count)
- [Create](#create)
- [Cron](#cron)
- [Download](#download)
- [ENV](#env)
- [Information](#information)
- [Locate binary](#locate-binary)
- [Keys](#keys)
- [Navigate](#navigate)
- [Netcat](#netcat)
- [Ownership](#ownership)
- [Permissions](#permissions)
- [Remove](#remove)
- [Search](#search)
- [Search & Replace](#search-replace)
- [Symlink](#symlink)
- [Tail](#tail)
- [Time](#time)
- [Wget](#wget)


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

<a name="append">
## Append
Append text to file
```
echo BEN="example" >> /etc/environment
```

<a name="base64">
## Base64

#### encode
```
echo -n '<item-to-encode>' | openssl base64
```

#### decode
```
echo '<item-to-decode>' | base64 --decode
```

<a name="cd">
## CD

#### quickly change directory
If you have the following two folders

```
/ben/cats
/ben/dogs
```
You can switch from `cats` to `dogs` by using:

```
cd cats dogs
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

#### Copy a folder and sub directories (not including parent directory)
```
cp -R <pathname>/* <pathname>
```

<a name="count">
## Count

#### Count folders in working directory
```
ls -l | grep "^d" | wc -l
```


<a name="create">
## Create

#### Make directory and create parents without error if they don't exist
```
mkdir -p <pathname>
```

#### Make directory and cd into it
```
mkdir <directory_name> && cd $_
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
echo $MY_ENV
```

#### Show all envs
```
printenv
```

#### remove env
```
unset MY_ENV
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

#### Find PID by port
```
lsof -i :<port>
```

#### Kill process
```
kill -9 <pid>
```

#### Kill all by name
```
killall node
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

<a name="locate-binary">
## Locate Binary
Locate psql bin folder
```
locate psql | grep /bin
```

<a name="keys">
## Keys

#### Create key
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

#### Copy public key to clipboard
```
pbcopy < ~/.ssh/id_rsa.pub 
```

#### Add your SSH key to the ssh-agent:
```
ssh-add ~/.ssh/id_rsa
```

#### Adding or changing a passphrase
```
ssh-keygen -p
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

<a name="netcat">
## Netcat
Ping Redis server
```
nc -z localhost 6379
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

#### Recursively set folder ownership to username
```
sudo chown -R `whoami` /usr/local
```

```
sudo chown -R `whoami` /Library/Caches/Homebrew/
```

<a name="permissions">
## Permissions
```
chmod 754 myfile
```

Here the digits `7`, `5`, and `4` each individually represent the permissions for the `user`, `group`, and `others`, in that order. 
Each digit is a combination of the numbers `4`, `2`, `1`, and `0`:

- `4` for "read",
- `2` for "write",
- `1` for "execute"
- `0` for "no permission."


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

#### Grep with RegEx
```
grep -nrE "data-sso=\"(true|client|server)\"" .
```

#### Grep with inverse
```
grep -nrE 'target="(_blank|_self|_top|_parent)"' . | grep -E -v 'target="(_blank|_self|_top|_parent)"'
```

#### Search directory
```
grep -nr <string> <directory>
```

#### Find string in file (do not include .svn files)
```
grep -rl <string> <pathname> | grep .svn -v
```

#### Find string in file (only in .html files)
```
grep -nr --include \*.html <string> .
```

#### Grep for selectorsand save results to file
```
grep -ohrE '^@m[^({]+' govuk_frontend_toolkit/stylesheets/ > ~/Desktop/govuk_frontend_toolkit-mixins.txt
```
```
grep -ohrE '^[$][^:]+' govuk_frontend_toolkit/stylesheets/ > ~/Desktop/govuk_frontend_toolkit-vars.txt
```
```
grep -ohrE '^[\.#][^{]+' govuk-elements-sass/public/sass/ > ~/Desktop/govuk-elements-sass-selectors.txt
```

#### Find file
```
find <pathname> -name <filename>
```

#### Loop through top level directories and git pull
```
find . -maxdepth 1 -type d | while read line; do cd $line; g co master; g pull; cd -; done
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

#### Find files and prepend value
```
folder="app/views/"; host="http://localhost:3000"; find $folder -name *.html | grep -v includes | grep -v layout | while read line; do echo $host${line#$folder}; done
```

#### Add filename labels to images 
```
find . -name *.png | while read line; do fileName=$(basename $line); montage -label '%f' $fileName "${fileName}_test"; done;
```

<a name="search-replace">
## Search & Replace

#### Sed
```
sed 's/one/ONE/' <file
```

- `s`	  			Substitute command
- `/../../`	  	Delimiter
- `one`	  		Regular Expression Pattern Search Pattern
- `ONE`	  		Replacement string



<a name="sym_link">
## Sym Link

#### Sym link
```
ln -s <filename> <sym_link>
```

<a name="time">
## Time

Time how long a command takes
```
time npm run something
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


<a name="wget">
## Wget

https://www.guyrutenberg.com/2014/05/02/make-offline-mirror-of-a-site-using-wget/

```
wget --mirror --convert-links --adjust-extension --page-requisites 
--no-parent http://example.org
```
