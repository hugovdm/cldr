# CLDR 25 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs 25 2014-03-19
[v25](cldr-25.md) [CLDR25](http://unicode.org/Public/cldr/25/)
[Charts25](http://www.unicode.org/repos/cldr-aux/charts/25/index.html)
[LDML25](http://www.unicode.org/reports/tr35/tr35-35/tr35.html)
[Δ25](http://unicode.org/cldr/trac/query?status=closed&milestone=25&max=900) ` [
release-25](http://unicode.org/cldr/trac/browser/tags/release-25)` ` [
ΔDTD25](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-25/common/dtd&old=HEAD@tags/release-24/common/dtd)`

## Overview

[TOC]

This release focused primarily on improvements to the LDML structure and tools,
and on consistency of data. There are many smaller data fixes, but there was no
general data submission. Changes include the following:

    New rules for plural ranges (1-2 liters) for 72 locales, plurals for 2
    locales, and ordinals for 18 locales.

    Better locale matching with fallbacks for languages, default languages for
    continents and subcontinents, and default scripts for more languages.

    Two new locales: West Frisian (fy) and Uyghur (ug).

    Two new metazones: Mexico_Pacific and Mexico_Northwest

    Updated zh pinyin & zhuyin collations and transforms for Unicode 6.3
    kMandarin data

    Updated keyboard layout data for OSX, Windows and others.

Details are provided below, including coverage, charts, and new features. There
is a detailed [Migration](cldr-25.md) section, which should be reviewed
carefully.

The table at the top of this page lists the files for this release. For a
description of their purpose and format, and for the coverage graphic, see the
[Key](cldr-24.md).

## Structural additions and changes

*   The preferred attribute ordering is now specified by the order in the DTD.
    \[#[6426](http://unicode.org/cldr/trac/ticket/6426)\]
*   Added the
    <[pluralRanges](http://www.unicode.org/reports/tr35/tr35-35/tr35-numbers.html#Plural_Ranges)>
    element. \[#[6722](http://unicode.org/cldr/trac/ticket/6722)\]
*   Added the <approvalRequirements> element for
    <[coverageLevels](http://www.unicode.org/reports/tr35/tr35-35/tr35-info.html#Coverage_Levels)>.
    \[#[6156](http://unicode.org/cldr/trac/ticket/6156)\]
*   Deprecations and renamings are listed in the Migration section.

## Data additions and changes

### General

*   Better locale matching, with better fallbacks; likely subtags for regions;
    added scripts for various languages.
*   Improved data on official languages.
*   Added new locales "fy" (West Frisian), "fy_NL", "ug" (Uyghur), "ug_Arab",
    "ug_Arab_CN", and (in seed) "prg" (Prussian).
    \[#[9747](http://unicode.org/cldr/trac/changeset/9747),
    #[6936](http://unicode.org/cldr/trac/ticket/6936),
    #[6590](http://unicode.org/cldr/trac/ticket/6590)\].
*   Correct the encoding for some data in the Myanmar (Burmese) locale from
    Zawgyi to proper Unicode.
*   Spanish narrow name for "weds" reverts to "X".
    \[#[6808](http://unicode.org/cldr/trac/ticket/6808)\]
*   Fixed order for en_CA short date.
    \[#[6752](http://unicode.org/cldr/trac/ticket/6752)\]
*   In zh and zh_Hant, Chinese calendar days now use "hanidays" numbering.
    \[#[6979](http://unicode.org/cldr/trac/ticket/6979)\]
    \[#[9732](http://unicode.org/cldr/trac/changeset/9732)\]
*   Added epoch/era data for Coptic and Ethiopic calendars.
    \[#[6674](http://unicode.org/cldr/trac/ticket/6674)\]
*   Added exemplar set data for over 700 new languages.
*   Many other fixes for date formats, locale display names, number symbols,
    unit names, etc.; see detailed deltas in table at the top of this page.

### Timezones

*   Added two metazones Mexico_Pacific and Mexico_Northwest and a few
    translations for them. \[#[5957](http://unicode.org/cldr/trac/ticket/5957)\]
*   Updated the short metazone names for European languages.
    \[#[9624](http://unicode.org/cldr/trac/changeset/9624)\]
*   Updated Windows timezone mappings.
    \[#[6973](http://unicode.org/cldr/trac/ticket/6973),
    #[6971](http://unicode.org/cldr/trac/ticket/6971)\]
*   Removed data for three deprecated zones.

### Plurals

*   Added cardinal (plural) rules for "root" and 2 locales: prg, ug
*   Added ordinal (1st, 2nd,…) rules for “root” and 18 locales: az, cy, fy, hy,
    ka, kk, km, ky, lo, mk, mn, my, ne, pa, prg, si, sq, uz
*   Added new plural ranges for 72 locales
*   Fleshed out [minimal
    pairs](http://cldr.unicode.org/index/cldr-spec/plural-rules#TOC-Determining-Plural-Categories)
    for fuller coverage.

### Collation

*   Collation data converted to remove deprecated elements & attributes.
    \[#[6747](http://unicode.org/cldr/trac/ticket/6747)\]
*   Added German tailoring of "eor" European Ordering Rules.
    \[#[6809](http://unicode.org/cldr/trac/ticket/6809)\]
*   Updated zh pinyin & zhuyin collations to use Unicode 6.3 kMandarin readings
    (added tones for 120+ characters)

### Transforms

*   Added IPA transcription rules for Chamorro (ch), Klingon (tlh), Latin (la),
    Lower Sorbian (dsb)
*   Updated Han-Latin transform to use Unicode 6.3 kMandarin readings (added
    tones for 120+ characters)

### RBNF

*   Added a new zh number system “hanidays”, for use with calendars.
    \[#[6979](http://unicode.org/cldr/trac/ticket/6979)\]

### Keyboard layouts

Keyboard layout data was updated for the newest versions of Android, Chrome OS,
Mac OSX and Windows. The layouts for different platforms and languages are
listed under the [Keyboard layout
charts](http://www.unicode.org/cldr/charts/25/keyboards/layouts/index.html). The
Mac OSX mappings are now current (in v24 they were a much older version). With
these updates CLDR has data for the following number of keyboards:

**CountPlatform** 175 Android 54 Chrome OS 136 Mac OS X 193 Windows
1*Additional*

The first four rows are keyboards that reflect the data shipping on the
respective platform. New in this release is the “Additional” row, which is for
other keyboard layouts that have been contributed to CLDR. The addition is the
Lithuanian Standard keyboard (LST 1582:2000, Information technology – Lithuanian
computer keyboard) found on [Lithuanian Keyboard
Layouts](http://www.unicode.org/cldr/charts/25/keyboards/layouts/lt.html)
(marked with /var).

## Specification changes

Some highlights:

*   For language and locale identifiers:
    *   Provided more detail on [conversion to/from BCP47
        identifiers](http://www.unicode.org/reports/tr35/tr35-35/tr35.html#BCP_47_Language_Tag_Conversion).
    *   Added a section on [private use
        codes](http://www.unicode.org/reports/tr35/tr35-35/tr35.html#Private_Use).
*   For number formatting:
    *   Removed the restriction on combining [significant
        digits](http://www.unicode.org/reports/tr35/tr35-35/tr35-numbers.html#sigdig)
        with minimum/maximum integer/fraction digit counts (implementations may
        still choose to restrict this).
    *   Clarified the behavior of cashRounding.
    *   Described the new
        [pluralRanges](http://www.unicode.org/reports/tr35/tr35-35/tr35-numbers.html#Plural_Ranges)
        structure.
    *   For [rule-based number
        formatting](http://www.unicode.org/reports/tr35/tr35-35/tr35-numbers.html#Rule-Based_Number_Formatting),
        described the common spellout rules and their usage.
*   In the [Date Field Symbol
    Table](http://www.unicode.org/reports/tr35/tr35-35/tr35-dates.html#Date_Field_Symbol_Table):
    *   Added symbol 'r' (for related Gregorian year).
    *   Noted that QQQQQ and qqqqq are used for narrow quarter and narrow
        stand-alone quarter respectively.
*   For collation:
    *   Expanded the list of CLDR collation algorithm features beyond those in
        the UCA.
    *   Specified the fallback sequence for collation types.
    *   Documented the range format for compact tailoring syntax, and that
        compact syntax can only be used for NFD-inert characters.
        \[#[6817](http://unicode.org/cldr/trac/ticket/6817),
        #[6738](http://unicode.org/cldr/trac/ticket/6738)\]
*   For keyboard data, clarified that the directories for specific platforms are
    only intended to contain the standard keyboards for those platforms; the
    "und" directory is for third-party additions, etc.

A more complete list is available in the
[Modifications](http://www.unicode.org/reports/tr35/tr35-35/tr35.html#Modifications)
section of *UTS #35: Unicode Locale Data Markup Language (LDML)*.

## Charts

The charts are updated for the new data. Some notable other changes or additions
are:

*   [Locale
    Coverage](http://www.unicode.org/cldr/charts/25/supplemental/locale_coverage.html)
    is a new chart, showing a summary of the coverage for each locale.
*   [Language Plural
    Rules](http://www.unicode.org/cldr/charts/25/supplemental/language_plural_rules.html)
    has plural ranges, additional or cleaned-up minimal pairs
*   [Likely
    Subtags](http://www.unicode.org/cldr/charts/25/supplemental/likely_subtags.html)
    shows the new macro languages and scripts
*   [Summary](http://www.unicode.org/cldr/charts/25/summary/index.html) has
    changed in format; all of the data for each base language (such as English
    (en) or Chinese (zh)) is displayed on the same page.

## BCP47 changes

*   Added collation parameter key "kv" (maxVariable, the last reordering group
    to be affected by ka-shifted), with possible values "space", "punct",
    "symbol, or "currency".
*   Added value for "nu" (number) key: "hanidays"
*   Deprecated values for "tz" (timezone) key: "aqams" (use "nzakl"), "camtr",
    "usnavajo" (use "usden")

## Coverage

The following chart shows the coverage for v25. (For a chart that shows the
increase in data over time, see [CLDR v24
Coverage](http://cldr.unicode.org/index/downloads/cldr-24#TOC-Coverage-improvements).)
The definition of the various levels of coverage increases over time, as new
structure and requirements are added. Three different coverage levels are shown
in the chart, from modern down to basic. The light lines show where data is
available, but unconfirmed.

For more details, see *LDML Part 6, Section 7 [Coverage
Levels](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-info.html#Coverage_Levels)*.

<iframe src="javascript:void(0);" width="800" height="400" allow="fullscreen"
/>document.getElementById('form513655734').submit();

## JSON data changes

CLDR 25 provides a JSON version of the complete set of CLDR 25 locale data.
Please be aware that the complete set of JSON is quite large, since it contains
all locales and all resolved fields. So we are publishing two zip files for
JSON, an abbreviated version containing only the "top-tier" locales as in
previous releases (json.zip) and also the complete set of JSON (json_full.zip).

## Tools

A major focus of CLDR 25 was improvements to tools, especially performance
Survey Tool performance. Those are not listed here, but the individual tickets
can be viewed by looking at the Changes in the table at the top. The Guava
library is now included with CLDR for use by CLDR tools.

## Migration

### Changes to plural/ordinal rules

*   **Cardinals (plurals)**
    *   **Russian:** CLDR 24 erroneously removed the “few” category; per
        #[6932](http://unicode.org/cldr/trac/ticket/6932), CLDR 25 restores
        “few” and reverts the integer rules to those from CLDR 23 (fractions
        were not supported in CLDR 23). There was no maintenance update for CLDR
        24, but CLDR members were notified and a CLDR 24 erratum was (belatedly)
        [posted](http://cldr.unicode.org/index/downloads/cldr-24#TOC-Known-Errors).
        ***Strings that used the CLDR 24 rules will need to translate for the
        “few” category.***
    *   **Filipino:** the set of keywords is the same, but the distribution is
        different. The chief reason was to account for the particle “na”. Older
        translations may work if they used “…⁠(na)⁠...” to work around the
        problem, but would be improved if they were retranslated. Probably only
        the "other" strings would be affected.
    *   **Manx:** there were some changes, but these probably will not affect
        many implementations.
*   **Ordinals (1st, 2nd, …)**
    *   Zulu: linguists agreed that the simpler form for ordinals is better.
        ***Strings that use ordinals will need retranslation.***
*   **Root**
    *   Added “root” to plurals and ordinals, to provide a fallback when no
        plural forms are provided explicitly.

#### Details

**Language** **Code** **Old Categories** **Action** **New Categories** **Integer
Changes** **Samples** Russian ru one, many, **other** SPLIT one, few, **many,
other** other➞few 2–4,22–24,32–34,42–44,… Filipino fil *one, other* CHANGED
*one, other* other➞one 2–3,5,7–8,10–13,15,17–18,20–23,25,27–28,… Manx gv one,
two, few, **other** SPLIT one, two, few, **many, other** other➞few 80 Zulu zu
**one, few, many, other** MERGED **other** few➞other 2–9

### Other

*   Renamed some values for the type attribute of the <contextTransformUsage>
    element for clarity, see
    [table](http://www.unicode.org/reports/tr35/tr35-35/tr35-general.html#contextTransformUsage_type_attribute_values):
    \[#[6857](http://unicode.org/cldr/trac/ticket/6857)\]
    *   changed "type" to "keyValue"
    *   changed "tense" to "relative"
    *   changed"displayName" and "displayName-count" to "currencyName" and
        "currencyName-count", respectively
*   Metazone subdivision for Mexico:
    *   In Mexico, "Pacific Zone" actually refers to the Mexico portion of the
        America_Mountain metazone, while the Mexico portion of the
        America_Pacific metazone is referred to inside Mexico as "Northwest
        Zone". To avoid confusion, two new metazones are added: Mexico_Pacific
        and Mexico_Northwest.
    *   CLDR 25 only includes translations of these for "de", "en", "es",
        "es_MX", "fr", "ja", "zh", and "zh_Hant". For other locales,
        applications should fall back to localized GMT format until more
        complete translations are available in CLDR 26.
        \[#[5957](http://unicode.org/cldr/trac/ticket/5957)\]
*   Locale codes:
    *   Language code “mo” is now replaced by “ro_MD” instead of “ro”.
        *   Note that language tag replacements may have multiple parts, such as
            "sh" ➞ "sr_Latn" or mo" ➞ "ro_MD". In such a case, the original
            script and/or region are retained if there is one. Thus "sh_Arab_AQ"
            ➞ "sr_Arab_AQ", not "sr_Latn_AQ". \[LDML [Likely
            Subtags](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html#Likely_Subtags)\]
    *   Removed language codes that are “collection codes”
    *   Removed deprecated timezone IDs corresponding to "aqams" (Amundsen-Scott
        Station, South Pole), "camtr" (Montreal, Canada), "usnavajo" (Shiprock,
        United States)
*   Collation:
    *   Deprecated the hiraganaQuaternary setting, implementations should use
        real quaternary relations instead.
        \[[#5015](http://unicode.org/cldr/trac/ticket/5015)\]
    *   Deprecated the variableTop setting and the \[variable top\] syntax,
        implementations should use the new maxVariable setting instead.
        [\[](goog_2107998906)#5016\]
    *   Characters that are not NFD-inert are now explicitly forbidden from the
        *compact* tailoring syntax. Implementations should replace any
        characters that are not NFD-inert.
        \[#[6738](http://unicode.org/cldr/trac/ticket/6738)\]
    *   Deprecated validSublocales and removed from data. Implementations should
        use the main inheritance hierarchy to determine validity.

## Key

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
