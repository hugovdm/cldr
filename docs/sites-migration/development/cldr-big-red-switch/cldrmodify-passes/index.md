# CLDRModify Passes

## Main Process

This section describes how to run the CLDRModify passes for the mechanical
cleanup before the release.

### From SurveyTool

1.  The data will be in <http://www.unicode.org/repos/cldr-aux/voting/30>/
2.  Copy the **dtd** and **casing** directories
    1.  from **trunk/cldr/common**
    2.  into **cldr-aux/voting/30/vxml/common**
    3.  (where 30 is replaced by the target version)
3.  Run RemoveEmptyCLDR.java to fix the empty annotations.
4.  Run ConsoleCheckCLDR with
    1.  -e -z final_testing -s {workspace}/cldr-aux/voting/30/vxml/common/main
5.  Pick a couple of sample locales, and diff them. Look for systemic problems.
6.  If there are no severe problems (eg, data may have errors, but there are no
    systemic problems), copy into **trunk/cldr/common**

### Before Starting

1.  ~~Diff common/main with incoming/common/main~~
2.  ~~Spot check for problems.~~
3.  Run the ConsoleCheckCLDR (with options below) to see if there are errors.

### Successive Passes

You will then run CLDRModify with different options, in multiple passes.

1.  With each step, sanity check the results (as described below), fix any
    problems, tag, and check in as described below.
2.  ***This sanity check is important,*** since the regularizing often reveals
    problems in the original. For example, a date format like MMM'-yy
    regularizes to MMM-'yy' -- but the original was clearly an error.
3.  If you need to do a single file over again (eg resolving conflicts), use the
    -m option on CLDRModify, as described below.

### After passes

*   After you are all done, run ConsoleCheckCLDR once more, to make sure you
    didn't introduce any new errors.

---

## Details

For the purpose of this document, we'll assume you are generating into
{cldrdata}/dropbox/gen/main/ as the target directory. Change any instance below
to the directory that you actually use.

### Passes

*   Each pass will build into {cldrdata}/dropbox/gen/main/
*   Each time you will run CLDRModify with the standard options, plus one of the
    listed [Options](index.md) bulleted below.
*   After building, remember to refresh data files with F5 if you are using
    Eclipse, after building.
*   Compare against the SVN files (see above) for sanity - it is best to diff
    every file and review.
*   Then copy the gen/main files to the common/main files
*   Run ConsoleCheckCLDR to verify that no errors have been introduced. Standard
    options, plus:

        *// set this to test in the original directory:*
        -DCLDR_MAIN={cldrdata}/dropbox/gen/main/

        -e

        -z final_testing

*   If ok, check in (see [How to check in consistently after each
    pass](index.md)).
*   Otherwise, either manually patch, or revert from SVN Head files to get back
    to a clean state, fix, and repeat.

### Options

Standard Options: -Dfile.encoding=UTF-8 -Xmx512M -DSHOW_FILES *plus* your choice
of source/target directories.

1.  After doing the **/common/main/** files, do the otherdirectories, with the
    extra options:
    1.  -s{cldrdir}**/common/annotations**
    2.  -s{cldrdir}**/common/subdivisions** *— import the Wikidata first*
    3.  -s{cldrdir}**/seed/main**
    4.  -s{cldrdir}**/seed/annotations**
    5.  -s{cldrdir}**/exemplars/main**

#### **Other options for each pass:**

**1 <no options> ALL Reformat**

1.  **This will regularize the structure, so that's not mixed in with later
    changes**
2.  **If any WARNING occurs, fix it manually (this is when two items have the
    same path when reading in the file).**

**2-fQonly /annotations Adds the annotation names to keywords3-fpALLDAIP
(normally done by Survey Tool, but this catches manual insertion)~~4-f_only
/mainRemove superfluous compound language translations (like "Portuguese
(Brazilian)")5-fmonly /mainRemove superfluous alt-variant values6-rALLMinimalize
data~~ \*\*\* DO NOT DO \*\*\* Check BRS for other steps, like
derivedAnnotations, sr_Latn,...**

#### ***You will have to repeat this cycle if any outside changes are made to the data!***

#### One-Time Fixes

There are a number of "one time fixes" that are in the CLDRModify code. The code
remains in case we want to adapt for future cases, but don't use them unless you
fix the code to do what you want, and carefully diff the results. Here are some
of them:

1.  -fk: use a configuration file. Details on [CLDRModify
    Config](cldrmodify-config.md)
2.  -fe: fix Interindic. If you need to make changes in transliteration, you
    might want to modify this and run it.
3.  -fs: Fix the stand-alone narrow values.
4.  -fu: Fix the unit patterns.
5.  -fd: Fix dates
6.  -fz: Fix exemplars
7.  -fr: Fix references and standard
8.  -fc: Transition from an old currency to a new currency. This fix is quite
    useful when a country introduces a new currency code ( usually due to a
    devaluation ), but the name remains the same. In order to use this fix,
    modify the following values in the CLDRModify code under "**fixList.add('c',
    "Fix transiton from an old currency code to a new one**"
    1.  Change the String oldCurrencyCode and newCurrencyCode to reflect the
        currency codes you are transitioning.
    2.  Change the int fromDate and toDate to reflect the dates that the old
        currency was in circulation. These will be used to create the date range
        in the old currency string.
    3.  Run the CLDRModify tool as usual, diff the results and check in.

---

## How to check in consistently after each pass

### Sanity Check

1.  The console will list changes made, such as:
    *   Creating File: {cldrdata}/dropbox\\gen\\main\\zh_Hant.xml
        \*Renaming old {cldrdata}/dropbox\\gen\\main\\zh_Hant.xml
        %zh_Hant_HK - Replacing: <yy'年'M'月'd'日'> by <yy年M月d日> at:
        //ldml/dates/calendars/calendar\[@type="gregorian"\]/dateFormats/dateFormatLength\[@type="short"\]/dateFormat\[@type="standard"\]/pattern\[@type="standard"\]
2.  The diff folder in the output has CompareIt! bat files for each change, or
    you can use SVN diff after moving to the SVN folder by doing the Copy and
    then checking.

### Copy Files

*   Copy from the target directory (eg {cldrdata}/dropbox\\gen\\main) to the svn
    directory (eg {cldrdata}/common\\main)
*   Run CLDRModify again, with nothing but standard options. This will verify
    that there are no xml errors.
    *   There should be no change in the output; thus you should not see
        anything but _unchanged_.....xml files in the target directory.

### Now ready to check in

*   Run the CLDR Unit Tests to make sure you didn't break anything
*   Run ConsoleCheckCLDR -e -z final_testing
*   Check in - I usually use a comment such as "cldrbug 1234: BRS Task A21 :
    CLDRModify -fp"

**If someone checks in a change in the middle of one of your passes, it is
generally easier to check in the rest of the changes, check out a clean copy of
that file, and return the pass with only that file. The -m(uk) option can be
used to restrict the pass to only uk.xml, for example.**
