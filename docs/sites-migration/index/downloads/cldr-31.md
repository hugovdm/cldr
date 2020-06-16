# CLDR 31 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs
31.0.12017-04-07[v31](http://cldr.unicode.org/index/downloads/cldr-31)[CLDR31.0.1](http://www.unicode.org/Public/cldr/31.0.1/)[Charts31](http://www.unicode.org/cldr/charts/31/)[LDML31](http://www.unicode.org/reports/tr35/tr35-47/tr35.html)[Δ31.0.1](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=31&milestone=31.0.1&group=component&max=999&col=id&col=summary&col=owner&col=type&col=status&col=priority&col=time&order=priority)[release-31-0-1](http://www.unicode.org/repos/cldr/tags/release-31-0-1/)[`ΔDTD31`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-31/common/dtd&old=HEAD@tags/release-30/common/dtd)
31 2017-03-20 [v31](http://cldr.unicode.org/index/downloads/cldr-31)
[CLDR31](http://unicode.org/Public/cldr/31/)
[Charts31](http://www.unicode.org/cldr/charts/31/)
[LDML31](http://www.unicode.org/reports/tr35/tr35-47/tr35.html)
[Δ31](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=31&group=component&max=999)
[release-31](http://www.unicode.org/repos/cldr/tags/release-31/)
[`ΔDTD31`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-31/common/dtd&old=HEAD@tags/release-30/common/dtd)

## Overview

Unicode CLDR 31 provides an update to the key building blocks for software
supporting the world's languages. This data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks.

Some of the improvements in the release are:

*   **Canonical codes** (See [Migration](cldr-31.md))
    *   The subdivision codes have been changed to all have the bcp47 format.
    *   The locales in the language-territory population data are in canonical
        format.
    *   The timezone ID for GMT has been split from UTC.
    *   There is a mechanism for identifying hybrid locales, such as
        [Hinglish](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html#Hybrid_Locale).
*   **Emoji 5.0**
    *   Short names and keywords have been updated for English. (Data for other
        languages to be gathered in the next cycle).
    *   Collation (sorting) adds the new 5.0 Emoji characters and sequences, and
        some fixes for Emoji 4.0 characters and sequences.
    *   For Emoji usage, subdivision names for Scotland, Wales, and England have
        been added for 65 languages.
    *   \[31.0.1\] Added full list of derived names
        [#](http://unicode.org/cldr/trac/ticket/10126)[10126](http://unicode.org/cldr/trac/ticket/10126),
        and fixed some collisions in derived names
        [#](http://unicode.org/cldr/trac/ticket/10127)[10127](http://unicode.org/cldr/trac/ticket/10127).

For changes that may affect migration to this version, see
[Migration](cldr-31.md).

### Other structural additions and changes

*   Codes now use canonical form, as described above.
*   New structure for lenient parsing
*   New structure for minimal pairs (for plurals)
*   New language-matching structure for matching groups of countries
*   The literacyPercent for a region is broken out from writingPercent
*   For DTD changes, see [DTD
    Deltas](http://www.unicode.org/cldr/charts/31/supplemental/dtd_deltas.html)

For more information, see [Spec
Modifications](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html#Modifications).

### Other data additions and changes

*   New timezone IDs (long form and bcp47 form).
*   New currency code BYR.
*   Minimal pairs for plural rules.
*   New data for lenient parsing
*   Enhanced Language Matching data (new elements and attributes)
*   Updated Windows keyboards
*   <fields> data fleshed out for era, weekday, dayperiod, and zone, and new
    <fields> data added for weekOfMonth, dayOfYear, weekdayOfMonth.
*   A pseudo-locale generation tool.
*   A number of additions to exemplar characters, such as for Arabic and Farsi
*   Some improvements to the Zawgyi-to-Unicode transform, and other transforms.
*   Collation data updated for Unihan 9.0 and for Emoji 5.0
*   New unit type "length-point"
*   \[31.0.1\] Fixed inconsistent names in Czechia
    [#10122](http://unicode.org/cldr/trac/ticket/10122), and some negative
    current subpatterns for compact decimal formatting
    [#10131](http://unicode.org/cldr/trac/ticket/10131)
*   \[31.0.1\] Fixed collation charts
    [#10139](http://unicode.org/cldr/trac/ticket/10139)

For more information, see [detailed delta
charts](http://www.unicode.org/cldr/charts/31/delta/index.html).

## Growth

The following gives the total overview of the change in data items in CLDR.
*This release did not have a data-submission cycle, so the changes reflect
cleanup and bug fixes.*

added items
0.99%
deleted items\*                                                         0.70%
changed items                                                   1.21%
*total items*                                                   *975,840*

\* The measurement of the number of items is reflects the different ways that
the information is represented. A single data field (element or attribute value)
may result in multiple data items. For example, plural rules may be shared by
multiple languages, and a single data field contains all the languages to which
those rules apply. Sometimes a changed item appears as a deletion+addition, and
sequences of items (such as sort order) are not counted as different even if the
order changes.

For more details, see the [Delta
Data](http://www.unicode.org/cldr/charts/31/delta/index.html) charts.

## JSON data

*   No structural changes for this release, just updated to match XML data.

## Survey Tool

*   no changes in the Survey Tool this release

## Specification changes

[Part 1, Sec
3.7](http://www.unicode.org/reports/tr35/tr35-47/tr35.html#t_Extension) New
table of -t- keys. [Part 1, Sec
3.10.2](http://www.unicode.org/reports/tr35/tr35-47/tr35.html#Hybrid_Locale)
Description of new hybrid locale identifiers [Part 1, Sec
4.4](http://www.unicode.org/reports/tr35/tr35-47/tr35.html#LanguageMatching)
Description of new structures for enhanced language matching [Part 1, Sec
6.2](http://www.unicode.org/reports/tr35/tr35-47/tr35.html#Extended_Pictographic)
Improved the emoji grapheme break rule extension GB11′ [Part 2, Sec
3.6](http://www.unicode.org/reports/tr35/tr35-47/tr35-general.html#Character_Parse_Lenient)
Description of new parseLenient element [Part 2, Sec
6](http://www.unicode.org/reports/tr35/tr35-47/tr35-general.html#Unit_Elements)
New unit added for typographic point
[Part 2, Sec
14.1](http://www.unicode.org/reports/tr35/tr35-47/tr35-general.html#SynthesizingNames)
Clarified construction of emoji annotations [Part 3, Sec
2.4.1](http://www.unicode.org/reports/tr35/tr35-47/tr35-numbers.html#Compact_Number_Formats)
Clarified use of ‘0’ in compact decimal patterns [Part 4, Sec
3](http://www.unicode.org/reports/tr35/tr35-47/tr35-dates.html#Calendar_Fields)
New <field> attributes [Part 4, Sec
4.3](http://www.unicode.org/reports/tr35/tr35-47/tr35-dates.html#Week_Data)
Clarified use of “week of” patterns [Part 4, Sec
8](http://www.unicode.org/reports/tr35/tr35-47/tr35-dates.html#Date_Format_Patterns)
Restructured date-time table. [Part 6, Sec
2.2](http://www.unicode.org/reports/tr35/tr35-47/tr35-info.html#Subdivision_Containment)

Subdivision containment, documenting the change in usage of the subgroup element
attributes type and contains

[Part 6, Sec
2.3](http://www.unicode.org/reports/tr35/tr35-47/tr35-info.html#Supplemental_Territory_Information)
Supplemental territory info: added literacy percent for language population

For details, see [Spec
Modifications](http://www.unicode.org/reports/tr35/tr35-47/tr35.html#Modifications).

## Migration

*   **Code changes**
    *   The subdivision codes have been changed to all be the bcp47 format, eg
        "usca" instead of "US-CA". This affects supplemental containment and
        subdivisions, and translations in subdivisions/en.xml, etc. See [Part 6,
        Sec
        2.2](http://www.unicode.org/reports/tr35/tr35-47/tr35-info.html#Subdivision_Containment)
        \[#[9942](http://unicode.org/cldr/trac/ticket/9942)\]
    *   The locales in the language-territory population tables have been
        changed to be the canonical format, dropping the script where it is the
        default. So "ku_Latn" changes to "ku"
    *   The exemplar/ locale data file names have also been changed to be the
        canonical format, dropping the script where it is the default.
*   **Plural rules**
    *   The Portuguese plural rules have changed so that all (and only) integers
        and decimal fractions < 2 are singular.
*   **Timezones**
    *   The GMT timezone has been split from the UTC timezone.
    *   New timezone bcp47 codes have been added.
*   **Language/Region data**
    *   The new literacyPercent attribute for supplemental <languagePopulation>
        has been broken out from writingPercent, the latter now only being used
        to reflect primarily-spoken languages.
        \[#[9421](http://unicode.org/cldr/trac/ticket/9421)\]
    *   A new format for language matching is provided. To allow time for
        implementations to change over, the old data is retained, and the new
        data is marked as "written-new".
    *   Languages "hr" and "sr" are no longer a short distance apart, for
        political reasons.
*   **Other**
    *   The primary names for CZ changed from "Czech Republic" to "Czechia",
        with the longer name now the alternate.

## Known Issues

### “Week of” structure

The structure and intended usage for the “week x of y” patterns is still being
refined and may change. This applies especially to dateFormatItems such as the
following:

<dateFormatItem id="MMMMW" count=...>'week' W 'of' MMM</dateFormatItem>
<dateFormatItem id="yw" count=...>'week' w 'of' y</dateFormatItem>

Areas of discussion include the use of the count attribute and the use of
ordinal vs. cardinal numbers. For more information see
\[#[9801](http://unicode.org/cldr/trac/ticket/9801)\].

### ~~Non-unique emoji short names (fixed in 31.0.1)~~

~~Some of the emoji names are not unique. Fixes are being gathered, but are not
in time for the release. See
\[[#10116](http://unicode.org/cldr/trac/ticket/10116)\],
\[[#10127](http://unicode.org/cldr/trac/ticket/10127)\]~~

### Chinese stroke collation

Since CLDR 30, Chinese stroke collation has been missing entries for several
basic characters. CLDR 32 reverts the stroke collation data to the CLDR 29
version; a complete fix for the underlying problem is targeted for CLDR 33. See
#[10497](http://unicode.org/cldr/trac/ticket/10497),
#[10642](http://unicode.org/cldr/trac/ticket/10642).

### Others

See [tickets for v31.0.1](http://unicode.org/cldr/trac/query?milestone=31.0.1).

## Acknowledgments

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](../acknowledgments.md) page for a full listing.

## Key

*   The Release Note contains a general description of the contents of the
    release, and any relevant notes about the release.
*   The Data link points to a set of zip files containing the contents of the
    release (the files are complete in themselves, and do not require files from
    earlier releases -- for the structure of the zip file, see
    [Repository
    Organization](http://cldr.unicode.org/index/downloads#Repository_Organization)).
*   The Spec is the version of                      [UTS #35:
    LDML](http://www.unicode.org/reports/tr35/) that corresponds to the release.
*   The Delta document points to a list of all the bug fixes and features in the
    release, which be used to get the precise corresponding file changes using
    [BugDiffs](http://unicode.org/cgi-bin/bugdiffs.pl).
*   The SVN Tag can be used to get the files via [Repository
    Access](http://cldr.unicode.org/index/downloads#latest_draft_version).
*   *For more details see [CLDR Releases (Downloads)](index.md).*

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
