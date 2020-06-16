# CLDR 23 Release Note

`**[release-23](http://unicode.org/cldr/trac/browser/tags/release-23)**` No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs **23** **2013-03-15** **[v23](cldr-23.md)** **[CLDR23](http://unicode.org/Public/cldr/23/)** **[Charts23](http://www.unicode.org/repos/cldr-aux/charts/23/index.html)** **[LDML23](http://www.unicode.org/reports/tr35/tr35-31/tr35.html)** [**Δ23**](http://unicode.org/cldr/trac/query?max=900&milestone=23dsub&milestone=23dres&milestone=23&order=id&col=id&col=summary&col=milestone&col=type&col=status&col=priority&col=component&revw=%21)
**`
[ΔDTD23](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-23/common/dtd&old=HEAD@tags/release-22-1/common/dtd)`**

Unicode CLDR 23.0 contains data for 215 languages and 227 territories—654
locales in all. This release focused primarily on improvements to the LDML
structure and tools, and on consistency of data. It includes substantially
improved support for non-Gregorian calendars (such as the Japanese Imperial
calendar used extensively in Japan). The data and structure has also been
modified to easily permit changing between 12 and 24 hour formats, and between 2
digit and 4 digit years. The new Unicode character is used for the Turkish Lira,
and information is provided for currencies that round to 5 cents (or other
subunits) in cash transactions. For most languages that use non-Latin scripts,
characters in the language’s script now collate before those in other scripts
(including A-Z). Language-specific letter-casing changes (Lower, Upper, Title)
have been added for Turkish, Azerbaijani, Lithuanian, and Greek. Keyboard data
has also been updated for Android.

The release had a short cycle so that we could move to the [new regular
semi-annual schedule](http://cldr.unicode.org/#TOC-2013Q1-Release). It thus only
included a limited data submission phase, for 4 languages only: Armenian (hy),
Georgian (ka), Mongolian (mn), and Welsh (cy). For those languages, the data
increased by over 100%.

Other major features are described below. The table above points to the files
for this release. For a description of their purpose and format, see the
[Key](cldr-23.md).

## Features

The main features include the following (see the Delta link above for a full
list of changes, aside from data additions and corrections):

### Structural additions and changes

*   The <fields> element has been moved from under each calendar (data only
    existed for gregorian) to just under the <dates> element
    \[[#5512](http://unicode.org/cldr/trac/ticket/5512)\]
*   A new "generic" calendar type is used to provide more consistent support for
    non-Gregorian calendars. This calendar type inherits from "gregorian", and
    all other calendar types (except chinese and dangi) inherit their format
    data from "generic", which typically has date patterns that include era.
    \[[#5385](http://unicode.org/cldr/trac/ticket/5385)\]
*   The <orientation> element attributes "characters" and "lines" are
    deprecated, replaced by new <characterOrder> and <lineOrder> elements under
    <orientation>. \[[#1297](http://unicode.org/cldr/trac/ticket/1297)\]
*   The ldml <singleCountries> element under <timeZoneNames> has been
    deprecated; it is replaced by the supplementalData top-level element
    <primaryZones>. \[[#5439](http://unicode.org/cldr/trac/review/5439)\]
*   In supplementalData, a new <timeData> element provides information on
    preferred and acceptable time cycles in various locales.
    \[[#5488](http://unicode.org/cldr/trac/review/5488)\]
*   In supplementalData, under <currencyData>:
    \[[#5548](http://unicode.org/cldr/trac/ticket/5548)\]
    *   The <info> element under <fractions> now has an additional optional
        "cashRounding" attribute used for distinguishing rounding in cash
        transactions from rounding in other (e.g. electronic) transactions.
    *   Individual <currency> elements can now use the digits, rounding, and
        cashRounding attributes.
*   The supplementalData <coverageAdditions> element and its subelements have
    been deprecated; the purpose for which this was formerly used is now handled
    by the <coverageLevels> element.
    \[[#5496](http://unicode.org/cldr/trac/ticket/5496)\]

### Data changes

*   Update to support tzdata through 2013a.
    \[[#5450](http://unicode.org/cldr/trac/ticket/5450)n,
    [#5761](http://unicode.org/cldr/trac/ticket/5761)\]
*   Significant additions to the locale data for cy (Welsh), hy (Armenian), ka
    (Georgian), and mn (Mongolian in Cyrillic script).
*   For most languages that use non-Latin scripts, characters in the language’s
    script now collate before those in other scripts.
    \[[#4020](http://unicode.org/cldr/trac/ticket/4020),
    [#5577](http://unicode.org/cldr/trac/ticket/5577)\]
*   For Assamese: Updated collation rules to support U+09CE KHANDA TA, added
    KSSA sequence to main exemplars.
    \[[#2998](http://unicode.org/cldr/trac/ticket/2998),
    [#5441](http://unicode.org/cldr/trac/ticket/5441)\]
*   The Turkish locale now uses the new U+20BA TURKISH LIRA SIGN.
    \[[#4448](http://unicode.org/cldr/trac/ticket/4448)\]
*   Most date formats with years were changed to use single 'y' (standard
    Gregorian short formats using “yy” were not changed except in a few specific
    cases such as French). \[[#5235](http://unicode.org/cldr/trac/ticket/5235),
    [#5347](http://unicode.org/cldr/trac/ticket/5347)\]
*   Initial "generic" format data is provided for all locales that had calendar
    format data. \[[#5385](http://unicode.org/cldr/trac/ticket/5385)\]
*   Several transforms have been added to support language-specific lettercasing
    changes (Lower, Upper, Title).
    \[[#2645](http://unicode.org/cldr/trac/ticket/2645),
    [#4779](http://unicode.org/cldr/trac/ticket/4779)\]
*   Number spellout (RBNF) fixes for Chinese, Croatian, Finnish, Hebrew,
    Japanese, Polish, and Ethiopic numerals.
    \[[#5352](http://unicode.org/cldr/trac/ticket/5352),
    [#5363](http://unicode.org/cldr/trac/ticket/5363),
    [#5418](http://unicode.org/cldr/trac/ticket/5418),
    [#5462](http://unicode.org/cldr/trac/ticket/5462),
    [#5663](http://unicode.org/cldr/trac/ticket/5663),
    [#5666](http://unicode.org/cldr/trac/ticket/5666),
    [#5670](http://unicode.org/cldr/trac/ticket/5670),
    [#5685](http://unicode.org/cldr/trac/ticket/5685),
    [#5460](http://unicode.org/cldr/trac/ticket/5460)\]
*   Added data for more Android key layouts.
    \[[#5420](http://unicode.org/cldr/trac/review/5420)\]
*   A number of spelling updates to Hindi names of languages & regions.
    \[[#5224](http://unicode.org/cldr/trac/ticket/5224)\]
*   Many other specific fixes and updates, please see the delta link above.

### Spec changes

*   The LDML specification has had a major reorganization. It has been split
    into multiple [Parts](http://www.unicode.org/reports/tr35/#Parts), with all
    of the material relevant to a particular topic being gathered in each Part.

### Conversion tools (including JSON support)

*   The new Ldml2JSonConverter supports conversion of LDML data to JSON format.
    \[[#2733](http://unicode.org/cldr/trac/review/2733) and many others\]
*   The LDML2ICUConverter has been enhanced to convert more types of CLDR data
    for ICU use, including supplementalData <territoryInfo> and the new
    <timeData>. \[[#2404](http://unicode.org/cldr/trac/ticket/2404),
    [#5660](http://unicode.org/cldr/trac/ticket/5660)\]

### BCP47 enhancements (after CLDR 22.1)

*   New currency ("cu") type: "zmw" \[Zambian Kwacha\]
*   New time zone ("tz") types: "debsngn" \[Europe/Busingen - Büsingen,
    Germany\], "rukhndg" \[Asia/Khandyga - Khandyga Tomponsky, Russia\] and
    "ruunera" \[Asia/Ust-Nera - Ust-Nera Oymyakonsky, Russia\]

### Key

*   The Release Note contains a general description of the contents of the
    release, and any relevant notes about the release.
*   The Data link points to a set of zip files containing the contents of the
    release (the files are complete in themselves, and do not require files from
    earlier releases -- for the structure of the zip file, see [Repository
    Organization](http://cldr.unicode.org/index/downloads#Repository_Organization)).
*   The Spec is the version of [UTS #35:
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
