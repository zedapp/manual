Editing Basics
==============

Zed uses conventional keys for editing text. When you press a character, e.g. 'a' it will be inserted. Similarly, the arrow keys move the cursor around. Below is a list of commands that may be less obvious, many of these will have keyboard shortcuts associated with them, but they depend on your configuration. To find out if there's a keyboard shortcut associated with a command, enter its name in the Execute Command UI (`Command-.`/`Ctrl-.`) and see if a shortcut is listed along the right of the listing.

Basic cursor movement
---------------------

Beyond the obvious up, down, left, right, page up, page down, here are some interesting cursor movement commands:

* `Cursor:Center`: centers the cursor on the screen vertically.
* `Cursor:File Start`/`Cursor:File End`: moves the cursor to the start resp. the end of the file.
* `Cursor:Line Start`/`Cursor:Line End`: moves the cursor to the start resp. the end of the line.
* `Cursor:To Matching Brace`/`Select:To Matching Brace`: moves/selects from the brace the cursor is currently at to the matching one.

Zed also supports vim-style cursor movement. These keyboard combinations have the advantage of not having to move your hand to your cursor keys to move around. If you're familiar with vi or vim, they are generally the same keys you always use to move around together with the `Alt` key. Supported are:

* `Alt-h`: move cursor to the left
* `Alt-j`: move cursor down
* `Alt-k`: move cursor up
* `Alt-k`: move cursor to the right
* `Alt-w`: move cursor one word to the right
* `Alt-b`: move cursor one word to the left
* `Alt-0`/`Alt-^`: move cursor to the start of the line
* `Alt-$`: move cursor to the end of the line
* `Alt-Shift-g`: move cursor to end of the file

In addition, many of these also work together with `Shift` to use them to select text, e.g. `Alt-Shift-H` selects one character to the left.

If one cursor isn't enough for you, have a look at Zed's support for multiple cursors: [cursors]

Editing
-------

Beside typing in regular characters (letters, numbers, underscores), using backspace and delete to remove characters, and cut, copy and paste (all bound to the usual keyboard shortcuts), Zed supports some more advanced editing commands:

* `Edit:Block Indent`: indents the selected block of text with a tab (or number of spaces). Useful for quickly fixing identation of blocks of code.
* `Edit:Block Outdent` does the opposite of `Edit:Block Indent`.
* `Edit:Complete`: invokes code completion (if succeeding a non-space character, otherwise performs `Edit:Indent`).
* `Edit:Copy Lines Up`/`Edit:Copy Lines Down`: creates a copy (_not_ via the clipboard) of the currently selected lines above/below the selection. Useful when a piece of code needs to be repeated a few times with minor changes. Often used in conjunction with `Edit:Move Lines Up` and `Edit:Move Lines Down` (see below).
* `Edit:Move Lines Up`/`Edit:Move Lines Down`: moves the currently selected up and down. Useful for moving code around a little bit (can often be used a replacement for cut and paste within the same file).
* `Edit:Remove Line`: Removes the current line entirely.
* `Edit:Remove To Line Start`/`Edit:Remove To Line End`: Removes everything from the current cursor position to the start/end of the line.
* `Edit:Uppercase`/`Edit:Lowercase`: upcases/downcases the current selection.
* `Edit:Number:Increase`/`Edit:Number:Decrease`: increases/decreases the integer under the cursor by 1.
* `Edit:Remove Word Left`/`Edit:Remove Word Right`: removes a word to the left/right of the cursor.
* `Edit:Split Line`: splits the currently at the cursor position in two.
* `Edit:Toggle Comment`: comments or uncomments the current line or selection.
