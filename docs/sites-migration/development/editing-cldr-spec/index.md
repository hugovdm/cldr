# Editing the CLDR Spec

[TOC]

*This is a basic guide to editing the spec. We'll add to this over time.*

## Location

The LDML Spec (TR35) for CLDR is maintained via SVN, just like the data files
and tools. It is divided into multiple parts:

*   [tr35.html](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html)
*   [tr35-collation.html](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-collation.html)
*   [tr35-dates.html](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-dates.html)
*   [tr35-general.html](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-general.html)
*   [tr35-info.html](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-info.html)
*   [tr35-numbers.html](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-numbers.html)

***As we convert to the multiple parts, we need to make sure that all the links
on [Compatibility Links](compatibility-links.md) continue to function.***

***The plan is at
<https://docs.google.com/spreadsheet/ccc?key=0AqRLrRqNEKv-dDdUNklJTXpQcENuT1RvQXZQU2dMRlE#gid=1>,
with details on the sections at
<https://docs.google.com/spreadsheet/ccc?key=0AqRLrRqNEKv-dDdUNklJTXpQcENuT1RvQXZQU2dMRlE#gid=0>.***

## Editing

The CLDR Spec is one of the Unicode Technical Standards, so it has a very
specific format. When you edit it, you want to make sure that you follow the
guidelines in this document.

### Don't mess with the HTML

If you use a WYSIWYG tool, make sure that it doesn't make arbitrary changes to
the HTML.

1.  *Don't use Microsoft Word* -- it completely mucks up the HTML
2.  If you use FrontPage, make sure to make the settings not change the HTML

### Mark all changes

New or changed text should be marked with <span class="changed">, and text to be
removed marked with <span class="removed">. Note that <span> can't cross block
elements like <div>, <p>, <td>, and so on. So if you are changing a bunch of
text within a table or multiple paragraphs, you have to mark each one
separately. *This is* ***MUCH*** *easier to do with a WYSIWYG editor.*

*   Also put a note summarizing each type of change in the Modifications
    section. At the end of the note, reference any relevant bug using the format
    "\[ticket #456\]".

### Use Styles

1.  For Examples, DTD fragments, etc.
2.  Look at existing text in the document to find the right style to use.

### Fix links

Every <hX> should be of the following form, with the name, href, and the <a>
surrounding all the text. By having both name and href, it is "double-linked";
users can get a link to that point in the text just by clicking. All header tags
(after Contents) should be in the Table of Contents.

**<h4><a name=*"Numeric_Codes"* href=*"#Numeric_Codes"*>3.1.1 Numeric
Codes</a></h4>**

Every table, and figure should be of the following form:

**<p class="caption"><a name=*"Legacy_Variant_Mappings"* href=*"#Legacy_Variant_Mappings"*>Legacy Variant Mappings</a></p>**
**<table>**

(don't use <caption>Legacy Variant Mappings</caption>)

There are other details on the format at
<http://unicode.org/reports/tr-template.html>.

### Make sure the markup is clean

***See [Cleaning up the spec](../../cleaning-up-the-spec/index.md)!***

### Validate the results

Run the following tools to make sure you haven't messed anything up. (You can
just click on the links in Preview Mode.)

1.  <http://validator.w3.org/check?uri=http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html>
2.  <http://jigsaw.w3.org/css-validator/validator?uri=http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html>
3.  <http://validator.w3.org/checklink?url=http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html>

### Diff the results

Before you check into CVS, make sure that you diff with the previous version, to
make sure that you don't have any inadvertent changes.

## DTD / Structure Changes

You must follow the process on [Updating DTDs](../updating-dtds/index.md)!

## Life-cycle

Ask Rick to do these steps at the appropriate times, to:
<http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html>

*See Big Red Switch document:*
[*http://unicode.org/cldr/big_red_switch.html*](http://unicode.org/cldr/big_red_switch.html)
*for details on some of these.*

*   When the new cycle is started:
    *   The header needs to be updated so that it is a draft version for the
        next release.
        *   Example: <http://unicode.org/draft/reports/tr35/tr35.html?rev=1.260>
        *   Note that it is a bit different from the other Unicode documents. In
            particular, use the following format for these fields
            *   Version: 1.5 (draft) $Revision: 1.240 $
            *   Date: $Date: 2007/07/25 03:54:31 $
    *   Add a new section of Revisions in the Modifications section at the end.
    *   If necessary, update the copyright year at the end of the document.
    *   In all data files, replace old DTD numbers by new, and check in. Update
        the soft link on the Unicode site. See BRS.
        *   Examples for the transition from 1.5 and 1.5.1 to 1.6:
        *   *In all common files: http://www.unicode.org/cldr/dtd/1.5*
            *   *=> http://www.unicode.org/cldr/dtd/1.6*
        *   "* *In 2 dtd files: version CDATA #FIXED "1.5
            *   *=> version CDATA #FIXED "1.6"*
        *   '* *In test files: cldrTest version='1.5.1
            *   *=> cldrTest version='1.6'*
*   For the final release:
    *   The header has to be all cleaned up, so that it is not a draft version.
    *   Everything has to validate (see above).
    *   That release version is copied over to the Unicode web site.
    *   [*http://unicode.org/cldr/big_red_switch.html*](http://unicode.org/cldr/big_red_switch.html)

## References

Use the same style for references as other TRs. If you have a reference to an
RFC, you can use links like <http://tools.ietf.org/html/rfc4646#section-2.2>. In
the References section, use the 'canonical' (aka ugly) URL, eg
<http://www.ietf.org/rfc/rfc4646.txt>.

## Recommended Editors

*   Windows
    *   FrontPage
*   Macintosh
    *   To edit the HTML directly (not WYSIWYG): BBEdit, Taco (has html preview
        and syntax check)
    *   WYSIWYG editors: DreamWeaver, <others?>
