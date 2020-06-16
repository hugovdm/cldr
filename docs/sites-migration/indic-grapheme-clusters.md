# Indic Grapheme Clusters (Draft)

There are a number of scripts that don't break after viramas (halants), so that
a cluster like ksha (X) is bound together into an item that behaves like a
single character for most operations.

In [CLDR 35](index/downloads/cldr-35/index.md), it is enabled for 6 scripts:
Gujr, Telu, Mlym, Orya, Beng, Deva, and will be implemented in ICU in its next
release.

## Adding Scripts

To add another script, please open a new ticket, and:

1.  Provide verification that the implementation below works for the language.
2.  Attach a test file for that script. It must be in precisely the format used
    in
    [common/testData/segmentation/graphemeCluster](https://github.com/unicode-org/cldr/tree/master/common/testData/segmentation/graphemeCluster).

## Verification

When a script is added, it changes the ScriptList in the following. We need
verification that it is ok to forbid breaking after a Virama in all these cases.

**LinkingConsonant Virama LinkingConsonant** **Variable** Virama ScriptList, limited to: Indic_Syllabic_Category=Virama **Variable**LinkingConsonantScriptList, limited to: Indic_Syllabic_Category=Consonant**Rule**9.3Don't break within
(allowing also combining marks before and after the Virama

To see what characters would be affected, look at the following lists (replacing
**Deva** by [your script's
code](https://unicode.org/iso15924/iso15924-codes.html)). Please also supply
links to web pages that substantiate this.

*   [Virama
    Contents](http://unicode.org/cldr/utility/list-unicodeset.jsp?a=%5Cp%7BIndic_Syllabic_Category%3DVirama%7D%26%5Cp%7BScript%3DDeva%7D)
*   [LinkingConsonant](https://unicode.org/cldr/utility/list-unicodeset.jsp?a=%5Cp%7BIndic_Syllabic_Category%3D+Consonant%7D%26%5Cp%7BScript%3DDeva%7D&g=&i=)

## Implementation Details

Most people don't need to know the details, but for the curious there is more
information at:

*   [common/properties/segments/readme.txt](https://github.com/unicode-org/cldr/blob/master/common/properties/segments/readme.txt)
