Zed Projects
============

Zed is an editor based on projects. When you do a fresh Zed install, a few project-like options will be available, depending on the version of Zed these may include "Local Folder", "Dropbox Folder", "Remote Folder", "Github Repository", and "Manual".

Editing Local Files
-------------------
To edit the files in a folder on your local hard drive pick "Local Folder". A directory picker window will pop up. Zed remembers the most recently opened folers in its project listing (under the "Recently Opened" heading), so they're easy to get to later.

Editing Files on Dropbox (Chrome App only)
------------------------------------------
To edit files on Dropbox, select "Dropbox Folder", login with Dropbox and select the folder to edit. Similar to local folders, the most recently edited Dropbox folders are also listed under "Recently Opened."

Github Repository
-----------------
When selecting the github repository option the first time, you will be guided through the process of creating a Github token and entering it into Zed for authentication. After that you will be presented with a list of all your public and private Github repositories. Alternatively, you can paste in a Github repository URL in the search box at the top. After selecting a repository you choose a branch to edit, after that you can start editing. Edits are kept locally until you run the `Version Control:Commit` command, which will allow to see any changed files, enter a commit message and commit the changes back to Github.

Renaming a Project
------------------
By default Zed will use a project's path, or part thereof as a project name. The project name appears in the editor's title bar as well as in the recent projects list. To rename a project, you can do so from within the editor using the `Project:Rename` command.

Deleting a Project
------------------
If you like you can manually delete projects from the list of recent projects simply by having the project highlighted and pressing the `Delete` key.
