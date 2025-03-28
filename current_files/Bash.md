
```Bash
# bash supports control flow techniques including `if`, `case`, `while` and `for`.

# Define variable
foo=bar

# Reference variable
echo $foo
-> bar

# Double quotes (string interpolation)
echo "Value is $foo"
-> Value is bar

# Single quotes
echo 'Value is $foo'
-> Value is $foo

# Open defined fuction
vim example.sh

# Load function into terminal
source example.sh

# Call function after loading
example argument # ($1 is the first argument reserve keyword..., $_ refers to the previous argument)

# Using sudo
mkdir /mtn/new
-> Permission denied
sudo !! (gets previous command: mkdir /mtn/new)

# || is or, below we see that since false always returns error code of 1, Bash will run the second because the first failed.
false || echo "oops"
-> oops

# Since true returns error code 0 (no error)...
true || "Does not print"
-> 

&& # and operator
false && echo "Not printed"
-> 

; # Concatenate commands on the same line
false : echo "This will always print!"
-> This will always print!

# Command substitution executes CMD in $(CMD) and substitute return in its place
echo "We are in $(pwd)"
-> We are in /present_working_directory

# Process substitution uses `<` to pass output of one command to temp file, and handing handle to next command
cat <(ls) <(ls ..)

# other references (more here: https://tldp.org/LDP/abs/html/special-chars.html)
`date` refers to today, 
`$0` refers to name of script, 
`$1` to `$9` arguments to the script in order, 
`$#` refers to number of arguments, 
`$$` refers to pid, 
`$@` refers to all arguments,
`$?` refers to the code of the previous command, 
`!!` returns entire last command with arguments, 
`$_` Last argument from last command, 
`$file` refers to the current file name, 
`>` redirects STDOUT, 
`2>` redirects standard error, 
`/dev/null` is a place for discarding output,
`if` refers to `test` for `man` purposes `fi` to close

# Shellglobbing: shortcut for feeding two arguments to one method
convert image.{png,jpg} # is short for:
convert image.png image.jpg

# Wildcards
`?` # any one character
`*` # any consecutive characters

# Get differences between two files:
diff <(ls foo) <(ls bar)

# To set a file to be interpreted by the shell as a Python script, use a shebang:
Python Script (example.py)
'#!/usr/bin/env python' (Instead of hard coding the path, this gets the path)

# Error Debugging Tool
shellcheck sample.py

# Common tools:
convert # images
ffmpeg # video
tldr command # gives examples of how to use a command

# Find files
find target_folder -name src -type d # Can also remove, etc.
fd ".*py" # Abbreviated, ignored .git
locate shell # Finds path(s) in system for the argument, in effect indexing them for faster finding later.
updatedb # Updates indexes

# Searching contents
grep foobar mcd.sh # Searching content of files, finds foobar in mcd.sh
grep -R foobar . # Checks files in . for argument
`-C` with integer arg gets results with context
`-v` inverts results
`-R` recursive
ripgrep # Like grip, but with extras like color coding, speed

# History
history :convert
CTRL-R

# Fuzzy finder
cat example.txt | fzf #Similar to interactive , gets all lines, offers search option for typing parameter to find something in the file

# Directory listing and navigation
tree
broot # Like tree, but allows to type and find 

# Navigating file system
Finding frequent and/or recent files and directories can be done through tools like [`fasd`](https://github.com/clvv/fasd) and [`autojump`](https://github.com/wting/autojump). Fasd ranks files and directories by [_frecency_](https://web.archive.org/web/20210421120120/https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Places/Frecency_algorithm), that is, by both _frequency_ and _recency_. By default, `fasd` adds a `z` command that you can use to quickly `cd` using a substring of a _frecent_ directory. For example, if you often go to `/home/user/files/cool_project` you can simply use `z cool` to jump there. Using autojump, this same change of directory could be accomplished using `j cool`.

```