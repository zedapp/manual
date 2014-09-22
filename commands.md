Commands and Keys
-----------------

Every operation in Zed is executed through _commands_. For instance, to delete a character in a file use the `Edit:Delete` command. To move the cursor up use the `Cursor:Up` command. Commands can be run in four ways:

1. By name using the `Command:Enter Command` command (`Command-.`/`Ctrl-.`).
2. Using a keyboard shortcut
3. Using the menu bar
4. By a handler

Running commands by name
-------------------------
The Enter Command UI (`Command:Enter Command`) can be triggered  using `Command-.`/`Ctrl-.`. Similar to Goto you can filter commands in a fuzzy way by typing in part of a command name to filter down the list. Commands that you recently executed by name appear along the top.

Using a keyboard shortcut
-------------------------
Many commonly used commands are already bound to a keyboard shortcut. You can see what these keyboard shortcuts are using the Enter command UI (see above), they appear along the right of the command (if there's any configured). If you have menus enabled (see below) keyboard shortcuts for commands also appear in the menu.

To configure your keyboard shortcuts, have a look at [configuration].

Using the menu bar
------------------
If you have the menu bar enabled (you can toggle the menu bar using the `Configuration:Preferences:Toggle Menus` command), you see a menu bar along the top of your editor's window. This menu is heavily curated, meaning it doesn't include all available commands, but all common ones are there.

Using a handler
---------------
Handers are a piece of configuration that automatically trigger commands when certain events occur. This is for instance how code completion, linting and symbol indexing is implemented. Unless you're interested in developing extensions for Zed, handlers aren't that relevant to you, so you can ignore them. If you are interested, have a look at [configuration].
