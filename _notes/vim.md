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

Replace `:%s/old/new/g`

Replace spaces with newlines `:%s/ /\r/g`

Insert mode
-----------
`i` enters insert mode

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

Other
-----
File explorer `:Ex`

Close buffer `:bd`

Scripts
=======

ANSI color escape sequences
---------------------------
Script to highlight ANSI escape sequences as colors (useful for browsing logs
with color):
http://vim.sourceforge.net/scripts/script.php?script_id=302


