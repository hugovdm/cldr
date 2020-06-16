# CLDRModify using Config file

[TOC]

The CLDRModify tool can be used to make changes to a number of files, based on a
configuration file.

*   Either put your changes into cldr/tool/modify_config.txt, or use -k
    config_file to specify a different file.
    *   Use the format specified below.
    *   The path is relative to cldr/tool/
*   Remember to specify the target directory, if different than common/main
*   Run CLDRModify with the -fk option, and as usual, diff your changes. For
    more info, see [CLDRModify Passes](index.md).
*   The format may change in the future!

As an example of how this is done, and the results, see:
<http://unicode.org/cldr/trac/changeset/9108>

## File Format

The file format is a series of lines of the form:

ConfigKeys1=ConfigMatch1 ; ConfigKeys2=ConfigMatch2 ; ...

### Debugging

The following line shows the number of file lines that are applicable to this
locale. It may be helpful in debugging.

# Checking entries & adding:    2

You can also search for /fixList.add('k',/ in the file, and put a breakpoint in
handleStart or handlePath.

### ConfigKeys

*locale*, *action*, *path*, *value, new_path, new_value*

A locale (regex) must be present.

Not all of {*path*, *value, new_path, new_value*} will be present (or can be),
depending on the action.

### ConfigMatch

For the action, see below. Everything else can be a regex or an exact string.

// Use a string of "/.../" for a regex match, otherwise an action, otherwise an
exact string match.
// The regex match is a "find", so use /^...$/ for a whole string match.

If the locale is /./, then any locale matches.

***Warning! This won't work if you need certain literal characters (such as ; or
a leading or trailing space, etc.).** **See** [TODO](cldrmodify-config.md).*

*   *If it is in a regex, you can use the **\\x3B** format to work around this.*
*   *If it is in a UnicodeSet use **\\u003B** format.*

### ConfigAction

#### **action=delete**

If there is a match for the value and path and locale, then the action is taken.

If the path is empty, any path matches. If the value is empty, any value
matches.

#### **action=add**

The new_path and new_value are explicit strings, and the <new_path, new_value>
are added to the files that match the locale.

#### action=addNew

Same as add, but only for paths that don't have values in the original value.

#### action=replace

Replace <path, value> with <newPath, newValue>

### Example file

locale= sv ; action=delete; value= YER ; path=
//ldml/numbers/currencies/currency\[@type="YER"\]/symbol ;

locale=en ; action=delete ; path=/.\*short.\*/

locale=en ; action=add ;
new_path=//ldml/localeDisplayNames/territories/territory\[@type="PS"\]\[@alt="short"\]
; new_value=Palestine

### Path Ids

An exact path can be either the literal string or a hex id. So the following are
equivalent:

locale=  sk     ; action=add ; new_path=68e706b7c7873181         ;
new_value=honduraskej lempiry

locale=  sk     ; action=add ;
new_path=//ldml/numbers/currencies/currency\[@type="HNL"\]/displayName\[@count="many"\]
; new_value=honduraskej lempiry

### TODO

Change **add** so that path and/or value can be present, and if so, $0..$9 will
be substituted for in the respective new_path or new_value.

After splitting at ";", change \\x3B and other \\x{H..H} characters into ";".
