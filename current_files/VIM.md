Start by running `vim` in the terminal.
#### Modes
- normal (starts here, press esc (some rebind caps lock to do this))
- insert mode (press i)
- replace (press R)
- visual (press v)
- visual line (press shift + V)
- visual block (press ^v)
- command-line (press :)

#### Notation
Control + V can be written:
- `^V`
- `Ctrl-V`
- `<C-V>`

#### Commands
In command line mode:
- `h`, `j`, `l`, `k` move the cursor.
- `:q!` close current window, quits when all are closed
- `:qa` closes all windows
- `:wq` writes (saves) the file, and closes all windows
- `:help (KEY (W) OR COMMAND (:W))`
- `x` delete character under cursor.
- `i` Insert text mode
- `<esc>` return to Normal mode
- `0` moves to start of line
- `a` append text
- `dd` delete whole line
- `u` undo
- `U` undo whole
- `r`+ char replaces with char
- `CTRL-R` redo command
- `p` put previously deleted text after

- Combos:
	- operator number motion
	- `d` delete operator
	- `dw` delete + to beginning of next word
	- `d$` delete + to end of line
	- `de` delete + to end of word
	- `3w` moves 3 words
	- `d2w` deletes two words
	- `c` change operator
	- `ce` change until end of word
	- `cc` change until end of line

### Buffers, Windows, Tabs


VIMs interface is a programming language.

#### Normal Mode
