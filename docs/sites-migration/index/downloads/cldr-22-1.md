# CLDR 22.1 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag **22.1** **2012-10-26**
**[Version22.1](cldr-22-1.md)**
[**CLDR22.1**](http://unicode.org/Public/cldr/22.1/)
**[Charts22.1](http://www.unicode.org/repos/cldr-aux/charts/22.1/index.html)**
**[LDML22.1](http://www.unicode.org/reports/tr35/tr35-29.html)**
[**Changes22.1**](http://unicode.org/cldr/trac/query?status=closed&milestone=22.1)
`[**release-22-1**](http://unicode.org/cldr/trac/browser/tags/release-22-1)`

Unicode CLDR 22.1 contains data for 215 languages and 227 territories—654
locales in all. Version 22.1 is an update release, with several important fixes
to CLDR 22.0.

The table above points to the files for this release. For a description of their
purpose and format, see the [Key](index.md); for more details see [CLDR Releases
(Downloads)](index.md); for a full list of changes, see the Delta link above.

The fixes include:

*   The new Turkish currency symbol (as an alternate form, until fonts catch up)
*   Simpler patterns for fallback timezone formatting (eg, “Los Angeles Time”
    instead of “United States Time (Los Angeles)”)
*   Extensive cleanup to compact numbers (eg, “1M” or “1 million”)
*   Changes of SPACE to NO-BREAK SPACE or vice versa for consistency, in many
    formats
*   Modifications to avoid collisions between city names and country names
*   Quarter patterns (eg, “2012Q1”) adjusted for consistency
*   Rule-based number patterns (eg, “twenty-three”) for several locales
*   Russian-Latin transliteration
*   Consistent capitalization for a few locales
*   Many clarifications to the specification (see
    [Modifications](http://unicode.org/reports/tr35/tr35-29.html#Modifications))

New tooling has been added for:

*   Generating locales using transliteration (eg, sr_Latn, “Serbian in Latin
    script”) or filtering (picking alternate versions of items, removing
    unnecessary data, etc.)
*   Error checking: language names containing digits, values containing SPACE or
    NBSP when the other is expected, collisions between city and country names,
    etc.
