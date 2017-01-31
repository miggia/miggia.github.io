---
layout: post
title: "Hand coding Creo Parametic mapkeys"
date: 2017-01-27
---

Creo Parametric mapkey files can be crafted by hand.
The syntax of the commands is that of the Creo "macro language". However Mapkey files have some differences with respect to trail files, that are somwhat simpler and easier to read.

A list of rules to be respected when writing mapkeys is given hereafter: 

1. all mapkeys must be preceded by an empty line or by a line ending with the `;` character
2. the first line of the mapkey shall start with the string `mapkey <mapkey_name_here> `
3. all but the first line must start with the string `mapkey(continued) `  (be careful not to forget the trailing space)
4. all mapkey lines shall end with the `\` character
5. all mapkey commands start with the `~` character and end with the `;` character
6. the maximum string witdth in the mapkey file is 96 columns; commands or file names that are longer shall be broken down in two lines.
7. mapkey labels can be inserted with the `@MAPKEY_LABEL<label_string_here>` string where `<label_string_here>` shal be substituted with the desired mapkey label.
   This string will show up TODO

### file paths

Relative file paths are allowed and interpreted correctly

Subfolders are accessed with double forward slash characters (`\\`).
For example the path `C:\folder\subfolder\subsubfolder` needs to be referenced as `C:\\folder\\subfolder\\subsubfolder`

### linebreaks

1. to break a mapkey line identify a space in the command/arguments sequence that occurs before the 96th column limit
2. add a `\` character at that point
3. move remaining text to the new line, and prepend to the text in the new line the string `mapkey(continued)`

#### examples

the following sequence of commands 

```
mapkey(continued) ...
mapkey(continued) ~ Update `file_open` `Inputname` mapkey(continued) `folder\\subfolder\\subsubfolder\\minimal_tree.cfg`;\
mapkey(continued) ...
```

can be safely broken down as

```
mapkey(continued) ...
mapkey(continued) ~ Update `file_open` `Inputname` \
mapkey(continued) `folder\\subfolder\\subsubfolder\\minimal_tree.cfg`;\ 
mapkey(continued) ...
```

### ...if it doesn't work

Most often hand-crafted mapkeys won't work at first.
Since no debugging tools are avialable getting them to work can be tricky.
Follows a list of points to check: 

1. a space character is present after the mapkey name
2. all lines but the last end with the `\` character
3. all commands are preceded by the ` ~ `  strin and followed by the `;` character (note the spaces)
4. all lines but the first, the last and broken lines end with the `;\` characters (consequence of points 2 and 3)
5. all mapkeys are called with the `%` symbol only (no `~` characters before  `%` )

### further thoughts

The rules described above are consistent and can easily be automated with scripts.
An intersting approach is to use the MS Windows powershell scripting language (more details on this in a coming post).