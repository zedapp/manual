Navigating a Project
====================

So, you now opened your first Zed project. Now, how do you navigate it? Depending on the choice you made in the initial screen that asked you what UI mode you preferred, you either now see a file tree along the left or not. If you chose the "Chromeless" option, don't panic. In whichever mode, you can always open the file tree using the `Navigate:File Tree` command (`Command-T` on Mac, `Ctrl-T` on other OSes). Another way is using the `Navigate:Goto` command (`Command-E` on Mac, `Ctrl-E` on other OSes). If you don't want to navigate to a specific _file_, but instead want to navigate to the declaration of a particular symbol (e.g. method or class) you can use `Navigate:Lookup Symbol` (`Command-J` on Mac, or `Ctrl-J` on other OSes). We'll go each of these options briefly.

Goto
----
Goto is Zed's powerful UI and preferred way to quickly navigate between files, within files, navigating between symbols and even _creating_ files. When activated using `Navigate:Goto` a box appears that you can type into. Along the bottom search results appear. When the Goto input box is empty, the list of results is ordered showing the most recently opened files first. This makes it a good way to navigate between a few files that you have to switch between quickly.

When you type a search phrase, results will match it against all files in your projects as well as symbols as follows:

* Symbols: the phrase has to match a symbol's prefix (e.g. `abc` matches a symbol `abcde`, but not `defabc`).
* Files: file names are matched in a fuzzy way, if the phrase appears as a substring of a path, it will rank higher than when characters are spread accross the path name.

There are a few special search phrase _prefixes_ that change the way the list is filtered:

* `/` starting your query with `/` only matches paths with your query as
  prefix. Using `/` within a query means that the part before the `/` should be   part of a directory name.
    * Example: `/mode` will match `/mode/bla.txt`,  but not  `/mymode.txt`. And `mo/javascript.js` will match `/mode/javascript.js`, but not `/test/javascript.js`.
* `:` starting your query with `:`, or using `:` within your query following a number, will jump to the line number that succeeds it.
    * Example: the query `:10` will jump to line 10 of your current file. The query `mod:10` will jump to line 10 of the first match of the `mod` query.
    * Shortcut: `Command-L`/`Ctrl-L`.
* `:/` starting your query with `:/`, or using `:/` within your query following a search string, will jump to the first match of this string with a file.
    * Example: the query `:/hank` will search for "hank" in your current document.
    * Shortcut: `Command-F`/`Ctrl-F`.
* `:@` starting your query with `:@`, following a search string, will jump to the first definition of a _symbol_ matching that search string in the current file.
    * Example:, the query `:@toString` will jump to the defintion of the `toString` function or method. A shortcut to this functionality is `Command-R`/`Ctrl-R`.
    * Shortcut: `Command-R`/`Ctrl-R`.
* `@` starting your query with `@` following by a search string will match symbols defined in the whole project.
    * Example: the query `@toString` will show all definitions of `toString` functions and methods in the current project.
    * Shortcut: `Command-J`/`Ctrl-J`.

File tree
---------

If you're new to a project, or are just a tree-loving person, the tree is a good way to navigate a project. Run `Navigate:File Tree` and the file tree will apear on the left and have focus. You can expand and close nodes using the mouse and select a file to open it. If you prefer to use the keyboard, you can do so as well:

* `Up`: move up a node in the tree.
* `Down`: move down a node in the tree.
* `Right`: expand a node in the tree.
* `Left`: collapse a node in the tree.
* `Enter`: open the selected file.
* `Escape`: close the tree (depending on your UI configuration) and move focus back to the editor.

Depending on your initial UI layout choice, your tree may always be visible or not. To switch between these options use the `Configuration:Preferences:Toggle Persistent Tree` command.

Creating files
--------------
Creating a file in Zed is equivalent to navigating to a non-existing file using Zed's Goto feature. Simply type in a path (starting with `/`) relative to the project root that you want to create and press `Enter`. Zed will even create any parent directories that do not yet exist for you.

Do you want to create a file in the same directory as the current file you're editing, use the `File:New` command (`Command-N`/`Ctrl-N`), this will automatically prefill Goto with the directory of the currently active file so you just have to type in the file name.

Back
----
Want to go back to your previous manual topic? Use Goto! The previous topic will be listed at the top.
