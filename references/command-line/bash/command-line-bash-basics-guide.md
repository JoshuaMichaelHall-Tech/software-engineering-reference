### Commands to Note
Clear Terminal
`ctrl - l` Clear Terminal
`\` escape character
`''` escapes most characters in line
`cd -` goes to previous 
`tail` gets last line of an output
`|` take output from left and send as input to right
`grep` search input stream for a given string, `-i` ignore case, takes arg
`cut --delimiter=' '` outputs array `-f2` gets the second field
### Connecting programs

All programs have an input and an output. We can redirect these streams.
- `< file` and `> file` rewire the input and output streams of a program to a file respectively:
```term
missing:~$ echo hello > hello.txt
missing:~$ cat hello.txt
hello
missing:~$ cat < hello.txt
hello
missing:~$ cat < hello.txt > hello2.txt
missing:~$ cat hello2.txt
hello
```

- `>>` appends to a file:
- `|` pipes output of one program as input to the next
```term
missing:~$ ls -l / | tail -n1
drwxr-xr-x 1 root  root  4096 Jun 20  2019 var
missing:~$ curl --head --silent google.com | grep --ignore-case content-length | cut --delimiter=' ' -f2
219
```

### Permissions
- For directories, `r` can see/list files, `w` create, rename, save, `x` search, enter (need all parent `x`)
- `sudo` only works in some instances. Operations like `|`, `>`, and `<` are done _by the shell_, not by the individual program.
- we can work around this:

```
$ echo 3 | sudo tee brightness
```

Since the `tee` program is the one to open the `/sys` file for writing, and _it_ is running as `root`, the permissions all work out.



