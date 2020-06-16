# CheckHtmlFiles

[TOC]

This tool is used to check the TR35 spec .html files for correctness. See
[Cleaning up the spec](../cleaning-up-the-spec/index.md).

## Checking

For checking the CLDR spec, no arguments need to be supplied (other than the
standard settings in [CLDR Tools](index.md)).

Input options include:

*   -t filename // can be empty for all LDML files, or 'ucd' for all unicode
    docs.
*   -v // verbose

The output will be a listing of problems and how to correct them. Sometimes the
HTML is not clean. In that case, you'll see lines like:

> 454     Couldn't pop: ul,
> /!doctype\[0\]/html\[2\]/body\[73\]/div\[88\]/ul\[240\]/li\[445\]/ul\[447\]/li\[448\]/ul\[450\]/li\[451\]

> 9474    Couldn't pop: div,
> /!doctype\[0\]/html\[2\]/body\[73\]/div\[88\]/ul\[240\]/li\[445\]

> 9476    Couldn't pop: body,
> /!doctype\[0\]/html\[2\]/body\[73\]/div\[88\]/ul\[240\]/li\[445\]

> 9478    Couldn't pop: html,
> /!doctype\[0\]/html\[2\]/body\[73\]/div\[88\]/ul\[240\]/li\[445\]

That is often due to only one problem (typically missing a closing value like
</li>) that cascades.

For tables that don't need captions, please add <!-- nocaption --> after the
<table>. That means people don't have to check through the problems each time to
see which are real and which are not.

Under errors you will find mismatches in the version section numbers, or missing
double links. There will be a suggestion as to the fix**, but look at the text
to see if that is right first, since sometimes it is the level that is wrong, or
some other problem!** Example: the following might be misnumbered, or it might
need to be an h4 instead of h2.

*   tr35-general.html       <h2><a name="Pivots" href="#Pivots">11
    Pivots</a></h2>  <!-- Section numbers mismatch, was 10.1.1; -->

## TOC

Once those are addressed, then a clean table of contents is generated after
"\*REVISED TOC\*", which you can use to replace the old ones.

## Missing/Extra DTD items

At the very end, it lists a comparison to of the DTD items. There are two
possible problems:

1.  There is an extra line in the spec. This is typically where the spec line
    needs to be fixed. Example:
    *   **beforeCurrency**      missing ldml    <!ELEMENT beforeCurrency
        (alias|(currencyMatch\*,surroundingMatch\*,insertBetween\*,special\*))
    *   **beforeCurrency**      extra           <!ELEMENT beforeCurrency (alias
        | (currencyMatch\*, surroundingMatch\*, insertBetween\*)) >
2.  A line is simply missing. Example:
    *   **codePattern** missing ldml    <!ATTLIST codePattern type NMTOKEN
        #REQUIRED >

Both of these issues should be addressed.

Notes:

*   Ideally, it would list missing/extra lines according to which spec they
    should be present in, but that isn't done yet
*   We probably want to skip the deprecated items; either that or have a
    notation in the spec that can be checked.
