# Vim Cheatsheet

>Disclaimer: This cheatsheet is summerized from my own experience and other publich information. It should not be considered official advice.

## Global
<pre lang=bash>
:help keyword # open help for keyword
:o file       # open file
:saveas file  # save file as
:close        # close current pane
</pre>

## Cursor movement
<pre lang=bash>
h        # move cursor left
j        # move cursor down
k        # move cursor up
l        # move cursor right
H        # move to top of screen
M        # move to middle of screen
L        # move to bottom of screen
w        # jump forwards to the start of a word
W        # jump forwards to the start of a word (words can contain punctuation)
e        # jump forwards to the end of a word
E        # jump forwards to the end of a word (words can contain punctuation)
b        # jump backwards to the start of a word
B        # jump backwards to the start of a word (words can contain punctuation)
0        # jump to the start of the line
^        # jump to the first non-blank character of the line
$        # jump to the end of the line
g_       # jump to the last non-blank character of the line
<b>gg       # go to the first line of the document </b>
<b>G        # go to the last line of the document </b>
5G       # go to line 5
fx       # jump to next occurrence of character x
<b>Fx       # jump to previous occurrence of character x </b>
tx       # jump to before next occurrence of character x
<b>}        # jump to next paragraph (or function/block, when editing code) </b>
<b>{        # jump to previous paragraph (or function/block, when editing code) </b>
zz       # center cursor on screen
Ctrl + b # move back one full screen
Ctrl + f # move forward one full screen
<b>Ctrl + d # move forward 1/2 a screen </b>
<b>Ctrl + u # move back 1/2 a screen </b>
</pre>

## Insert mode - inserting/appending text
<pre lang=bash>
i        # insert before the cursor
I        # insert at the beginning of the line
a        # insert (append) after the cursor
A        # insert (append) at the end of the line
o        # append (open) a new line below the current line
O        # append (open) a new line above the current line
ea       # insert (append) at the end of the word
Esc      # exit insert mode
</pre>

## Editing
<pre lang=bash>
r        # replace a single character
J        # join line below to the current one
<b>cc       # change (replace) entire line </b>
<b>cw       # change (replace) to the start of the next word </b>
ce       # change (replace) to the end of the next word
cb       # change (replace) to the start of the previous word
c$       # change (replace) to the end of the line
s        # delete character and substitute text
S        # delete line and substitute text (same as cc)
xp       # transpose two letters (delete and paste)
.        # repeat last command
u        # undo
Ctrl + r # redo
</pre>

## Marking text (visual mode)
<pre lang=bash>
v        # start visual mode, mark lines, then do a command (like y-yank)
V        # start linewise visual mode
o        # move to other end of marked area
O        # move to other corner of block
<b>aw       # mark a word </b>
<b>ab       # a block with () </b>
<b>aB       # a block with {} </b>
<b>ib       # inner block with () </b>
<b>iB       # inner block with {} </b>
Esc      # exit visual mode
Ctrl + v # start visual block mode
</pre>

## Visual commands
<pre lang=bash>
>       # shift text right
<       # shift text left
y       # yank (copy) marked text
d       # delete marked text
<b>~       # switch case </b>
</pre>

## Cut and paste
<pre lang=bash>
yy       # yank (copy) a line
2yy      # yank (copy) 2 lines
<b>yw       # yank (copy) the characters of the word from the cursor position to the start of the next word </b>
y$       # yank (copy) to end of line
p        # put (paste) the clipboard after cursor
P        # put (paste) before cursor
dd       # delete (cut) a line
2dd      # delete (cut) 2 lines
dw       # delete (cut) the characters of the word from the cursor position to the start of the next word
D        # delete (cut) to the end of the line
d$       # delete (cut) to the end of the line
<b>d^       # delete (cut) to the first non-blank character of the line </b>
d0       # delete (cut) to the begining of the line
x        # delete (cut) character
</pre>

## Search and replace
<pre lang=bash>
/pattern       # search for pattern
?pattern       # search backward for pattern
\vpattern      # 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
n              # repeat search in same direction
N              # repeat search in opposite direction
:%s/old/new/g  # replace all old with new throughout file
:%s/old/new/gc # replace all old with new throughout file with confirmations
<b>:noh           # remove highlighting of search matches </b>
</pre>

## Search in multiple files
<pre lang=bash>
<b>:vimgrep /pattern/ {file} # search for pattern in multiple files </b>
:cn                       # jump to the next match
:cp                       # jump to the previous match
:copen                    # open a window containing the list of matches
</pre>

## Exiting
<pre lang=bash>
:w              # write (save) the file, but don't exit
:w !sudo tee %  # write out the current file using sudo
:wq or :x or ZZ # write (save) and quit
:q              # quit (fails if there are unsaved changes)
:q! or ZQ       # quit and throw away unsaved changes
</pre>

## Working with multiple files
<pre lang=bash>
:e file       # edit a file in a new buffer
:bnext or :bn # go to the next buffer
:bprev or :bp # go to the previous buffer
:bd           # delete a buffer (close a file)
:ls           # list all open buffers
:sp file      # open a file in a new buffer and split window
:vsp file     # open a file in a new buffer and vertically split window
Ctrl + ws     # split window
Ctrl + ww     # switch windows
Ctrl + wq     # quit a window
Ctrl + wv     # split window vertically
Ctrl + wh     # move cursor to the left window (vertical split)
Ctrl + wl     # move cursor to the right window (vertical split)
Ctrl + wj     # move cursor to the window below (horizontal split)
Ctrl + wk     # move cursor to the window above (horizontal split)
</pre>

## Tabs
<pre lang=bash>
:tabnew or :tabnew file # open a file in a new tab
<b>Ctrl + wT               # move the current split window into its own tab </b>
gt or :tabnext or :tabn # move to the next tab
gT or :tabprev or :tabp # move to the previous tab
<b><number>gt              # move to tab <number> </b>
:tabmove <number>       # move current tab to the <number>th position (indexed from 0)
:tabclose or :tabc      # close the current tab and all its windows
:tabonly or :tabo       # close all tabs except for the current one
:tabdo command          # run the command on all tabs (e.g. :tabdo q - closes all opened tabs)
</pre>

## Advanced:
<pre lang=bash>
:%norm A*               # append a '*' symbol at the end of every line. 
:'<,'>norm A",          # append a '",' string at the end of the lines selected previously by visual mode.
</pre>

This is what it means:
```
 %       = for every line
 norm    = type the following commands
 A*      = append '*' to the end of current line
```
