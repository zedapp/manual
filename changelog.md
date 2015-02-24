Changelog
=========

1.1.0
------

* New project type: Zedd Folder (for editing of local and remote files), see http://zedapp.org/zedd for more details on how and when to use this.
* Support for running external tools in Zedd projects as well as Standalone local folder projects. This enables new commands and packages like:
    * `Tools:External:Insert Command Output`
    * `Tools:External:Filter Selection Through Command`
    * Package (included by default): git-tools which exposes commands like:
        * `Git:Grep`
        * `Git:Add`
        * `Git:Commit`
        * `Git:Diff`
        * `Git:Status`
        * `Git:Blame`
* Chrome App only: ability to just open one or a few files (rather than a whole folder)
* Zed version number now visible in project picker
* Theme split: you can now configure your "window theme" and "editor theme" separately (by TheKiteEatingTree)
* Multiple sandboxes: many tasks (such as checking, code completion) now happen in separate sandboxes (= threads) to speed up certain tasks. Sandboxes are automatically cleaned up after a timeout.
* Better handling of projects that are no longer accessible (removed from recent project list when opened and alert window)
* Modes:
    * JSX mode (React) updated to 0.12


1.0.1
-----

* Many bug fixes
* Upgraded to latest ACE, with improved Vim mode and other improvements
* Window size persistence tweaks
* Internal: old symbol databases are now cleaned up (after 2 weeks)
* Auto symbol indexing fixed
* Modes:
    * XML: Fixed beautify feature
    * New Elixer mode
    * New Elm mode
    * HTML: now also opens .htm files
    * Erlang: now also used for header files (opie4624)

1.0.0
-----

* Unified UI: the separate project picker window is gone and has been integrated into editor windows (using same theming etc.). Similarly the first run, dropbox project, github picker windows have all been integrated as well.
* The "Notes" space has been removed, due to too frequent data loss for users, we recommend to just use a local folder instead. If you were using Notes before and would like to access it still, enter "syncfs:" in the project picker search box and press Enter.
* New preferences GUI offering a more friendly way of changing preferences, access it via `Configuration:Preferences` (`Command-,`/`Ctrl-,`)
* Window restore on relaunch: All windows are now restored after Zed quit (`Zed:Quit`) and restart.
* Native window chrome (title bar) is now used in the standalone version of Zed as well as the Chrome App version on Linux.
* Syntax highlighting added for TeX/LaTeX, Ada, Assembly, Cobol, diff files, FORTH, .gitignore, Jade, Lisp, Objective-C, Pascal, R, Scheme, SQL (including MySQL and Postges flavours), SVG, Tcl, Typescript, Vala, and a bunch more, some of which I never heard of — if Ace supports it, now we support it too (by lalomartins)
* Standalone: Windows version now uses Zed icon on desktop.
* Default editor window size increased to 1024x768
* Linux window size restore improved.
* Fixed mouse UI UX issues (dragging and dropping of text now supported) (by nightwing)
* New commands:
    * `Navigate:Last Edit Point` (useful to go back to last location you were editing after jumping to a symbol)
    * `Window:List` (lists all open Zed windows and allows you to quickly jump between them)
* Keyboard shortcuts have been refactored here and there to better support non-Mac OSes (ChromeOS, Linux, Windows) -- check the command list when a keybinding you were accustomed to no longer works.
* Fixed Coffeescript display bug (by nightwing)

0.13.0
------
Big new features in this release:

1. Github support: Support for opening, editing to Github repositories without the need to clone them -- right from Zed.
2. Embedded web server: serve (static) files right from Zed.
3. Zedrem change: current Zedrem users using last version's userKeys: user keys are now no longer stored in preferences, but instead in a token store outside the Configuration project. Your user key will have changed. For details, see below.

Here's the full list of changes:

* Github support: There's now a "Open Github Repository" item in the project picker. The first time you'll click it it'll ask you to create a Github token that it'll save (outside the Configuration project). After this a repository picker will appear, but you can also paste in full Github urls immediately. After picking a repo it'll ask you to pick a branch to edit.
    * Changes made to a Github project are saved locally on your machine into an IndexedDB database only. To commit the changes to Github, use the `Version Control:Commit` command (also available in the "Tools" menu if you have menus enabled).
    * You can reset any changes you made locally using the `Version Control:Reset` command.
    * You can create a branch (that'll open in a new window) using `Version Control:Create Branch`.
* Zedrem: configuration changes:
    * the "zedrem" key under preferences in the Configuration project is now _ignored_, you can remove this key safely.
    * User keys are now stored in a token store (as are the Github tokens), to retrieve your zedrem userKey run the `Zedrem:Get User Key` command.
    * If you like you can generate a new user key using `Zedrem:Generate New User Key`, a Zed restart will be required for this change to take effect.
    * The project picker now shows the status of your connection to your selected zedrem server at the bottom of the screen.
* Embedded Web server -- serve files right from Zed (works both in Chrome App and Standalone): this is available both as sandbox API (so you can implement your own servers -- see zefhemel/zcms for an example) and with a default static file server you can run out of the box.
    * Start static file server using the `Tools:Static Server:Start` command, this will also automatically open your browser. A port is automatically assigned.
    * Stop static file server using `Tools:Static Server:Stop`. The server will also automatically stop when you close your editor window.
* Drag and drop of binary files: this is not an advertised feature at all, but you can actually drag and drop files onto a Zed editor window and it'll "upload" them to your project. This now also works correctly with binary files, such as images.
* Currently open files (open in some split) will now appear in your Goto file list (although at the very bottom), Zed will do some session switcharoo to make this work correctly.
* Modes:
    * Improved C++ symbol indexing support (by cessen)
    * Dockerfile mode (syntax highlighting only)
    * Ruby: behavior support (auto-inserts matching braces etc.)

0.12.1
------
This release has a much improved flow for editing files remotely using zedrem. Rather than having to copy and paste URLs every time, you can now pass in a user-specific key to the zedrem command and windows will automatically open up when you use zedrem.

* Zedrem: The `zedrem` binary now takes an optional `-key` flag where the user key can be passed in. This key is automatically generated (see below) and can be requested using the `Configuration:Zedrem:Get User Key` command. When passed in, edit windows will automatically appear when you run zedrem.
* Zedrem: the ~/.zedremrc file (that is: the .zedremrc file in your $HOME directory) has been extended to have a `userKey` entry in the `[client]` section, this is useful if often editing files on the same server and not wanting to pass in the user key every time.
* To support the above there is now a `zedrem` preference in the Configuration (under preference). By default a server is configured there (remote.zedapp.org over SSL) and a `userKey` generated. The project picker will establish a persistent websocket connection with this server to enable the behavior described above.
* Zedrem: ownership of files is now preserved.
* Modes:
    * Improved C++ symbol indexing (by cessen)
* Key bindings:
    * Mac: Alt-Delete now added as alternative to Alt-D (by 11684)
* Zed now works on the Chrome Beta channel again (Chrome 37)
* Symbols are now listed in order that they appear in files, rather than based on length.
* Mutliple cursor bug fixes: moving and copying lines up and down now works with multiple cursors, as does whitespace trimming.
* Standalone: no more crashes with the splash screen.

0.12.0
------
This one's a big release, both internally (the whole code base has been refactored to use ES6-promises instead of node.js-style callbacks) and externally: there's now an optional "traditional" UI mode that shows you a persistent file tree on the left and a menu bar along the top. In addition, there's now a basic UI for managing snippets.

* First-run screen that asks you to pick a UI layout. This is fully configurable later on, via:
    * New `persistentTree` preference that, when enabled, shows a file tree along the left.
    * New `showMenus` preference that shows a menu along the top with a (curated) list of common commands (and their key bindings).
* Snippet manager (`Snippet:List`, `Snippet:Add`) shows and adds snippets to the mode of the currently active session.
* `File:New` command (bound to `Command-N`/`Ctrl-N`) that opens the Goto UI with the directory of the currently active file prefilled.
* ZPM and Snippet manager use special "Zed UI" Ace mode that highlights "buttons" more like buttons, so you can tell they're clickable.
* Language modes can now have a `completionTriggers` key with characters that should automatically trigger code completion, e.g. `.` for JavaScript or `->` for PHP. And as a result...
* Code completion now automatically triggers after typing a `completionTriggers` sequence of characters (this can be switched on/off with the `autoTriggerCompletion` preference).
* Big Manual overhaul
* Modes:
    * Scala symbol indexing
    * PHP follow complete support
    * Clojure follow complete support
    * Gherkin mode (by lalomartins)
* Themes:
    * Base16 theme (by farnoy)

0.11.5
------
* Modes:
    * Ruby: symbol indexing
    * Python: improved symbol indexing
    * C: symbol indexing
    * PHP: improved symbol indexing
    * Java: symbol indexing
    * C#: symbol indexing
    * GLSL syntax highlighting
    * Stylus syntax highlighting
* Two new packages made part of the default distribution:
    * follow-complete: offers quasi-intelligent completions for `x.y` property accesses/method calls for many languages (currently enabled for JavaScript, Python, Ruby, Go, Java, C#, Groovy, Lua, Nix, Rust and Scala)
    * bracket-check: checks matching brackes (currently enabled for Clojure, Go, Dart, Python, Ruby, Java, and C#)
* Local (Chrome) directories with more than 100 files/directories did not show up completely before, this is now fixed (by farnoy)
* Projects are automatically indexed (for symbols and code completion) the first time they are opened, you can do this manually with `Tools:Index Project`.
* Search project now only searches known file types and does so more sequentially, which should prevent crashes
* Key bindings:
    * Default keybinding for `Find:Next` on Linux/Windows/ChromeOS is now `Ctrl-G`, and `Find:Previous` is now `Ctrl-Shift-G`.
    * `Nativate:Reload Filelist` is now bound to `Command-Shift-L` on Mac and `Ctrl-Shift-L` on Windows/Linux/ChromeOS as well as `F5` on both.
* Dotfiles (files starting with `.`) now appear in the file list, except those defined in `gotoExcludes` (by default `.git`)
* Goto matching algorithm tweaked, now also does fuzzy matching again (although with a lower score).
* File renaming fixes (by TheKiteEatingTree)

0.11.4
------
* Goto improvements:
    * Goto (Ctrl-E/Command-E) now also includes matches from the symbol index (without having to use the `:@` or `@` prefix)
    * New fuzzy matching algorithm:
        * Now also searches file directory names by default.
        * Character sequences now have to match exactly, spaces can be used as wildcards. E.g. "bcd" matches "abcde" but not "abccde", however "bc d" will match "abccde".
        * Scoring is now based on how close the pattern match is to the end of the path, the closer to the end, the higher the score. This favors file name matches over directory name matches, which is usually what you want.
* Project search improvements:
    * Now integrated into goto (Ctrl-Shift-F/Command-Shift-F)
    * New query syntax: `searchphrase [-flags] [filepath pattern]`
      for example: `hello` or `hello *.js` or `hello -i` (case insensitive search) `he*llo -ie /docs/*.md` (case insensitive regex search).
      Supported flags: `-i` (case insensitive matching) and `-e` (regex match).
* Batched undo: you no longer have to run undo for every character, certain operations (including typing and deleting) are now batched up.
* Better behavior when "closing" a split (going from 2 to 1 splits): the split left will now contain the file in the active split.
* Bug fix: Fix window positioning after restore
* Bug fix: Better recovery from broken configuration
* Bug fix: No longer show stacked "file changed" dialogs for each change
* Sandbox API:
    * `zed/http` API now also has POST, PUT, DELETE etc. support and returns not just content, but also headers (by akoenig)
    * `zed/preview` API now supports opening the preview split (by akoenig)
* Mode:
  * Clojure/ClojureScript mode: symbol indexing and better indenting

0.11.3
------
* ZeDB: a simple abstraction layer on top of IndexedDB. Packages and other sandbox code can create their own data stores and indexes (via the `databases` key in configuration) and read, write and query that data quickly. This system is current primarily used for symbol indexing and code completion (see below).
* Complete rework of generic project indexing system, now storing symbol information in IndexedDB for faster retrieval (than the `/tags` file in ctags format that it used to use).
* Support for full function signatures and icons in symbol list (`Command-R`/`Ctrl-R`) and code completion for certain languages (JavaScript, Go, others still have to be updated)
* General-purpose regex-based symbol indexer allows to add basic symbol indexing to modes without writing any JavaScript (see Go and JavaScript mode for examples).
* Additional multi-cursor commands (`Cursor:Multiple:Add Above Skip Current` and `Cursor:Multiple:Add Below Skip Current` by thebishopgame)
* Standalone:
    * No longer crashes when an exception occurs
    * Do not save window position for minimized windows (by nightwing)
* Modes:
    * New matlab mode (by timothyrenner)
    * Markdown: disable strip whitespace (by robru)
    * Handlebars mode (by chenxsan)

0.11.2
------
* New "Edit in Zed" Chrome Extension for Zed Chrome version: adds a little on-hover Zed icon to textareas on any website in Chrome, when you click it, you can edit the contents of this text area using Zed. [Download the extension from the Chrome Store](https://chrome.google.com/webstore/detail/edit-in-zed/dpkaficlkfnjemlheobmkabnnoafeepg)
* Usage data colleciton: upon first launch you will be asked to agree to collect anonymous usage data. This helps us to see what features (e.g. language modes) people are using and what to improve.
* ZPM fix github package support (by conradz)
* Fix: code beautification (formatting) for selection works now
* Scroll past end of editor preference (by TheKiteEatingTree)
* Modes:
    * JSX (react.js) mode now has JSHint support
    * Ruby mode now also works on Vagrantfile
* Various minor bug fixes (by robru and others)

0.11.1
------
* New auto save that always saves (which should be friendlier for people using build systems with file watchers):
    * When switching between splits
    * When switching between files
    * When the editor loses focus
    * And optionally: after a x number of milliseconds of inactivity (set to `saveTimeout` to 0 to disable this)
* Commands to move splits around: (`Split:Move To *`)
* New splits now receive focus automatically
* Version number now appears in project picker
* Fixes to file tree (by eltuerto)
* Sandbox messages now appear in zed::log for standalone version
* Configuration now uses JSON5 format (which supports comments etc.)
* Fix to trim remote URLs when pasting (by surma)
* ZPM auto update fixes
* Scroll past end preference (`scrollPastEnd`) (by TheKiteEatingTree)
* Modes:
    * PHP mode now includes a parser and reports parse errors
    * Livescript mode (by maninalift)
    * Groovy mode (by calebmpeterson)
    * JSX mode
    * Improved Markdown preview styling (by ghotsla)

0.11
----
* Standalone:
    * First release of Zed standalone! I'm sure there will still be bugs, please report them on github when you find them.
    * Open individual files or directories from the command line by calling "zed <dir>" or "zed <file>". On Mac, please install the CLI tools via the `Tools:Install Mac CLI` or the native Tools menu in the Mac app to use this.
* Multiple keybindings support. That's right, we now have Vim and Emacs keybindings. Use the `Configuration:Preferences:KeyBinding:*` commands to switch between them. (by nightwing)
* New commands:
    * `File:Copy` (by iElectric)
* Language modes:
    * Python now has CTags indexing (by ghotsla)
    * Ability to switch off certain CSSLint options (by conradz)
* Bugs fixed:
    * Fixed a bug where when the project history is empty, no new projects are added.

0.10.2
------
* Refactoring of Zed core codebase to use Architect plug-ins, making it easier to create the Zed standalone (without Chrome dependency) version.
* New commands:
    * `Help:Commands` (bound to F1 by default) gives you a context-sensitive list of all available Zed commands in your current mode, documentation (if available) and current keybinding (by robru)
    * `Tools:Document Statistics` gives some useful stats about your current document (word count, line count, character count etc.) (by robru)
* Sandbox updates:
    * Added sandbox commands to call goto and invoke arbitrary other commands (by robru)
    * Added a "click" handler for the sandbox.
* Language modes:
    * Separate SCSS mode (by wpapper)
    * Scala mode (by netzwerg)
    * Mode is now set for files without a file extension based on Unix shebang line, e.g. #!/bin/bash uses bash mode (by robru)
* Made configuration loading more robust, even if user.json contains JSON parse errors.
* Minor fixes of the whitespace trimmer (by robru)
* Indent on paste fixes (by TheKiteEatingTree)
* Some minor updates to the manual (particularly the config.md documentation)

0.10.1
------
* Important: all sandbox APIs (and packages) have now been refactored to use JavaScript-native promises
* Sandbox commands can now request inputs like "text", "cursor" which will inject values directly into the first argument argument to the command. (by robru)
* The JSON and JavaScript modes have been extracted into Zed packages and will be kept up-to-date automatically outside the Zed release cycle
* Zed theme CSS will now automatically be updated as you edit it (by TheKiteEatingTree)
* Automatically indent on paste (by TheKiteEatingTree)
* Case insensitive find (by TheKiteEatingTree)

0.10
----
* New skinnable window chrome! Slightly more compact and generally more awesome. The edit bar is gone and has been incorporated with the title bar now.
* New and improved whitespace stripper that lives in the sandbox (by robru)
* Added "internal" flag to commands to not show commands only useful for internal use
* Window commands (`Window:Close`, `Window:Minimize` etc.) (by robru)
* Various new sandbox APIs (by robru)
* New `/user.css` file in Configuration project to override any editor style you like (independent of theme), changes apply on save (by TheKiteEatingTree)
* Moved all preference toggling commands to sandbox (by robru)
* New globalAutoRevert preference to automatically reload changed files without asking (by robru)
* Initial implementation of continous code completion (not bug free yet and disabled by default under `continuousCompletion` preference).
* Various bug fixes


0.9.4
-----
This is a release with some major new features, but they're not well documented and a bit hidden, so we'll wait a bit to expose them more seriously. I'm very happy to see that an increasing number of people are starting to contribute, in this release: TheKiteEatingTree, robru and dsrw. Thanks all!

* ZPM! We now have a package manager built-in, more information, and more heavy use of this on this in future releases (by TheKiteEatingTree)
* Sandbox code can now use CommonJS syntax without the require.js boiler plate (see new version of included sandbox extensions)
* Minor theme tweaks
* New `zed::log` document that gives you access to internal Zed (and sandbox) log messages
* Language support:
    * Sass language support (by dsrw)
    * Perl language support
    * Python snippets (by robru)
    * JSHint fix where the wrong word was underlined when using tabs (by TheKiteEatingTree)
* Selected line sorter command (by robru)
* Ability to move Configuration project to local folder (via `Configuration:Store in Local Folder`)
* Trim Whitespace on empty lines toggle command (by robru)
* Key binding tweaks (by robru)

0.9.3
-----
* Added RHTML mode (thanks Scott Wadden!)
* Added the ability to add extra globals for JSHint (thanks Bartek Szopka!)
* `zed::log` document that gives some information of what Zed is doing behind the scenes (eventually this will also contain sandbox messages).

0.9.2
-----
* Bound `Find:All` to `Ctrl-Alt-F`

0.9.1
-----
* Improved intro text when first entering the Zed editor (previously the "Zed Cheatsheet"
* Bind opening the tree to `Ctrl-T` on Linux/Windows/ChromeOS
* Use font set in preferences for context bar end edit bar
* Find:All command to put cursors on all instances of the current selection

0.9.0
-----
* Theme overhaul: themes are now part of Zed itself (they were part of ACE before), created using configuration files in the Configuration project. Users can now create custom themes as well from within the Configuration project. A theme can, in theory, theme any element of the Zed UI (but for now, just theme the editor).
* Created a custom dark Zed theme, which is now the default.
* Moved the extension sandbox into a Chrome `<webview>` which lives in its own process and therefore no longer blocks the editor event loop.
* Trying to infer position information from JSHint messages, thereby underlining warnings and errors inline rather than just with a gutter marker.
* Configuration project now has a README
* New `gotoExclude` preference with a list of patterns (use `*` as a wildcard) for files to exclude from goto (and project-wide search).
* Fixed bug where Zed would always say "No preview available" even when it was available.

0.8.5
-----

* Adds support for "Tools:Fix", a generic infrastructure to run arbitrary commands that can "fix" code or text (e.g. fix a spelling mistake, offer thesaurus based word suggestions, rename a variable etc.). Fix is bound to `Command-Enter`/`Ctrl-Enter`
* Adds a fixer for the spell checker
* Faster editor load: no longer analyzes all open files on editor open, but does so on demand.
* Goto panel now supports PgUp and PgDown as well as holding Up/Down/Tab/Shift-Tab keys to keep scrolling.

0.8.4
-----
* Added better PHP support (builtins, ctag indexing)
* Implemented file locking to avoid the file watcher picking up a changed file while it is being written
* Replaced showdown with pagedown for Markdown previewing
* Renamed `events` to `handlers` in configuration files
* Tree pop-up and disappear fix (thanks TheKiteEatingTree!)
* Added `check` handler to allow multiple extensions to contribute to the inline error markers
* HTML/CSS beautifiers now take tabSize preference into account (thanks TheKiteEatingTree!)
* Added a super initial version of a spell checker (disabled by default for now, enable by switching the `spellCheck` preference to `true`), no correction suggestions yet, US English only.

0.8.2
-----
* Initial implementation of Chrome-extension-to-extend-Zed support. Allowing users to write Chrome extensions that extend Zed's functionality. This feature is still in development.
* Tweaking of manual (added "Projects" page)
* Tweaked default project names slightly, tweaked font on non-Mac OSes of project picker window

0.8.1
-----
Purely a Chrome Web Store SEO release (different application name and description).

0.8.0
-----
* This release drops "zed --local" support, please use Chrome 31's+ Local Folder support instead
* File creation behavior change: when accidentally creating a file, e.g. by navigating to `/whoops` and pressing enter, the file is now only created once you type something in it. If you navigate away immediately, the file will not be created.
* Tweaked hints when about to create a new file (now becomes an action result)
* Added support for deleting and renaming projects (delete by pressing `Delete` in the project list, rename via the Project:Rename command).
* Bumped default maximum number of recent folder preference to 10.
* Some initial documentation on the Zed internals in the manual.

0.7.2
-----
Improved project navigation. The project list can now be navigated using your keyboard: Use `Up` or `Shift-Tab` to go up and `Down` or `Tab` to go down in the list and `Enter` to open the selected project. Type in the filter box to filter the project list.

The project list can be brought up from any Zed editor window using the `Command-Shift-O`/`Ctrl-Shift-O` key quickly.

0.7.1
-----
Replaced goto filter box implementation with an ACE editor implementation which should be _substantially_ faster, especially in large projects.
