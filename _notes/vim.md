---
layout: note
title: vim
---

"You can use any editor or IDE you want on your machine, but you better learn
vim for working on shared, remote, or customer systems." - sage advice from an
old co-worker at HP.

Vimrc
-----

My vimrc is mostly for style. I do not want to depend on lots of functionality
in a vimrc to prevent being crippled when working on systems where I am a
guest.

Column select
-------------
Use visual block editing!
Ctrl+v

Search and replace
------------------
Case sensitive `/pattern`

Case insensitive `/\cpattern` `/pAtTeRn\c`

Next result (forward) `n`

Next result (backward) `N`

Search for current word `*`

Find/replace file `:%s/old/new/g`

Fine/replace line `:.s/old/new/g`

Replace spaces with newlines `:%s/ /\r/g`

Insert mode
-----------
`i` enters insert mode at before current character position

`A` enters insert mode at end of current line

`I` enters insert mode at beginning (first non-whitespace) of current line

`o` enters insert mode by opening (inserting) new line below

`O` enters insert mode by opening (inserting) new line above

###Digraphs
Digraph is two characters used to enter a single character, such as one not
found on a standard US keyboard.

`Ctrl+k` is used to start a digraph.

Accent with '
`Ctrl+k a '` gives `á`

Tilde with ~
`Ctrl+k n ~` gives `ñ`

Inverted with I
`Ctrl+k ! I` gives `¡`;
`Ctrl+k ? I` gives `¿`

Greek with *
`Ctrl+k a *` gives `α`;
`Ctrl+k D *` gives `Δ`

Formatting
----------
Break long line `gqq`

Change (delete) in quotes `ci"`

Change (delete) in parenthesis `ci(`

Lower case line `guu`

Lower case word `guw`

Upper case line `gUU`


Other
-----
File explorer `:Ex`

Close buffer `:bd`

Move between splits `Ctrl+w Ctrl+w`

Navigate to start/end of parens/braces `%`

Navigate to end of line `$`

Navigate to end of file `G`

Navigate to beginning of like `0`

Navigate to beginning of C block `[{`

Navigate to end of C block `]}`

Repeat last : command `@:`

Repeat last normal mode command `.`

Lookup man page `K`

Delete character `x`

Delete to end of line `d$`

Delete to end of file `dG`

Scripts
=======

ANSI color escape sequences
---------------------------
Script to highlight ANSI escape sequences as colors (useful for browsing logs
with color):
http://vim.sourceforge.net/scripts/script.php?script_id=302
