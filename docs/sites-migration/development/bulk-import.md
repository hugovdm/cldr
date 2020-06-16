# Bulk Import of XML Data (Outdated)

**The following are older instructions for how to bulk-upload XML files. Do not
use them; they are now out of date. Instead, please go to [Bulk Data
Upload](../index/survey-tool/upload/index.md).**

### Preparation

1.  Create a temporary directory in dropbox for the new files. For this example,
    we'll assume that the directory is
    **/Users/markdavis/Documents/workspace/cldr/common/indic/**
    1.  Note that you will need to put it into common for the tools to work
        right.
2.  Each one should be a regular CLDR file, with the right filename and identity
    elements. For this example, we'll assume that they are the following:
    bn.xml, gu.xml, ..., te.xml
3.  If you don't have a root.xml or en.xml in that directory you'll need to copy
    it from the regular source directory before running the tool.
4.  **Make sure that each one is a valid CLDR file.**The easiest way to do this
    is to put them in a temporary directory, and run ConsoleCheckCLDR, with the
    option:
    *   -s /Users/markdavis/Documents/workspace/cldr/common/indic/
    *   If you only have delta files (not complete), then you will want to add
        the following option to omit the Coverage tests
        *   -t ((?!.\*CheckCoverage).\*)
    *   Of course, you don't have to worry about errors / warnings that were
        there before you started. The simplest way to deal with that is to run
        ConsoleCheckCLDR with the -f option to restrict to just the locales you
        are going to change, save the result, and then diff it. For example
        *   -f (bn|gu|hi|kn|ml|mr|or|ta|te)
    *   Don't worry about errors / warnings that translators will have to deal
        with, like collisions. **(As long as you are importing before final
        vetting!)**
    *   **WARNING: a common error is to populate a default content locale (like
        zh-CN), or populate a locale using a non-standard code (iw instead of
        he). Make sure you don't do this!**
5.  For **each** file, find out which USERID to use.
    *   Go to the Survey tool, and click on Manage Users (if you don't see that,
        ask your coordinator to do this for you.
    *   In the number next to the name (i.e.#**764** Glorgle Tharp
        [foo@bar.ba](mailto:foo@bar.baz)==z==) ) is the USERID.
    *   The USERID must be for a valid user who is authorized to submit to that
        locale; typically someone from your organization. The new data will have
        a vote with the strength of that user, as if they had voted.
    *   If the user has already voted for the item or an alternate spelling of
        the item in this release, this process will not have an effect. You can
        check whether they have voted in this locale by using the Coverage page.
6.  Mark ***each*** new data item by adding alt and draft attributes, using the
    following pattern:
    1.  **alt="proposed-u<USERID>-implicit1.8" draft="unconfirmed"**
        For example:
        *   <territory type="UY">ఉరుగువే</territory>
            *becomes*
        *   <territory type="UY" alt="**proposed-u764-implicit1.8**"
            draft="unconfirmed">ఉరుగువే</territory>

*Example:*

<?xml version="1.0" encoding="UTF-8" ?>

<!DOCTYPE ldml SYSTEM "../../common/dtd/ldml.dtd">

<ldml>

<identity>

<version number="$Revision: 4337 $"/>

<generation date="$Date: 2009-10-14 17:39:12 -0700 (Wed, 14 Oct 2009) $"/>

<language type="it"/>

</identity>

<localeDisplayNames>

<languages>

<language type="az" alt="proposed-u650-implicit1.8"
draft="unconfirmed">azero</language>

<language type="ba" alt="proposed-u650-implicit1.8"
draft="unconfirmed">bashkir</language>

<language type="bn" alt="proposed-u650-implicit1.8"
draft="unconfirmed">bengali</language>

<language type="ca" alt="proposed-u650-implicit1.8"
draft="unconfirmed">catalan</language>

<language type="dz" alt="proposed-u650-implicit1.8"
draft="unconfirmed">bhutani</language>

</languages>

</localeDisplayNames>

</ldml>

### Merge. Do one of the following, A, B, or C.

---

#### A. Data into Survey Tool (after data submission start)

Tell Steven to merge your data into the running Survey Tool.

#### B. New Locale into SVN (anytime)

This is pretty straightforward.

1.  Check the files in.

#### C. Additions to Existing Locales mechanically (ONLY before data submission start)

You'll use the tool CLDRModify to do merge the new data in with the old file,
according to the following:

1.  Create a temporary target directory in dropbox/gen. We'll assume it is
    /Users/markdavis/Documents/workspace/gen/indic
2.  Run CLDRModify with the following options:
    *   -j /Users/markdavis/Documents/workspace/cldr/src/dropbox/indic/\*
    *   -d /Users/markdavis/Documents/workspace/gen/indic
    *   See also [Running Tools](running-tools/index.md)
3.  It will populate the target directory with merged files.
4.  Diff each one, and verify that there were no problems.
5.  Copy to the regular CVS source directory (/common/main), and run the
    validity checks again with ConsoleCheckCLDR.
    1.  If there is a problem, you'll have to revert the CVS files.
    2.  If you want to run the ConsoleCheckCLDR in the temporary target
        directory *before* copying over, use the following option instead.
        *   -s /Users/markdavis/Documents/workspace/gen/indic
        *   However, if you don't have a root.xml or en.xml in that directory
            you'll need to copy them from the regular source directory.

#### D. Additions to Existing Locales by hand (ONLY before data submission start)

Adding individual new items by hand is ok, as long as you check.

---

### B/C Verification (of SVN)

Finally, make sure that you didn't muck anything up.

1.  Tag the old files, so that you can roll back if you need to.
2.  Check into CVS, and notify Rick and Steven so they can update Kwanyin for
    testing.
3.  Verify that everything went well, then notify Rick and Steven so that they
    update the public server.
