# CLDR 36 Release Note

No. Date Rel. Note Data Charts Spec Delta git tag **DTD Δs** 36.1 2020-03-11
[v36.1](#TOC-CLDR-36.1) [CLDR36.1](http://unicode.org/Public/cldr/36.1/)
[Charts36.1](http://www.unicode.org/cldr/charts/36.1/)
[LDML36](https://www.unicode.org/reports/tr35/tr35-57/tr35.html)
[Δ36.1](https://unicode-org.atlassian.net/issues/?jql=project%20%3D%20CLDR%20AND%20fixVersion%20%3D%20%2236.1%22%20ORDER%20BY%20component%20ASC%2C%20priority%20DESC%2C%20created%20ASC)
[release-36-1](https://github.com/unicode-org/cldr/tree/release-36-1)
[ΔDtd36.1](http://www.unicode.org/cldr/charts/36.1/supplemental/dtd_deltas.html)
36 2019-10-04 [v36](http://cldr.unicode.org/index/downloads/cldr-36)
[CLDR36](http://unicode.org/Public/cldr/36/)
[Charts36](http://www.unicode.org/cldr/charts/36/)
[LDML36](https://www.unicode.org/reports/tr35/tr35-57/tr35.html)
[Δ36](https://unicode-org.atlassian.net/issues/?jql=project%20%3D%20CLDR%20AND%20status%20%3D%20Done%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2236%22%20ORDER%20BY%20component%20ASC%2C%20priority%20DESC%2C%20created%20ASC)
[release-36](https://github.com/unicode-org/cldr/tree/release-36)
[ΔDtd36](http://www.unicode.org/cldr/charts/36/supplemental/dtd_deltas.html)

## Overview

[TOC]

Unicode CLDR 36 provides an update to the key building blocks for software
supporting the world's languages. CLDR data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks.

A main focus this release was on infrastructure. We moved to GitHub for source
code control and Jira for bug tracking, and made significant improvements in
performance of the online data-gathering Survey Tool. We are also now keeping
more information in the master data, reflecting the votes in the Survey Tool for
the “inherited” items (see Migration).

*   Approximately 32K items added
    *   Significant increase (approx 50% or more) in moderate and/or modern
        coverage for: ceb (Cebuano), ha (Hausa / Latin script), ig (Igbo), kok
        (Konkani), qu (Quechua), to (Tongan), yo (Yoruba). Additionally, the
        following locales had at least a 15% increase in basic coverage: az
        (Azerbaijani / Latin script), so (Somali / Latin script).
    *   Seed data for new locales, including three native languages of N.
        America: cic (Chickasaw), mus (Muscogee), osa (Osage, Osage script); an
        (Aragonese), su (Sundanese, Latin script), szl (Silesian).
    *   Additional data for new items listed below.
*   Emoji
    *   Added names and keywords for Emoji 13.0 draft candidates; these are to
        be fleshed out further in v36.1.
    *   Refined names and keywords for Emoji 12.0, including for English.
*   Measurement units:
    *   Additional compoundUnitPattern ({0}⋅{1} in root) for expressing units
        like newton-meter (N⋅m)
    *   Additional units: dot-per-centimeter, dot-per-inch, em, megapixel,
        pixel, pixel-per-centimeter, pixel-per-inch; decade; therm-us; bar,
        pascal
*   Locale identifiers and names
    *   Extended Language Matching to have fallbacks for many encompassed
        languages.
        [\[CLDR-13244](https://unicode-org.atlassian.net/browse/CLDR-13244)\]
    *   Added more languageAliases from the BCP47 language subtag registry, for
        deprecated languages.
    *   New alt=“menu” names for certain languages, intended to provide better
        sorting in menus.
        \[[CLDR-11834](https://unicode-org.atlassian.net/browse/CLDR-11834)\]
    *   Updated validity and collection information for geographic subregions;
        updated names especially for subregions of UK and Sweden.
    *   Names have been added for “pseudo-regions” XA (Pseudo-Accents) and XB
        (Pseudo-Bidi). These are only intended for testing purposes, you may
        need to add special handling to remove them for production purposes.
        \[[CLDR-13100](https://unicode-org.atlassian.net/browse/CLDR-13100)\]
*   Other
    *   Time zone data support for 2019c.
        \[[CLDR-13281](https://unicode-org.atlassian.net/browse/CLDR-13281)\]
*   Additions for testing:
    *   Added new test directory /common/testData/, with test data for:
        *   localeIdentifiers,
        *   graphemeClusters (currently supported Indic languages)
        *   transforms (transliterations)
    *   For test purposes, added names for “pseudo-regions” XA and XB as noted
        above.
*   Infrastructure
    *   Moved to GitHub for source code control and Jira for bug tracking (See
        [CLDR Change Requests](http://cldr.unicode.org/index/bug-reports) for
        new information). Queries using Trac no longer work.
    *   Data in cldr repository keeps record of votes for inherited (↑↑↑)
        [\[CLDR-11989](https://unicode-org.atlassian.net/browse/CLDR-11989)\]. A
        new tool GenerateProductionData is used to resolve the inheritance
        markers and provide appropriate minimization.
    *   A new
        [cldr-staging](https://github.com/unicode-org/cldr-staging/tree/release-36/production)
        repository contains data that has been processed with
        GenerateProductionData.
    *   Added new API and tooling to support conversion to other formats (ICU in
        particular)
    *   Performance improvements in Survey Tool

For details, see [Detailed Specification Changes](cldr-36.md), [Detailed
Structure Changes](cldr-36.md), and [Detailed Data Changes](cldr-36.md).

## Detailed Specification Changes

For this version, the primary change in the LDML specification was to document
changes in the [emoji derived name
algorithm](https://www.unicode.org/reports/tr35/tr35-57/tr35-general.html#SynthesizingNames).

For more detailed specification changes, see [LDML36
Modifications](https://www.unicode.org/reports/tr35/tr35-57/tr35.html#Modifications).

## Detailed Structure Changes

This version had only one structural addition and one new “alt” value for
language names:

*   A new <compoundUnit type="times"> provides the pattern for combining units
    in a multiplicative relationship such as Newton-meters,
*   For some language names there is a new alt="menu" form which procides names
    more suitable for use in menus. For example:
    <language type="yue" alt="menu">Chinese, Cantonese</language>.

## Detailed Data Changes

Important data changes besides those listed in the Overview:

*   Transforms
    *   Hiragana-Katakana no longer modifies the spacing dakuten U+309B, U+309C.
        \[[CLDR-13127](https://unicode-org.atlassian.net/browse/CLDR-13127)\]
    *   Latin-ASCII enhanced for Latin extended C and D and some symbols.
        \[[CLDR-11383](https://unicode-org.atlassian.net/browse/CLDR-11383)\]
*   Miscellaneous
    *   zh: The currency symbol for CNY changed from fullwidth ￥(FFE5) to
        halfwidth ¥ (00A5)
    *   fr_CA : Switched to full year (not 2-digit year) in short date formats.
        \[[CLDR-11666](https://unicode-org.atlassian.net/browse/CLDR-11666)\]
    *   bg: Removed “ч.” from time formats.
        \[[CLDR-11545](https://unicode-org.atlassian.net/browse/CLDR-11545)\]
    *   The translations for the new name 'North Macedonia' has been refined for
        many languages by contributors, and those languages with no contributors
        have been reverted to code 'MK'. All Alt values also have been removed
        \[[CLDR-13099](https://unicode-org.atlassian.net/browse/CLDR-13099)\].

For more details see the list of bug fixes:
[Δ36](https://unicode-org.atlassian.net/issues/?jql=project%20%3D%20CLDR%20AND%20status%20%3D%20Done%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2236%22%20ORDER%20BY%20component%20ASC%2C%20priority%20DESC%2C%20created%20ASC).

## Migration

1.  CLDR has moved to GitHub for source code control and Jira for bug tracking.
    Queries using Trac no longer work.
2.  The data in main cldr git repository includes element values with “↑↑↑”.
    1.  Such values indicate that translators explicitly determined that the
        parent value is always valid.
    2.  These values (and the paths they belong to) are removed from the release
        data, but tools that explicitly access the repository information
        directly need to remove them.
    3.  A new tool in CLDR, GenerateProductionData.java, is used to strip the
        ↑↑↑ and minimize the data. (Those implementations that don't use that
        tool can remove lines that contain ↑↑↑; they will always be leaf nodes
        in XML.)
    4.  A new repository cldr-staging contains data that has already been
        processed with GenerateProductionData.java (this is the data that is
        used for the release).
3.  Some empty files are included in /collation/, where the root data is valid
    for them, while some empty files are removed from /annotationsDerived and
    /subdivisions/
4.  Names have been added for “pseudo-regions” XA (Pseudo-Accents) and XB
    (Pseudo-Bidi). These are only intended for testing purposes, you may need to
    add special handling to remove them for production purposes.
    \[[CLDR-13100](https://unicode-org.atlassian.net/browse/CLDR-13100)\]
5.  North Macedonia: The translations for the new name 'North Macedonia' has
    been refined for many languages by contributors, and those languages with no
    contributors have been reverted to code 'MK'. All Alt values also have been
    removed
    \[[CLDR-13099](https://unicode-org.atlassian.net/browse/CLDR-13099)\].
6.  Other specific data changes to be aware of:
    1.  zh: The currency symbol for CNY changed from fullwidth ￥(FFE5) to
        halfwidth ¥ (00A5)
    2.  fr_CA : Switched to full year (not 2-digit year) in short date formats.
        \[[CLDR-11666](https://unicode-org.atlassian.net/browse/CLDR-11666)\]
    3.  bg: Removed “ч.” from time formats.
        \[[CLDR-11545](https://unicode-org.atlassian.net/browse/CLDR-11545)\]

## Known Issues

1.  The Transform charts are temporarily disabled.
    \[[CLDR-13308](https://unicode-org.atlassian.net/browse/CLDR-13308)\]

## CLDR 36.1

This dot release makes incremental additions to version 36 for support of
Unicode 13 and ICU 66. (These new, extra Q1 releases are for integration by
vendors who could not otherwise release their products with the newest version
of Unicode.)

1.  New script codes: Chrs, Diak, Kits, Yezi
2.  New numbering system: diak, segment
3.  Unicode 13.0 updates to root collation, with updated emoji collation *(from
    CLDR 37 alpha data)*
4.  Updates to Han-Latin transform and to Chinese pinyin and stroke collations
    from Unihan 13.0 data
5.  Updates to emoji annotations *(from CLDR 37 alpha data)*

## Acknowledgments

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](../acknowledgments.md) page for a full listing.

## Key to Header Links

Rel. Note a general description of the contents of the release, and any relevant
notes about the release Data a set of zip files containing the contents of the
release (the files are complete in themselves, and do not require files from
earlier releases -- for the structure of the zip file, see [Repository
Organization](http://cldr.unicode.org/index/downloads#Repository_Organization))
Charts a set of charts showing some of the data in the release. Spec the version
of [UTS #35: LDML](http://www.unicode.org/reports/tr35/) that corresponds to the
release Delta a list of all the bug fixes and features in the release, which be
used to get the precise corresponding file changes using
[BugDiffs](http://unicode.org/cgi-bin/bugdiffs.pl) SVN Tag the files in the
release, accessible via via [Repository
Access](http://cldr.unicode.org/index/downloads#latest_draft_version). *For more
details see [CLDR Releases (Downloads)](index.md)* DTD Diffs a diff of the DTD
source files DTD Δs a link pointing to a charts of changes in the DTDs over
time.

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
