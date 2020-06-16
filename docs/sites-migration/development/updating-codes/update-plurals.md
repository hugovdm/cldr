# Adding/Fixing Plural and Ordinals

## Run WritePluralRulesSpreadsheets.java

## Adding rules for a locale

1.  Add the new plural and ordinal rules to plurals.xml and ordinals.xml.
2.  Run GeneratedPluralSamples as below.
3.  Add the minimal pairs to the locale.

## Changing rules/ranges

## Whenever you change plural rules, ordinal rules, or plural ranges — and at the end of the release — you must do the following. The reformatting is required, since it regenerates the samples (after @), which are now necessary for correct functioning of ICU and other clients.

1.  Run GeneratePluralRanges.java to reformat pluralRanges.xml
    1.  The results on the console. Paste into the file, and check differences.
2.  Run GeneratedPluralSamples to reformat plurals.xml, ordinals.xml.
    1.  Generates two new files (in {generated}/cldr/supplemental/), which you
        can copy into the supplemental directory.
3.  Run GenerateAllCharts (actually, it is enough to run ShowLanguages) and the
    unit tests.
    1.  This will insure that the rules are correctly represented, and aligned
        with the minimal pairs.
    2.  Diff the plurals chart against the old one: eg
        /cldr-aux/charts/<version>/supplemental/language_plural_rules.html
4.  ~~Run FindPluralDifferences to see that the expected changes are there (only
    tests integers right now).~~
    1.  ~~Modify the versions variable to use the last release.~~
    2.  ~~This is also run at the end of the release to get the Migration info
        for the release.~~
5.  Compare the results carefully, then check in.
