# Constructing Bulk Uploads

The following describes how to construct bulk uploads from existing files.

1. Use SearchXml.java to find the original paths + values that you want to work
from.

***Example:*** all paths for Croatian

> -f ^hr$

> -p .\*

***Results:***

> ...

> **hr**.xml      **afarski**
> **//ldml/localeDisplayNames/languages/language\[@type="aa"\]**

> ...

> *(Search has other options: use -h to see them.)*

2. Copy the results (which are tab-delimited) into a file, and use regex, search
and replaces, or spreadsheets to get the right format for a config file.

***Example:***

> locale=**bs** ; action=addNew ; new_value= **afarski** ;
> new_path=**//ldml/localeDisplayNames/languages/language\[@type="aa"\]**

For example, what I find simple is to copy into a spreadsheet, and construct the
config line from them:

> "locale=bs ; action=add ; new_value=" & B1 & "; new_path=" & C1

Alternatively, for simple cases like the above, you can just do search & replace
within the file.

3. Use [CLDRModify using Config
file](cldr-big-red-switch/cldrmodify-passes/cldrmodify-config.md) to
modify/create a file.

4. Sanity Check

5. Either merge into trunk or make a separate file for bulk upload, depending on
the ticket description.
