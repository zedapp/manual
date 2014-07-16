Code Completion and Snippets
============================

Zed has an extensible code completion mechanism. Various plugins can provide completion results and the quality/usefulness of the results depend on the language you use. Completion is triggered by pressing the `Tab` key following a non-whitespace character. Completion can also be triggered automatically under certain conditions depending on your configuration.

These are completion engines distributed with Zed by default:

* Word completion: this completer works the same for every file type (including plain text): it finds all words in the current document, and finds results that match the prefix you're completing, ranking more close matches first.
* Symbol completion: Zed includes symbol indexers for many languages, the symbol completer completes your code based on indexed symbols project-wide.
* Snippet completion: Zed comes with some code snippets included for some languages, in addition you can create your own. See the Snippets section below for more details.
* Built completion: certain language modes contain a list of symbols built into the language (e.g. PHP).
* Follow completion: this completion engine is enabled for many languages, but not all. It works best for languages that use a notation like `element.method()` (that is identifier-separator-identifier) and will index occurrences like these to provide the completion `element.method()` after requesting comletion for `element.`

Unline some other editors, Zed has just one key to remember to get code completion: `Tab` it tries to intelligently rank the result to show the result you're looking for up top.

Snippets
--------

Zed comes with some snippets out of the box for some languages (such as JavaScript). However, you can define your own as well. To see the snippets available for the language mode of your currently open file, run the `Snippets:List` command. This will present a UI that lists existing snippets, allows you to edit and remove them (if they're not built in) and define new ones.

Within the snippet you can use special placeholders like ${1} and ${2} as cursor insertion points (which you can jump between using `Tab` after inserting the snippet). You can also define a default value for the placeholder using the ${1:default content} notation.
