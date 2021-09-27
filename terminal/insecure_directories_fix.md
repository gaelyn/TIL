### Problem
When setting up an application locally, I ran the following in my terminal  
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
which resulted in this alert in my terminal
```
zsh compinit: insecure directories, run compaudit for list.
Ignore insecure directories and continue [y] or abort compinit [n]?
```
Now this alert comes up every time I open my terminal or a new terminal tab.  

I didn't want to hit `y` and when I hit `n` I got this
```
compinit: initialization aborted
complete:13: command not found: compdef
```
Running `compaudit` resulted in the following
```
There are insecure directories:
/usr/local/share/zsh/site-functions
/usr/local/share/zsh
```

### Solution
I talked through this with Josh and. starting with [this Stack Overflow post](https://stackoverflow.com/questions/13762280/zsh-compinit-insecure-directories), the first solution was to try   
 `compaudit | xargs chown -R "$(whoami)"`

 I really didn't know what this was supposed to do so we broke it down. According to the SO poster
 > setting the current user as the owner of all the directories/subdirectories/files in cause  

 - `compaudit` lists insecure folders (group writable) [zsh docs](https://zsh.sourceforge.io/Doc/Release/Completion-System.html#index-compaudit)
 - `xargs` - Execute a command with piped arguments coming from another command, a file, etc
  - Run a command using the input data as arguments:
     `arguments_source | xargs command`
 - `chown -R` - Recursively change the owner of a directory and its contents.
 - `whoami` - Print the username associated with the current effective user ID.

 Next I ran `compaudit | xargs chmod go-w`
 > Removing write permissions for group/others for the files in cause

 - `chmod go-w` - Change the access permissions of a file or directory.
  - [g]roup
  - [o]thers
  - [w]rite


  Now, `compaudit` does not return anything
