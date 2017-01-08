ViM -- VIsual IMproved
======================

_Vim_ is a decades old text editor - created in 1991 by Bram Moolenaar - and is an extension of the _vi_ line editor originally created in 1976 by Bill Joy.  Since the base functionality in Vim predates both the mouse and graphical interfaces, it utilizes short command line keyboard instructions to quickly and efficiently write and edit documents.  This ability to quickly manipulate text without ever having to leave the keyboard makes Vim a popular editor - even today - among many programmers who swear by it Ps lightning fast productivity.  The large number of seemingly arcane instructions Vim users have to memorize in order to become efficient - or even barely functional - sets Vim's bar for entry abnormally high, and has left many would be adoptors of Vim fustrated, angry and confused about what all the fuss is about.

##Vim is a Modal Editor

Vim has four primary modes, each with its own set of commands:

### Normal Mode.

Normal mode allows the user to navigate and edit a document and is where the user starts by default.  Other modes are entered from within Normal Mode.  In Normal Mode the user can navigate and edit the document.  Return to Normal mode from other modes using `esc`.

`h` - moves to the left  
`l` - moves to the right    
`j` - moves down  
`k` - moves up  
`w` - next word  
`b` - previous word  

for more than a single space, word or line - type a number and then direction, e.g. *5k* to move up five lines

`0` - move to beginning of line
`$` - move to end of line
`gg` - move to beginning of file
`G` - move to end of file

`d+<direction>` (e.g. dl) - delete a character in that direction
prefix a number to delete N characters in specified direction

`dd` - will delete the current line
`D` - delete everything from cursor position to end of line

`x` - deletes the character at the cursor`s current position
`X` - deletes before the cursor
both `x` and `X` accept a number prefix as well

`p` - pastes segments cut or yanked from within Visual Mode.

### Insert Mode.

There are multiple ways to enter Insert Mode
using `i` to start Insert Mode allows text to be inserted to the left of the current cursor position
using `a` inserts to the right of the cursor
Likewise, `I` inserts at the beginning of the line
while, `A` inserts at the end of the line
`o` inserts a new line after the cursor
`O` inserts a new line above the cursor

### Visual Mode

### Command Mode

### Saving and Closing

In normal mode - ZZ to save everything and exit.
To quit the editor - q
Also, :w! (Command, Write, Force Operation w/o question)
Also, :wq (Command, Write, Quit) or :wq!
Also, :q!


### Line Numbering

:set number - turns on line numbering
:set nonumber - turns off line numbering
:set relativenumber - set numbering to relative
:set norelativenumber - absolute line numbering

## The .vimrc File

This is the Vim configuration file.  It's commands are loaded every time the editor is booted.

## Search and Replace

/ - search ( /target ) [Regular Expressions can be used]

replacement within line is
`:s/<target>/<replacement>`
and again RegEx can be used

additional delimiters are also possible
`:s/<target>/<replacement>/gi`
g - makes the substitution global, without it the substitution is only once per line
i - makes the search case insensitive
I - makes the search case sensitive (but what`s the default?)

##Visual Mode

use v to enter Visual mode and then move the cursor to select text.
V starts and sets Visual Mode selecting entire lines instead of characters

y - yanks or copies the selected text
p - pastes selection after the cursor
x - deletes selection
d - cuts the selection
