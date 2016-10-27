---
layout: post
title: "Automating PTC Creo tasks with trail files"
date: 2016-10-27
---

When working with PTC Creo Parametric one often encounters the situation where multiple files need to be processed, files exported or similar issues. 
An option that is not so well known is that of writing trail files and executing them with the `Run trail file` command.
In this post I'll describe shortly how this can be done.

## What is a trail file?

Every Creo Parametric session records all user input into a trail file.
The trail file can then be replayed to replicate a given user session.
The "syntax" of the trail file is extremely similar to that of Creo Parametric Mapkeys.

The PTC J-Link user guide advises against using this method for 

> Creating or editing the macro string manually is not supported as the mapkeys are not a supported scripting language.
> The syntax is not defined for users and is not guaranteed to remain constant across different
> datecodes of Creo Parametric 
>

Furthermore the syntax is not documented, making it really hard for users

Despite all these premises I have found that writing trail files is a very convenient way of automating tedious tasks.

It is not as elegant as writing Toolkit applications but is much quicker, and I tend to adopt it as the quick-and-dirty way.

## Creo Parametric Macro language reference

As described before PTC does not provide a documentation for the Macro language.

However it is rather simple to "reverse engineer" the syntax by looking at Creo trail files of short sessions where only simple commands are executed.

The macro language "translation" of commonly used commands are reported hereafter.

#### Open file

```
~ Activate `main_dlg_cur` `main_dlg_cur`
~ Command `ProCmdModelOpen` 
~ Update `file_open` `Inputname` `ADD_FILE_NAME_HERE`
~ Activate `file_open` `Inputname` 
```

#### Save as step
```
~ Command `ProCmdModelSaveAs` 
~ Open `file_saveas` `type_option`
~ Select `file_saveas` `type_option` 1 `db_539`
~ Update `file_saveas` `Inputname` `ADD_FILE_NAME_HERE`
~ Activate `file_saveas` `Inputname`
~ Activate `intf_export` `OkPushBtn`
```

#### Saveas pdf
```
~ Command `ProCmdModelSaveAs` 
~ Open `file_saveas` `type_option`
~ Select `file_saveas` `type_option` 1 `db_617`
~ Activate `file_saveas` `file_saveas`
~ Update `file_saveas` `Inputname` `ADD_FILE_NAME_HERE`
~ Activate `file_saveas` `Inputname`
~ Open `intf_profile` `pdf_export.pdf_raster_dpi`
~ Select `intf_profile` `pdf_export.pdf_raster_dpi` 1 `600`
~ Select `intf_profile` `pdf_export.pdf_color_depth` 1 `pdf_gray`
~ Activate `intf_profile` `pdf_export.pdf_launch_viewer` 0
~ Activate `intf_profile` `OkPshBtn`
```

#### Close model and erase not displayed
```
~ Command `ProCmdWinCloseGroup` 
~ Command `ProCmdModelEraseNotDisp` 
~ Activate `file_erase_nd` `ok_pb`
```

#### Close Creo
```
~ Activate `main_dlg_cur` `main_dlg_cur`
~ Close `main_dlg_cur` `main_dlg_cur`
~ FocusIn `UI Message Dialog` `yes`
~ Activate `UI Message Dialog` `yes`
```

#### Save BOM as text file
```
~ Command `ProCmdInfoBom` 
~ Activate `bom` `ok.OkBtn`
#FILE
```
#### Activate EDU-COM converter

```
~ Select `main_dlg_curappl_casc`
~ Command `ProCmdRibbonOptionsDlg` 
~ Select `ribbon_options_dialog` `PageSwitcherPageList` 1 `LicLayout`
~ Activate `ribbon_options_dialog` `LicLayout.RefBtn`
~ Activate `ribbon_options_dialog` `LicLayout.ck.EDU_COM_Convert` 1
~ Activate `ribbon_options_dialog` `OkPshBtn`
```

## Caveats

It does not seem to be possible to use a trail file to run a trail file.
When doing so with the syntax:

```
~ Command `ProCmdUtilTrailTrain` 
~ Update `file_open` `Inputname` `ADD_FILE_NAME_HERE`
~ Activate `file_open` `Inputname`
```

Creo crashes returning the following error message: 

`!%CEERROR: Trail file out of sequence at line 12.`

 