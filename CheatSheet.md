# Cheat Sheet

## Navigation Basics
| Description | `bash` | `PowerShell` |
| --- | --- | --- |
| Navigation | `cd, pwd` |
| List contents in current directory | `ls` |
| List contents in other directory | `ls /other/directory` |
| List contents including hidden ones | `ls -a` |
| List contents with details | `ls -l` |
| List file details | `ls -l file.txt` |
| List directory details | `ls -ld directory` |
| List contents of directory recursively | `ls -R directory` |
| View contents of text file in scrollable view with basic search functionality | `less file.txt` <br> Page down: Scroll button or **CTRL+F** <br> Page up: **CTRL+B** <br> Search: Type **/searchterm** <br> Navigate search results: Type **n** or **N** <br> Exit less: Type **q** |

## Shell Basics
| Description | `bash` | `PowerShell` |
| --- | --- | --- |
| Find out home directory of current user | `echo $HOME` |
| Find out current username | `echo $USER` |
| Find out current shell | `echo $SHELL` |
| Find out current directory | `echo $PWD` |
| Find out current type of terminal | `echo $TERM` |
| View installed shells | `cat /etc/shells` |
| Change the default shell | `chsh -s /usr/bin/zsh` |
| Find path for command | `which date` <br> `command -v date` <br> `whereis date` |
| View details about command | `type date` |
| Find resolved path of symlink | `realpath /bin/ls` <br> `readlink -f /bin/ls` <br> `ls -ld /bin` |
| Find all files with filename | `locate -b '\date'` <br> `find / -name "date" -ls` |
| List all files installed by package | `dpkg -L docker-ce` |
| Display package information | `apt show docker-ce` |
| Make variable available for child processes of current shell | `export VAR="value"` |
| Permanently add a variable (user) | Append to `~/.bashrc`, then `source ~/.bashrc` |
| Permanently add a variable (all users) | create new script in `/etc/profile.d` |
| Permanently add a variable (system) | Append to `/etc/environmentc`, then `source /etc/environment` |
| View all current environment variables | `env` <br> `printenv` |
| Make a script executable | `chmod +x script.sh` |
| Run a script within the current shell | `source script.sh` |
| Remove a variable | `unset VAR` |
| Execute command in new shell | `sh -c "echo $SHELL"` |
| Write stdout from command to file | `ls fffff > file.txt` <br> `ls fffff 1> file.txt` |
| Append stdout from command to file | `ls fffff >> file.txt` <br> `ls fffff 1>> file.txt` |
| Write stderr from command to file | `ls fffff 2> file.txt` |
| Append stderr from command to file | `ls fffff 2>> file.txt` |
| Write stdout and stderr from command to file | `ls fffff > file.txt 2>&1` <br> `ls fffff &> file.txt` |
| Redirect stdout from one command to another one as stdin | `command1 \| command2` |
| Redirect contents of file to command as stdin | `command < file.txt` |
| **exec + xargs?** |
| Display current username | `whoami` |
| Display details of current user | `id` |

## Files
| | | |
| --- | --- | --- |
| Create one or more new file(s) or modify existing file's last modified | `touch file.txt file2.txt` |
| Create file with content | `echo "Hello World!" > file.txt` |
| Create file interactively | `cat > file.txt` <br> Save with **CTRL+D** |
| View text file on the terminal | `cat file.txt` |
| Edit a text file in the terminal | `nano file.txt` |
| Create a directory | `mkdir directory` |
| Create directory structure | `mkdir -p some/nested/directory` |
| Rename a file | `mv file.txt file2.txt` |
| Move file into directory | `mv file.txt directory` |
| Move and rename | `mv file.txt directory/file2.txt` |
| Move multiple files | `mv file.txt file2.txt directory` |
| Move multiple files | `mv *.txt directory` |
| Move or rename a directory | `mv directory directory2`|
| Ask before overwriting files | `mv -i *.txt directory` |
| Only overwrite if source file is newer | `mv -u *.txt directory` |
| Verbose moving | `mv -v file.txt file2.txt` |
| Skip moving existing files | `mv -n *.txt directory` |
| Overwrite protected file without prompting | `mv -f file.txt file2.txt` |
| Create backup before moving | `mv -S .back -b file.txt directory/file.txt` |
| Copy a file | `cp file file2.txt` |
| Copy file into directory | `cp file.txt directory` |
| Copy multiple files | `cp file.txt file2.txt directory` |
| Copy multiple files | `cp *.txt directory` |
| Copy a directory | `cp -r directory directory2` |
| Ask before overwriting files | `cp -i *.txt directory` |
| Only overwrite if source file is newer | `cp -u *.txt directory` |
| Verbose copying | `cp -v file.txt file2.txt` |
| Preserve file attributes | `cp -p file.txt file2.txt` |
| Remove a file | `rm file.txt` |
| Remove an empty directory | `rmdir directory` |
| Remove a non-empty directory | `rm -r directory` |
| Remove multiple files | `rm file.txt file2.txt` |
| Remove multiple files | `rm *.txt` |
| Ask before removing | `rm -i file.txt` |
| Verbose removing | `rm -v file.txt` |
| Remove without prompting | `rm -f file.txt` |
| Permission format | `-rw-r--r--` <br> 1st character: file type (`-`, `d` or `l`) <br> 1st triplet: owner permissions <br> 2nd triplet: group permissions <br> 3rd triplet: others permissions |
| Permission behaviour on directories | `r`, `w`, `x`: self-explanatory <br> `s` in user triplet: `setuid` (file is executed with owner's privileges) <br> `s` in group triplet: `setgid` (file is executed with group's privileges) |
| Permission behaviour on directories | `r`: contents can be shown (e. g. `ls`) <br> `w`: contents can be altered (e. g. create and delete files) <br> `x`: directory can be navigated using `cd` <br> `s` in group triplet: `setgid` (new files created within the directory inherid the GID of the directory) <br> `t` in others triplet: `sticky` (only the owner can delete or rename files within the directory) |
| Give permission for owner, group and others to only execute a file | `chmod =x script.sh` <br> `chmod a=x script.sh` <br> `chmod ugo=x script.sh` |
| Add permission for owner, group and others to execute a file | `chmod +x script.sh` <br> `chmod a+x script.sh` <br> `chmod ugo+x script.sh` |
| Remove permission for owner, group and others to execute a file | `chmod -x script.sh` <br> `chmod a-x script.sh` <br> `chmod ugo-x script.sh` |
| Add permission for owner to execute a file | `chmod u+x script.sh` |
| Add permission for group to execute a file | `chmod g+x script.sh` |
| Add permission for others to execute a file | `chmod o+x script.sh` |
| Remove all permissions for others | `chmod o= script.sh` <br> `chmod o-rwx` |
| Give all permissions to the owner and read permissions to the group and others | `chmod u=rwx,go=r script.sh` |
| Give read permissions for other users for a directory recursively | `chmod -R o=r directory` |
| Numeric permissions | read = 4 <br> write = 2 <br> execute = 1 <br> no permissions = 0 |
| Numeric permissions with optional fourth digit | setuid = 4 <br> setgid = 2 <br> sticky = 1 <br> no changes = 0 |
| Check permissions in numeric notation | `stat -c "%a" script.sh` |
| Give all permissions to owner, group and others | `chmod 777 script.sh` |
| Change owner of file | `chown user file.txt` |
| Change group of file | `chown :group file.txt` <br> `chgrp group file.txt` |
| Change owner and group of file | `chown user:group file.txt` |
| Change owner of directory recursively | `chown -R user directory` |