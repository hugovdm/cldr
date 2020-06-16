# CLDR 26 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs 26 2014-09-18
[v26](cldr-26.md) [CLDR26](http://unicode.org/Public/cldr/26/)
[Charts26](http://www.unicode.org/cldr/charts/26/)
[LDML26](http://www.unicode.org/reports/tr35/tr35-37/tr35.html)
[Δ26](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=26&group=component&max=999&col=id&col=summary)
` [ release-26](http://unicode.org/cldr/trac/browser/tags/release-26)` `
[ΔDTD26](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-26/common/dtd&old=HEAD@tags/release-25/common/dtd)`

## Overview

Version 26 added significant new data, with 77 locales now reaching the 100%
modern coverage level (see [§4 Coverage](cldr-26.md)). Collation data was
reorganized to use the new import feature, resulting in about 23% less source
data. Overall there was a growth of about 20% in data.

Changes include the following:

*   **Units:** Added 72 new units, added display names for all units and a new
    perUnitPattern (eg, liters per second).
*   **Collation:** Updated collation (sorting) to Unicode 7.0, moved Unihan
    radical-stroke collation into root to avoid duplication, used import to
    reduce source size by 23% and ease maintenance. Major changes to Arabic
    collation.
*   **Spell-out numbers:** improvements for round-trip fidelity; new syntax for
    use of plural categories.
*   **Specification:** documented new structure, \\x{h...h} syntax for Unicode
    code points; construction of “unit per unit” formats; clarified BCP47 and
    Unicode identifiers, and different kinds of locale lookup, matching, and
    inheritance. For more info, see
    [Modifications](http://www.unicode.org/reports/tr35/tr35-37/tr35.html#Modifications).
*   **Survey Tool:** Major improvements to the UI to make it easier and faster
    to enter and check data.

A major goal for the release was improving the submission tool UI to make it
easier for people to enter data, and to flesh out more of the measurement units.

**Totals**

submitters: 239 new submitted items: 312,418 new data: 135,045 changed data:
20,528

The new/changed data were items that appeared in the release, after reconciling
votes from different submitters. The number is thus lower than the number of
submissions.

The table at the top of this page lists the files for this release. For a
description of their purpose and format, and for the coverage graphic, see the
[Key](cldr-26.md). For a full list of ticketed changes, see the Delta link in
the table above. Most translation data is entered in through the Survey Tool,
and isn't ticketed.

## Structural additions and changes

### Units

For more information see [Unit Elements (LDML
spec)](http://www.unicode.org/reports/tr35/tr35-general.html#Unit_Elements) and
[Units (Translation Guidelines)](../../translation/units-1/units.md).

Under <unitLength type=“xx”><unit type=“xx”>, added the following

*   <displayName> element providing a display name of the given length type for
    the given unit (eg, *centimeters*).
*   Optional <perUnitPattern> element such as “{0} per hour” as an option
    (depending on grammar requirements) for constructing compound units such as
    “4.5 cm per hour”. \[#[6020](http://unicode.org/cldr/trac/ticket/6020)\]

Added 72 more unit types (beyond the 49 in CLDR 25) and data for them
\[#[7214](http://unicode.org/cldr/trac/ticket/7214)\]:

    acceleration meter per second squared proportion karat angle radian area square centimeter/inch/yard consumption liter per kilometer, mile per gallon digital (kilo/mega/giga/tera) bit/byte duration microsecond, nanosecond electric ampere, milliampere, ohm, volt energy calorie, Calorie, kilocalorie, joule, kilojoule, kilowatt-hour frequency (kilo/mega/giga) hertz length (deci/micro/nano) meter, nautical mile, astronomical unit, parsec;
    fathom, furlong light lux mass (milli/micro) gram, carat, metric ton, ton, troy ounce, stone power (milli/mega/giga) watt pressure millimeter of mercury, pound per square inch temperature kelvin volume (milli/centi/deci/hecto/mega) liter;
    cubic (centi) meter, foot, inch;
    teaspoon, tablespoon, fluid ounce, cup, pint, quart, gallon, bushel, acre foot

### Numbers

*   Under <numbers>, add <minimumGroupingDigits>. This can be used to indicate
    whether the locale suppresses grouping separators (such as thousands
    separators) below a certain value, so that for example the grouping
    separator is only used for values of 10000 and up. See [Number Elements
    (LDML
    spec)](http://www.unicode.org/reports/tr35/tr35-numbers.html#Number_Elements)
    and [Numbering Systems (Translation
    Guidelines)](../../translation/-core-data/numbering-systems.md).
*   Under <numbers>/<symbols>, add <timeSeparator>. This replaces any use of ":"
    in a date-time format pattern, which allows the same time format to be used
    for multiple number systems. For example, the time format for Arabic should
    be colon when using the Latin numbering system, but comma when using the
    Arabic numbering system.
    \[#[4254](http://unicode.org/cldr/trac/ticket/4254)\]

### RBNF

*   RBNF (spelling out numbers, such as “twenty-two”) can now make use of plural
    categories, allowing the rules to be more general and simpler, for example
    "$(ordinal,one{st}two{nd}few{rd}other{th})$" or
    "$(cardinal,one{миллион}few{миллионы}other{миллионов})$". The relevant
    syntax is defined by ICU and is documented in the RuleBasedNumberFormat
    class documentation. \[ICU
    #[10880](http://bugs.icu-project.org/trac/ticket/10880),
    #[11064](http://bugs.icu-project.org/trac/ticket/11064)\]

### Dates

*   Under <cyclicNameSets>, added <cyclicNameSet type="solarTerms”> for the
    24-name cycle of major and minor solar terms used in the Chinese lunar
    calendar, e.g. “spring begins”, “rain water”, “insects awaken”, “spring
    equinox”, ... \[#[7285](http://unicode.org/cldr/trac/ticket/7285)\]
*   Under <fields>:
    *   Added <field type=“quarter”> for e.g. “last quarter”.
        \[#[6042](http://unicode.org/cldr/trac/ticket/6042)\]
    *   Added -short and -narrow versions of most existing types (year, month,
        week, day, hour, minute, second, and the days sun..sat), for e.g. “3
        secs. ago” or “3s ago”.
        \[#[6702](http://unicode.org/cldr/trac/ticket/6702)\]
*   In date/time patterns, ':' can now act as a pattern character; if the number
    symbols for the number system in effect include a <timeSeparator> element,
    then the value of that element replaces the ':'; otherwise, the literal ':'
    is used. \[#[4254](http://unicode.org/cldr/trac/ticket/4254)\]

### Collation

*   The <collation> element "visibility='internal'" attribute-value has been
    deprecated. Collations have external visibility by default; a collation
    whose type name starts with "private-" is internal. For example, this can
    control which collations are displayed in a list of collation options for
    users to choose from. \[#[3949](http://unicode.org/cldr/trac/ticket/3949)\]

### Segmentation

*   Under <segmentation>, the <exceptions> element introduced in CLDR 24 has
    been deprecated and replaced with the <suppressions> element, which takes a
    type attribute, typically as <suppressions type="standard”>.
    \[#[7237](http://unicode.org/cldr/trac/ticket/7237)\]

### Supplemental

*   Under supplemental <codeMappings>, added <currencyCodes> table mapping ISO
    4217 3-letter currency codes to numeric codes.
    \[#[4764](http://unicode.org/cldr/trac/ticket/4764)\]
*   For the <languageAlias> element, the reason attribute supports additional
    values including the new "bibliographic".

## Data additions and changes

Aside from the large volume of additional data gathered through the survey tool
(see Coverage), the following specific changes have been made.

### Numbers

*   Changed fr_CH thousands separator to space.
    \[#[7238](http://unicode.org/cldr/trac/ticket/7238)\]
*   For Thai, changed symbol for THB from "฿" to "THB".
    \[#[7618](http://unicode.org/cldr/trac/ticket/7618)\]
*   For pt_PT, pt_CV, kea: Change currency formats for Escudo so the currency
    symbol is the decimal separator, e.g. "1,234$56".
    \[#[7670](http://unicode.org/cldr/trac/ticket/7670)\]

### RBNF

*   English ordinal rules now round-trip (format → parse recovers value)
    \[#[7829](http://unicode.org/cldr/trac/ticket/7829)\]
*   Russian, Polish and Belarusian now properly format and parse the numbers
    larger than 1000. \[#[5879](http://unicode.org/cldr/trac/ticket/5879),
    #[6774](http://unicode.org/cldr/trac/ticket/6774),
    #[7344](http://unicode.org/cldr/trac/ticket/7344),
    #[7680](http://unicode.org/cldr/trac/ticket/7680)\]
*   Other fixes for Indonesian, Ethiopic, and Spanish (Replaced many
    regional-variant rules with es_003.xml).
    \[#[6994](http://unicode.org/cldr/trac/ticket/6994),
    #[7204](http://unicode.org/cldr/trac/ticket/7204),
    #[6799](http://unicode.org/cldr/trac/ticket/6799)\]
*   For German, added many inflected forms.
    \[#[7384](http://unicode.org/cldr/trac/ticket/7384)\]

### Times and dates

*   Added availableFormats item for skeleton "E", typically mapping to pattern
    "ccc". \[#[7236](http://unicode.org/cldr/trac/ticket/7236)\]
*   Relative dates were changed to lowercase in additional languages, e.g. in
    German. \[#[7711](http://unicode.org/cldr/trac/ticket/7711)\]
*   Many specific changes, some of which are called out in the [relevant
    Migration Issues section](cldr-26.md) below.

### Timezones

*   Added new metazone "Apia" (Independent State of Samoa) and
    "Europe_Further_Eastern" (year-round UTC+3 zone in Russia and Belarus).
    \[#[7530](http://unicode.org/cldr/trac/ticket/7530)\]\[#[7317](http://unicode.org/cldr/trac/ticket/7317)\]
*   The English name for daylight time in the "Europe/Dublin" zone is changed
    from "Irish Summer Time" to "Irish Standard Time".
    \[#[10076](http://unicode.org/cldr/trac/ticket/10076)\]
*   In French, for summer time use “heure d’été “ instead of “heure avancée”.
    \[#[7717](http://unicode.org/cldr/trac/ticket/7717)\]
*   Also see [BCP47 changes](cldr-26.md) below.

### Other display names

*   Many new language names in English, mostly for use by Microsoft or
    translatewiki.net
*   Additional Script names and metadata for the new Unicode 7.0 scripts
*   Shortened English display names for some regions (e.g. from "Saint
    Barthélemy" to "St. Barthélemy")
    \[#[7777](http://unicode.org/cldr/trac/ticket/7777)\]

### Collation

*   Updated to Unicode 7.0. The root collation covers all new scripts and
    characters. \[#[7195](http://unicode.org/cldr/trac/ticket/7195)\]
*   Added import statements to reduce source size and improve maintenance.
    \[#[4246](http://unicode.org/cldr/trac/ticket/4246)\]
*   Revised search collators to import root search data rather than duplicating
    its rules. \[#[6578](http://unicode.org/cldr/trac/ticket/6578)\]
*   The root collation data files include data for Unihan radical-stroke order;
    and most of the mappings were removed from CJK type="unihan" tailorings,
    because they now can assume that the root collation order sorts Han
    characters in Unihan radical-stroke
    order.\[#[7176](http://unicode.org/cldr/trac/ticket/7176)\]
*   Major changes to Arabic collation. The previous collation is available as
    type="compat". Full details are available as comments in the collation
    source. \[#[4207](http://unicode.org/cldr/trac/ticket/4207)\]
*   Small changes to collation sequences for Danish, Finnish, Estonian, Maltese,
    and Malayalam. \[#[6615](http://unicode.org/cldr/trac/ticket/6615),
    #[6701](http://unicode.org/cldr/trac/ticket/6701),
    #[7023](http://unicode.org/cldr/trac/ticket/7023),
    #[7031](http://unicode.org/cldr/trac/ticket/7031),
    #[7486](http://unicode.org/cldr/trac/ticket/7486)\]

### Plurals

*   Expanded the number of locales with plural ranges to 73 (af, am, ar, az, bg,
    bn, bs, ca, cs, cy, da, de, el, en, es, et, eu, fa, fi, fil, fr, gl, gu, he,
    hi, hr, hu, hy, id, is, it, ja, ka, kk, km, kn, ko, ky, lo, lt, lv, mk, ml,
    mn, mr, ms, my, nb, ne, nl, pa, pl, pt, ro, ru, si, sk, sl, sq, sr, sv, sw,
    ta, te, th, tr, ug, uk, ur, uz, vi, zh, zu)
*   Added ordinals for 3 locales \[bs, dsb, hsb\], and cardinals to 2 locales
    \[dsb, hsb\]. Modifications for 2 locales.

### Segmentation

*   Updated the segmentation suppressions with new data from ULI for de, en, es,
    fr, it, pt, ru. \[#[10745](http://unicode.org/cldr/trac/ticket/10745)\]

### Transforms

*   The Lithuanian casing transforms (lt-Lower, lt-Title) are fixed to match the
    Unicode file SpecialCasing.txt
    \[#[7039](http://unicode.org/cldr/trac/ticket/7039)\]
*   Latin-Bopomofo no handles 'v' correctly.
    \[#[7598](http://unicode.org/cldr/trac/ticket/7598)\]

### Supplemental

*   Many new likely subtags; the generation also now ensures idempotency (within
    certain constraints)
*   The language matching fallback for Lao changed to English.
*   Some additions and fixes to "official" languages, populations, and literacy
    data.
*   Made islamic-umalqura be the preferred islamic calendar in Saudi Arabic and
    4 nearby countries. \[#[7592](http://unicode.org/cldr/trac/ticket/7592)\]
*   Updated weekend data for Algeria, Iran, Oman.
    \[#[10859](http://unicode.org/cldr/trac/ticket/10859)\]

### Misc.

*   Added MyanmarZawgyiConverter.java; now used to convert Zawgyi into Unicode
    when data is input. \[#[6977](http://unicode.org/cldr/trac/ticket/6977)\]
*   Almost all data now exported to ICU with the NewLDML2ICUConverter, including
    all bcp47 data, plus supplemental and alternates
    \[#[7808](http://unicode.org/cldr/trac/ticket/7808)\]
*   Updated scriptMetadata for new scripts in Unicode 7.0.
    \[#[6762](http://unicode.org/cldr/trac/ticket/6762)\]

## Coverage

The following shows the additional coverage in this release. The horizontal axis
shows the number of languages. The area between lines are the additional data
added in that release. The axis shows the percentage of modern coverage, as
measured for the v26 definition.

document.getElementById('form1327344284').submit();

The definition of “modern coverage” increases over time, as new structure and
requirements are added. This chart is using the most recent definition, but
applying it to previous versions. In late 2009 we introduced the coverage
levels, and thus the data starts to hit certain plateaux, one at 100% and one at
around 30%.The plateaux tend to “slump” because of plurals; that is, when a new
field with plurals is introduced, it counts as 1 missing string in Japanese
(with only one plural form), and 6 missing strings in Arabic (with six plural
forms).

For consistency, the current versioning convention is applied to versions 2.0
and previous; thus they appear as 20, 19, etc. The odd-numbered versions (25,
23, ...) tend to be consolidation releases, which don't have a major data
submission phase. Some languages don't quite hit 100% because of the way
coverage is measured.

The following chart shows the coverage levels for v26. The definition of the
various levels of coverage increases over time, as new structure and
requirements are added. Three different coverage levels are shown in the chart,
from modern down to basic. The light lines show where data is available, but
unconfirmed.

document.getElementById('form170511797').submit();

## Charts

The version 26 [Charts](http://www.unicode.org/cldr/charts/26/) have been
updated for the new data. There were some refinements to the locale data charts,
where all the regional locale values that are different are shown in the
**Sublocales** column, on the same row in the main language chart, such as for
[Spanish](http://www.unicode.org/cldr/charts/26/summary/es.html) \[es\].

## Specification changes

The specification changes are detailed in [LDML
Modifications](http://www.unicode.org/reports/tr35/tr35-37/tr35.html#Modifications).
Other than documentation of the new structure, there was a reorganization of
Section 3 to make the information about BCP47 extensions more accessible, and
there were many clarifications to the documentation: For example regarding BCP47
and Unicode identifiers; different kinds of locale lookup, matching, and
inheritance; \\x{h...h} syntax for Unicode code points; construction of “unit
per unit” formats.

## BCP47 changes

*   Deprecated key "kh" (collation parameter for special Hiragana handling).
*   Added collation ("co") type value: "compat"
*   Added timezone ("tz") type values: "aqtrl" (Antarctica/Troll), "ruchita"
    (Asia/Chita), "rusred" (Asia/Srednekolymsk)
*   Deprecated timezone ("tz") type values: "cnckg" (use "cnsha"), "cnhrb" (use
    "cnsha"), "cnkhg" (use "cnurc")

## Changes to JSON structure and data

No significant structural changes to the JSON data. All JSON data has been
regenerated to correspond to the XML as published in the 26 release.

## Survey Tool

*   Completely redesigned user interface - including a new "dashboard" feature
    that allows the user to "fix" problem areas
*   Ability to hide items already investigated
*   CSS webfont support for improving display of some languages
*   Improved many of the forum features, including multi-thread support for
    forum discussions.
*   Ability to flag high visibility items for CLDR TC review
*   Improvements to show differences between related sublocales ( such as de_DE
    vs. de_CH )
*   Many performance enhancements.

## Migration issues

The main "pain points" for migration have typically been changes in:

*   plural forms: since the categories are used for translation of system or
    application messages, and may require retranslation.
*   collation: because if sort keys are stored in a database, the database
    requires reindexing.
*   date/time/number formatting: typically only because of "Golden Data" tests;
    where people store a snapshot of formatted dates (for example), and compare
    results against that snapshot.

### Changes to plural/ordinal rules

Cardinals (0, 1, 2, …)

*   Portuguese (default = Brazilian) changes the plural category of 0 to
    singular (one).
*   This should not require retranslation, except where messages mask "one" with
    the explicit "=1", and where the message allows for zero 0 items (not
    "unused plural form").

Ordinals (1st, 2nd, …)

*   Ukrainian introduces the category *few* for 3,23,33,43,53,63,73,83,93...
*   This would require retranslation to add the messages for few, but only with
    ordinals, not cardinals.

### Changes to Collation

Collation has changed for Unicode 7.0, but also some small changes in certain
languages. There is a major change in Arabic; the previous comparison is
preserved for now under the tag "compat". See below for details.

### Changes in Date/Time/Number formatting

*   Changed fr_CH thousands separator to space.
    \[#[7238](http://unicode.org/cldr/trac/ticket/7238)\]
*   For Thai, changed symbol for THB from "฿" to "THB".
    \[#[7618](http://unicode.org/cldr/trac/ticket/7618)\]
*   nb/nn short date format changed from "dd.MM.yy” to "dd.MM.y" \[#7778\]
*   es_US, changed date formats to match es \[#10787\]
*   th, add era G to gregorian date formats \[#7784\]
*   Lithuanian date formats: use nominative month name LLL+ when the format does
    not include day number, avoid abbreviated month names (use numeric for
    medium format). \[#[7580](http://unicode.org/cldr/trac/ticket/7580),
    #[6909](http://unicode.org/cldr/trac/ticket/6909)\]
*   The English name for daylight time in the "Europe/Dublin" zone is changed
    from "Irish Summer Time" to "Irish Standard Time".
    \[#[10076](http://unicode.org/cldr/trac/ticket/10076)\]
*   In French, for summer time use “heure d’été “ instead of “heure avancée”.
    \[#[7717](http://unicode.org/cldr/trac/ticket/7717)\]

### Other Data changes

In the English locale, there were two changes that may require changes in Golden
Data tests:

*   “South-Eastern Asian” changed to ”Southeast Asia”
*   Some country names changed for more consistent use of & and St.
*   Replaced generic quotes ' and " by curly quotes “”‘’, or sometimes the
    letter modifier U+02BC.

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
