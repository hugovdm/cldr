# Updating Script Metadata

## New Unicode scripts

We should work on script metadata early for a Unicode version, so that it is
available for tools (such as Mark's "UCA" tools).

*   Unicode 9/CLDR 29: New scripts in CLDR but not yet in ICU caused trouble.
*   Unicode 10: Working on a pre-CLDR-31 branch, plan to merge into CLDR trunk
    after CLDR 31 is done.
*   Should the script metadata code live in the Unicode Tools, so that we don't
    need a CLDR branch during early Unicode next-version work?

If the new Unicode version's PropertyValueAliases.txt does not have lines for
Block and Script properties yet, then create a preliminary version. Diff the
Blocks.txt file and UnicodeData.txt to find new scripts. Get the script codes
from <http://www.unicode.org/iso15924/codelists.html> . Follow existing patterns
for block and script names, especially for abbreviations. Do not add
abbreviations (which differ from the long forms) unless there is a
well-established pattern in the existing data.

Aside from instructions below for all script metadata changes, new script codes
need English names (common/main/en.xml) and need to be added to
common/supplemental/coverageLevels, under key %script100, so that the new script
names will show up in the survey tool. For example, see the [changes for new
Unicode 8 scripts](http://unicode.org/cldr/trac/review/8109).

Can we add new scripts in CLDR ==trunk== before or only after adding them to
CLDR's copy of ICU4J? We did add new Unicode 9 scripts in CLDR 29 before adding
them to ICU4J. The CLDR unit tests do not fail any more for scripts that are
newer than the Unicode version in CLDR's copy of ICU.

## Sample characters

We need sample characters for the "UCA" tools for generating FractionalUCA.txt.

Look for patterns of what kinds of characters we have picked for other scripts,
for example the script's letter "KA". We basically want a character where people
say "that looks Greek", and the same shape should not be used in multiple
scripts. So for Latin we use "L", not "A". We usually prefer consonants, if
applicable, but it is more important that a character look unique across
scripts. It does want to be a ==*letter*==, and if possible should not be a
combining mark. It would be nice if the letters were commonly used in the
majority language, if there are multiple. Compare with the [charts for existing
scripts](http://www.unicode.org/charts/), especially related ones.

## Editing the spreadsheet

Google Spreadsheet: [Script
Metadata](https://docs.google.com/spreadsheet/ccc?key=0AqRLrRqNEKv-dG53NFlnbWg5TEp6ejVxdnVjYXZQZkE#gid=0)

Use and copy cell formulas rather than duplicating contents, if possible. Look
for which cells have formulas in existing data, especially for Unicode 1.1 and
7.0 scripts.

For example,

*   Script names should only be entered on the LikelyLanguage sheet. Other
    sheets should use a formula to map from the script code.
*   On the Samples sheet, use a formula to map from the code point to the actual
    character. This is especially important for avoiding mistakes since almost
    no one will have font support for the new scripts, which means that most
    people will see "Tofu" glyphs for the sample characters.

## Script Metadata properties file

1.  Go to the spreadsheet [Script
    Metadata](https://docs.google.com/spreadsheet/ccc?key=0AqRLrRqNEKv-dG53NFlnbWg5TEp6ejVxdnVjYXZQZkE#gid=0)
2.  File>Download as>Comma Separated Values
3.  Location/Name =
    {CLDR}/tools/java/org/unicode/cldr/util/data/Script_Metadata.csv
4.  Refresh files (eclipse), then compare with previous version for sanity
    check.
5.  Run {cldr}/tools/java/org/unicode/cldr/unittest/TestScriptMetadata.java
    1.  VM argument:
        1.  -DCLDR_DIR=/usr/local/google/home/mscherer/cldr/uni/src
    2.  A common error is if some of the data from the spreadsheet is missing,
        or has incorrect values.
6.  Run GenerateScriptMetadata, which will produce a modified
    [common/properties/scriptMetadata.txt](https://github.com/unicode-org/cldr/blob/master/common/properties/scriptMetadata.txt)
    file.
    1.  VM arguments:
        1.  -DCLDR_DIR=/usr/local/google/home/mscherer/cldr/uni/src
        2.  -DSCRIPT_UNICODE_VERSION=13
    2.  If this ignores the new scripts: You may need to update the
        -DSCRIPT_UNICODE_VERSION or edit the ScriptMetadata.java line that sets
        the UNICODE_VERSION variable.
7.  Add the English script names (from the script metadata spreadsheet) to
    common/main/en.xml.
8.  Add the French script names from [ISO
    15924](https://www.unicode.org/iso15924/iso15924-codes.html), but mark them
    as draft="provisional".
9.  Add the script codes to common/supplemental/coverageLevels.xml (under key
    %script100) so that the new script names will show up in the CLDR survey
    tool.
    1.  See
        [#8109#comment:4](http://unicode.org/cldr/trac/ticket/8109#comment:4)
        [r11491](http://unicode.org/cldr/trac/changeset/11491)
    2.  See changes for Unicode 10: <http://unicode.org/cldr/trac/review/9882>
    3.  See changes for Unicode 12:
        [CLDR-11478](https://unicode-org.atlassian.net/browse/CLDR-11478)
        [commit/647ce01](https://github.com/unicode-org/cldr/commit/be3000629ca3af2ae77de6304480abefe647ce01)
10. Add the script codes to TestCoverageLevel.java variable script100.
    1.  Why is this hardcoded here? Why does it not come from
        common/supplemental/coverageLevels.xml?
11. Remove new script codes from $scriptNonUnicode in
    common/supplemental/attributeValueValidity.xml if needed
12. For the following step to work as expected, the CLDR copy of the IANA BCP 47
    language subtag registry must be updated (at least with the new script
    codes).
    1.  Copy the latest version of
        <https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry>
        to {CLDR}/tools/java/org/unicode/cldr/util/data/language-subtag-registry
    2.  Consider copying only the new script subtags (and making a note near the
        top of the CLDR file) to avoid having to update other parts of CLDR.
13. Run GenerateValidityXML.java like this:
    1.  See [Update Validity XML](update-validity-xml.md)
    2.  This needs the previous version of CLDR in a sibling folder.
        1.  For example, with the current post-36 trunk in ~/cldr/uni/src:
        2.  Create (mkdir) ~/cldr/uni/cldr-archive/cldr-36
        3.  cd to there
        4.  git clone the CLDR repo there
            1.  probably from your fork: git clone
                https://github.com/markusicu/cldr.git .
        5.  Switch to the release branch: git checkout release-36
    3.  Now run GenerateValidityXML.java with the usual VM arguments like
        1.  -DCLDR_DIR=/usr/local/google/home/mscherer/cldr/uni/src
        2.  -DSCRIPT_UNICODE_VERSION=13
    4.  If this crashes with a NullPointerException trying to create a Validity
        object, check that ToolConstants.LAST_RELEASE_VERSION is set to the
        actual last release.
        1.  Currently, the CHART_VERSION must be a simple integer, no ".1"
            suffix.
    5.  Compare the trunk files with the generated ones: meld common/validity
        ../Generated/cldr/validity
    6.  At least script.xml should show the new scripts. Copy this file into the
        trunk.
14. Run GenerateMaximalLocales, [as described on the likelysubtags
    page](likelysubtags.md), which generates another two files.
    1.  VM arguments:
        1.  -DCLDR_DIR=/usr/local/google/home/mscherer/cldr/uni/src
        2.  -DSCRIPT_UNICODE_VERSION=13
    2.  Compare the trunk files with the generated ones: meld
        common/supplemental ../Generated/cldr/supplemental
    3.  Copy likelySubtags.xml and supplementalMetadata.xml to the trunk if they
        have changes.
15. Compare generated files with previous versions for sanity check.
16. Run the CLDR unit tests.
    1.  org.unicode.cldr.unittest.TestAll
        1.  -DCLDR_DIR=/usr/local/google/home/mscherer/cldr/uni/src
    2.  These tests have sometimes failed:
        1.  LikelySubtagsTest
        2.  TestInheritance
    3.  They may need special adjustments, for example in
        GenerateMaximalLocales.java adding an extra entry to its MAX_ADDITIONS
        or LANGUAGE_OVERRIDES.
17. Check in the updated files.

Problems are typically because a non-standard name is used for a territory name.
That can be fixed and the process rerun.
