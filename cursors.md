Multiple Cursor Editing
=======================
Zed has powerful multiple cursor support.

Block selection (mouse)
-----------------------
Hold down `Alt` and select a block of text, now any edit commands will be
applied to the block as a whole.

Adding Cursors
--------------
Zed supports editing with multiple cursors. These are relevant commands to use this feature:

* `Cursor:Multiple:Add Above`/`Cursor:Multiple:Add Below`: adds an extra cursor on the line above or below the current at the same column.
* `Cursor:Multiple:Add Above Skip Current`/`Cursor:Multiple:Add Above Skip Current`: moves the most recently created multiple curson up/down by one row.
* `Cursor:Multiple:Add At Previous Instance Of Identifier`/`Cursor:Multiple:Add At Next Instance Of Identifier`: adds another cursor at the next/previous occurrence of the identifier under the cursor (useful for easily renaming a local variable or function).

#protip
-------

Zed does not have a find and replace feature. It doesn't need it, the Zed way
of doing it is searching for an instance of the string (or selecting it), then
adding cursors on other instances using `Cursor:Multiple:Add At Previous Instance Of Identifier` and `Cursor:Multiple:Add At Next Instance Of Identifier`, and then simply typing the replacement.
