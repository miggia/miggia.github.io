---
layout: post
title: "Converting Creo Parametic files from Educational to Commercial"
date: 2017-01-17
---

Research institutions, like the one to which I belong, are normally eligible for Educational Creo Parametric licenses. With respect to their commercial counterparts these licenses are generally more powerful (as they allow to use most Creo modules) and are generally more affordable.

However files generated with an Educational license cannot be opened with a commercial license and cannot be used for commercial purposes.

What sometimes happens though is that Companies having commercially licensed Creo Parametric copies need to open files generated with the Educational version.

To solve this issue files can be converted with a specific EDU/COMM converter module that is sold by PTC.

To convert a file all you need to do is to activate the EDU/COMM, that is generally available as floating module, and to save a backup of a given file.

## tips & tricks: converting drawings

A problem that is commonly encountered when needing to convert to Commercial large assemblies is that of converting multiple component files and their drawings. Indeed if an assembly contains many custom parts, and several sub-assemblies, each component file and its drawing file needs to be opened and saved separately.

There is however a simple workaround that allows to greatly reduce the amount of work needed for the conversion. This method is based on the `Save a Copy` command and its capability to save drawings when parts or assemblies are saved.

To do this follow the steps described hereafter

1. Activate your EDU/COMM converter
2. Open the assembly you want to save
3. Issue the `Save a Copy` command and make sure the `Copy Drawings`checkbox in the `Associated Items` section is checked
4. Select all components from the model tree
5. Save a copy of all files with a temporary suffix (e.g. `_TEMP`) by adding a string in the `Use Suffix` textbox in the `Name / Number Generation` section
6. Open the newly saved assembly and repeat the `Save a Copy` operation
7. Select all components from the model tree
8. Save a copy of all files and remove the added suffix by selecting `Use Template` in the `Name / Number Generation` section, and exploitng the `*` wildcard (e.g. `*_TEMP = *` in this example)

The trick is basically to run `Save a Copy` twice (once the EDU/COMM converter has been activated active), first to save all files with a new name, and secondly to restore their original name. This can be done exploiting the `Use Template` in the `Name / Number Generation` section

### caveat: family tables

The method above tends to create issues if family table components are used in the assembly. This is because once the first `Save a Copy` operation has been performed, a new component is generated.
However the code of this new component cannot be restored because a family table instance with that name is already present.

The solution to this issue is to exclude components belonging to family tables from the `Save a Copy` operation by selecting `Reuse` in the `Action` column of the `Save a Copy` `Model tree` dialogue.

If the assembly is big most likely it will contain lots of family table instances and setting all of the to `Reuse` would be extremely time consuming. An efficient way to solve this issue is to exploit the `Advanced Search` option to select them all at once provided you have a way to filter out these components (e.g. we use a component parameter that allows us to filter custom ands commercial components).

To do this:

1. click on `Select ` in the `Save a Copy` `Model tree` dialogue
2. then click on `Advanced Search`
3. apply the search criteria in the `Advanced Search` dialogue
4. set all the selected components to `Reuse`

