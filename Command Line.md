Bash Prompt: $    or # if Root
Zsh Prompt: %     or # if Root
echo $SHELL - returns shell directory
startup files: `.bash_profile`, `.bashrc`, `.zprofile`,, and `.zshrc`.
`STDIN` (standard input)
`env` returns the environment variables

Below is an example of the prompt on an Ubuntu Linux server:

```bash
ubuntu@chopin:~$
```

The above prompt follows this format:

```bash
[user]@[hostname]:[current_directory]$
```

|Command|Description|
|---|---|
|`cd`|Change directory.|
|`ls`|List files and directories in current directory.|
|`pwd`|Display the path of the current directory.|
|`touch`|Create a file.|
|`mkdir`|Create a directory.|
|`rm`|Remove a file or directory. Warning: deleting a file or directory with this command is permanent!|
|`cp`|Copy a file or directory.|
|`mv`|Move or rename a file or directory.|
|`echo`|Print text to STDOUT.|
|`cat`|Display contents of a file.|
|`more`|Display contents of a file, starting at the top and letting the user scroll down.|
|`less`|Display contents of a file in an even more interactive way.|
|`head`|Display the first part of a file.|
|`tail`|Display the last part of a file.|
|`man`|Display documentation about a command.|
[[Command Line Shortcuts.png]]

- `/` - The root directory or a separator when listing directories
- `.` - The current directory (also `./`) or the same level
- `..` - The directory one level up (also `../`)
- `../..` - The directory that is two levels up; that is, the directory that is one level up from `..`
- `~` - Your "home" directory, or the directory you are placed in when you log in.
- `*` - The "splat" or "glob" operator. This is the wildcard of the command line and represents "any characters."

running `cd $HOME` is the same as running `cd /home/ubuntu`, assuming your home directory is `/home/ubuntu`.

**Setting Environmental Variables**
```
$ SOMETHING="some value" 
$ echo $SOMETHING 
some value
```
When you set a variable you don't prepend the dollar sign, but when you reference it, you do.

Change Prompt and Environment
```
#Example
$ PS1="\n\[\e[0;37m\][\h] \e[0;35m\]\d\e[0m\]\n\[\e[0;31m\]\u\[\e[0;34m\] in \[\e[1;33m\]\w\[\e[m\]\[\e[0;31m\]\n\[\033[35m\]$\[\033[00m\] "
```
For permanent changes, modify ~/.bashrc
```
#Example
export PS1="\n\[\e[0;37m\][\h] \e[0;35m\]\d\e[0m\]\n\[\e[0;31m\]\u\[\e[0;34m\] in \[\e[1;33m\]\w\[\e[m\]\[\e[0;31m\]\n\[\033[35m\]$\[\033[00m\] "
```

 In Bash and Zsh - using single quotes prevents the `!` from being treated specially; double quotes do not. You can also use `\` to escape the `!` while still using double quotes.

