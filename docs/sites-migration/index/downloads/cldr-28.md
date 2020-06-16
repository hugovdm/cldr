# CLDR 28 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs 28 2015-09-17
[v28](cldr-28.md) [CLDR28](http://unicode.org/Public/cldr/28/)
[Charts28](http://www.unicode.org/cldr/charts/28/)
[LDML28](http://www.unicode.org/reports/tr35/tr35-41/tr35.html)
[Δ28](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=28&group=component&max=999&col=id&col=summary)
`[release-28](http://unicode.org/cldr/trac/browser/tags/release-28)`
`[ΔDTD28](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-28/common/dtd&old=HEAD@tags/release-27/common/dtd)`

## Overview

[TOC]

Unicode CLDR 28 provides an update to the key building blocks for software
supporting the world's languages. This data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks. The following summarizes the
main improvements in the release.

*   **General locale data.** Overall, about 5% of the data items in this release
    are new (see [Growth](cldr-28.md)), while about 8% have corrections. Notable
    changes include a major review of and improvement to Spanish locales for
    Latin America; the addition of two new “modern-coverage” locales (Belarusian
    and Irish); and moving certain data from en_GB to en_001 for improved
    quality and reduced data size in locales that use en_GB conventions.
*   **Formatting.** There are a number of new units and types of formats, with a
    major revision to the [day period
    rules](http://www.unicode.org/cldr/charts/28/supplemental/day_periods.html)—preferred
    for many languages instead of AM/PM (“10:30 at night”)—with localizations;
    the addition of compact formatting for currencies (“€10M”, “€10 million”),
    and the addition of more unit measures, including 7 new general units
    (duration-century), 21 new per-unit types, 4 new units for measuring
    personal age (needed for some languages), and new coordinate units for
    formatting latitude and longitude across languages (“10°N”).
*   **Identifiers.** The new features extend the ability to specify [subregions
    of
    countries](http://www.unicode.org/cldr/charts/28/supplemental/territory_subdivisions.html),
    validate identifiers, and customize locales, including the addition of
    subdivisions of countries, such as *Scotland* and *California* (localized
    names are not yet present, except for English); the addition of [validity
    data](http://unicode.org/cldr/trac/browser/tags/release-28/common/validity)
    for currency codes, measurement units, and locale identifier elements
    (allowing validation of Unicode language and locale identifiers without
    requiring BCP47 data); the addition of seven -u- extension keys and
    corresponding types to allow customization of locales (“cf” for specifying
    *standard* vs *accounting* currency formats), and the clarification of the
    specification of identifiers, especially for validity testing.

The [specification](http://www.unicode.org/reports/tr35/tr35-41/tr35.html) and
[charts](http://www.unicode.org/cldr/charts/28/) have also been updated.

## Structural additions and changes

### BCP47 changes

*   [Disallow unicode_language_subtags with 4
    letters](http://unicode.org/cldr/trac/ticket/8707), to facilitate
    distinguishing them from unicode_script_subtags.
    \[#[8707](http://unicode.org/cldr/trac/ticket/8707)\]
*   Add the unicode_subdivision_subtag to distinguish regions at a finer level
    than the ISO 3166-1 codes.
    \[#[8423](http://unicode.org/cldr/trac/ticket/8423)\]
*   Add variant for Portuguese Language Orthographic Agreement of 1990.
*   New keys and types for locale id -u- extension:
    *   key "cf" for currency format style ("standard" or "account").
        \[#[8052](http://unicode.org/cldr/trac/ticket/8052)\]
    *   key "fw" for first day of week for calendar display ("sun", "mon", ... ,
        "fri", "sat").
    *   key "hc" for hour cycle (0..11, 1..12, 0..23, 1..24).
    *   key "lw" for line break to specify CSS level 3 word-break options
        ("normal", "breakall", "keep all").
        \[#[8204](http://unicode.org/cldr/trac/ticket/8204)\]
    *   key "ms" to specify measurement system (metric, ussystem, uksystem).
        \[#[7168](http://unicode.org/cldr/trac/ticket/7168)\]
    *   key "sd" to specify region subdivision.
    *   key "ss" for sentence break to control use of suppressions data ("none"
        or "standard"). \[#[7032](http://unicode.org/cldr/trac/ticket/7032)\]
    *   for "nu", added math decimal numbering systems
        \[#[7098](http://unicode.org/cldr/trac/ticket/7098)\] and numbering
        systems new in Unicode 8.
        \[#[8881](http://unicode.org/cldr/trac/ticket/8881)\]

### Main locale data

*   localeDisplayNames
    *   New subdivisions/subdivision elements.
*   numbers:
    *   Compact currency formatting (“€10M”, “€10 million”)
        (<currencyFormatLength type="short">).
        \[#[5390](http://unicode.org/cldr/trac/ticket/5390)\]
    *   Defined number pattern field "¤¤¤¤¤" to designate narrow currency
        symbol.
*   dates
    *   Withdrew COLON as the pattern character designating the timeSeparator
        symbol. \[#[8905](http://unicode.org/cldr/trac/ticket/8905)\]
    *   dayPeriods translations:
        *   for formatting (“10 in the morning”) and
        *   for selection (“arrived yesterday morning”
    *   Defined new pattern characters b, B, and C to permit specification of
        dayPeriods in patterns.
        \[#[8862](http://unicode.org/cldr/trac/ticket/8862)\]
    *   availableFormats, additional standard date skeletons for MMMM:
        \[#[8537](http://unicode.org/cldr/trac/ticket/8537)\]
        *   "MMMMd"
        *   "yMMMM"
*   units
    *   new coordinateUnit/coordinateUnitPattern elements: north, east, south,
        west, for formatting latitude and longitude across languages (e.g.
        "10°N").
    *   many new <perUnitPattern> items for existing units, such as per
        area-square-centimeter ({0}/cm²).
    *   new units:
        *   angle-revolution ({0} rev)
        *   consumption-liter-per-100kilometers ({0} L/100km)
        *   duration-century (0} c)
        *   length-mile-scandinavian ({0} smi)
        *   speed-knot ({0} kn)
        *   volume-pint-metric ({0} mpt)
        *   volume-cup-metric ({0} mc)
        *   also duration-\*-person for languages such as Chinese, where \* is
            one of year, month, week, day
*   casingItem
    *   new forceErr attribute to force error instead of warning for unexpected
        casing in specific data items.
        \[#[8250](http://unicode.org/cldr/trac/ticket/8250)\]

### Supplemental data

*   New subdivisionContainment and subgroup, for representing subdivisions of
    countries/regions.
*   New subdivisionAlias, for (future) deprecation of subdivisions.
*   New idValidity for providing subtag validity data.

### DTDs

*   Certain metadata that was in supplemental data or tooling code has been
    moved into DTD annotations, providing a more visible and maintainable
    structure. The tooling has been modified to use this information directly:
    *   <!--@VALUE--> to indicate that an attribute is not distinguishing, and
        is treated like an element value.
    *   <!--@METADATA--> to indicate that an attribute is a "comment" on the
        data, like the draft status.
    *   <!--@ORDERED--> to indicate that an element's children are ordered.
    *   <!--@DEPRECATED--> to indicate that an attribute or element is
        deprecated.
    *   <!--@DEPRECATED:*attribute-value*--> to indicate that an attribute value
        is deprecated.
*   Deprecated several collation elements in favor of syntax in the cr element:
    *   import, settings, suppress_contractions, and optimize.
*   Deprecated and removed the <generation> element.
*   See
    [ΔDTD28](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-28/common/dtd&old=HEAD@tags/release-27/common/dtd)
    for details.

## Data additions and changes

*Data additions and changes that are more likely to cause migration issues are
listed in the [Migration](cldr-27.md) section below.*

*   General locale data
    *   New locales in common/main:
        *   Added several English locales for Europe and W Asia.
            \[#[8642](http://unicode.org/cldr/trac/ticket/8642)\]
    *   New locales in common/seed:
        *   cv, Chuvash \[#[8086](http://unicode.org/cldr/trac/ticket/8086)\]
        *   bgn, Western Balochi
            \[#[8275](http://unicode.org/cldr/trac/ticket/8275)\]
        *   mzn, Mazandarani
            \[#[8364](http://unicode.org/cldr/trac/ticket/8364)\]
        *   az_Arab (replacing azb), South Azerbaijani
            \[#[8437](http://unicode.org/cldr/trac/ticket/8437)\]
        *   sdh, Southern Kurdish
            \[#[8445](http://unicode.org/cldr/trac/ticket/8445)\]
    *   Moved to "modern" coverage level: be Belarusian, gd Irish.
    *   Major review of and improvement to Spanish locales for Latin America.
    *   Moved some data from en_GB to en_001 for improved quality and reduced
        data size in locales that use en_GB conventions.
    *   Improved consistency in casing across locales, mainly by moving to
        middle-of-sentence as much as possible; the context transforms data can
        be used to provide appropriate capitalization for different usage
        contexts. This change primarily impacted date/time symbols.
    *   Many updates to the supplemental <territoryInfo> providing information
        on language use by region.
*   RBNF (number spellout): Improvements to many rulesets, including fixing
    mistakes, and in various cases adding support for ordinals, fractions,
    and/or additional grammatical inflections: Arabic, Burmese, Danish, Finnish,
    Greek, Hebrew, Italian, Norwegian, Portuguese, Russian, Spanish, Thai,
    Turkish.
*   Date/time:
    *   Default calendar for Saudi Arabia is now islamic-umalqura.
        \[#[8665](http://unicode.org/cldr/trac/ticket/8665)\]
    *   [timeSeparator for "arab" digits is now colon, not Arabic
        comma](http://unicode.org/cldr/trac/ticket/8385).
        \[#[8385](http://unicode.org/cldr/trac/ticket/8385)\]
    *   Significant review and updating of the day period ranges for many
        locales. \[#[8387](http://unicode.org/cldr/trac/ticket/8387),
        #[8775](http://unicode.org/cldr/trac/ticket/8775) and others\]
*   Plurals
    *   Added plural rules for be, gd.
        \[#[8809](http://unicode.org/cldr/trac/ticket/8809)\]
*   Collation
    *   Updated to UCA 8.0.
        \[#[8311](http://unicode.org/cldr/trac/ticket/8311)\]
    *   Collation settings have been covered to ICU format.
        \[#[8289](http://unicode.org/cldr/trac/ticket/8289)\]
    *   Added collation for "bo" (same as for "dz").
        \[#[8506](http://unicode.org/cldr/trac/ticket/8506)\]
    *   Make native non-Latin script sort first for additional languages: am,
        chr, ka, lo, mn, ne.
        \[#[8575](http://unicode.org/cldr/trac/ticket/8575)\]
*   Segmentation
    *   Updated for Unicode 8. \[#8418\]
*   Transforms
    *   Added IPA transcription for Amharic (am), Kyrgyz (ky), Esperanto (eo)
        and Interlingua (ia).

## Growth

The following shows the additional coverage in this release.

<iframe src="javascript:void(0);" width="800" height="450" allow="fullscreen"
/>document.getElementById('form61982890').submit();

## Coverage

The following chart shows the coverage levels for this release.

<iframe src="javascript:void(0);" width="800" height="450" allow="fullscreen"
/>document.getElementById('form1570313520').submit();

## Charts

The version 28 [Charts](http://www.unicode.org/cldr/charts/28/) are updated for
the new data. There are also some changes in the charts themselves:

*   New [Verification](http://www.unicode.org/cldr/charts/28/verify/index.html)
    charts, showing the result of composing data for
    [Dates](http://www.unicode.org/cldr/charts/28/verify/dates/index.html),
    [Time Zones](http://www.unicode.org/cldr/charts/28/verify/zones/index.html),
    and
    [Numbers](http://www.unicode.org/cldr/charts/28/verify/numbers/index.html).
*   New [DTD
    Deltas](http://www.unicode.org/cldr/charts/28/supplemental/dtd_deltas.html)
    charts, showing the changes in DTD elements and attributes across releases.
*   New [Territory
    Subdivisions](http://www.unicode.org/cldr/charts/28/supplemental/territory_subdivisions.html)
    charts, showing the new CLDR subdivision data.
*   Improved navigation, with an Index link always going up one level.
*   Improved [Delta
    Data](http://www.unicode.org/cldr/charts/28/delta/index.html) charts, with
    more types of information.

## Specification changes

The following summarizes the main changes in the specification. The
specification changes are detailed in [LDML
Modifications](http://www.unicode.org/reports/tr35/tr35-41/tr35.html#Modifications).

*   Identifiers
    *   Enhanced the unicode language and locale identifiers, and their
        components.
    *   Added unicode_subdivision_subtag.
*   Structure
    *   Described new unicode subdivision items, including
        unicode_subdivision_subtag, validity data, and containment information.
        See Section [3.6.5 Subdivision
        Codes](http://www.unicode.org/reports/tr35/tr35-41/tr35.html#Unicode_Subdivision_Codes).
    *   Described new validity data for assessing the validity of unicode
        language/locale identifiers without requiring BCP47 data, and checking
        the validity of other identifiers, such as units. See Section [3.11
        Validity
        Data](http://www.unicode.org/reports/tr35/tr35-41/tr35.html#Validity_Data).
    *   Added string ranges for UnicodeSets and other data presentation.
*   For numbers,
    *   Described how a format with an explicit + can be derived from the CLDR
        data.
    *   Clarified the use of sequences of ¤ characters.
*   For dates,
    *   Clarified the matching process for getting from a skeleton (eg yMMMd) to
        a localized pattern (eg MMM d, yyyy).
    *   Added new day-period symbols b, B, and C to [Date Field Symbol
        Table](http://www.unicode.org/reports/tr35/tr35-41/tr35-dates.html#Date_Field_Symbol_Table).
    *   Added more examples of lenient parsing, such as “a.m.” vs “AM”.
    *   Clarified the ISO 8601 timezone formats.
*   Other
    *   Described new units of measure, and coordinateUnits (eg "10°N").
    *   Added descriptions of CLDR usage of the terms: [literacy
        percent](http://www.unicode.org/reports/tr35/tr35-41/tr35-info.html#literacy_percent),
        [language population
        percent](http://www.unicode.org/reports/tr35/tr35-41/tr35-info.html#language_population_percent),
        [writing
        percent](http://www.unicode.org/reports/tr35/tr35-41/tr35-info.html#writing_percent),
        [official
        language](http://www.unicode.org/reports/tr35/tr35-41/tr35-info.html#official_language),
        and [official regional
        language](http://www.unicode.org/reports/tr35/tr35-41/tr35-info.html#official_regional_language).

## Survey Tool

*   Survey Tool has been modified to allow translators to distinguish between a
    "vote for inherited" and a "hard" vote for a given item.

## Migration

The following are particular points that may need attention in updating to this
version.

*   DTD
    *   Various elements have been deprecated, and may need code or parser
        changes. In particular, the collation sub-elements import, settings,
        suppress_contractions, and optimize are deprecated. Use equivalent "ICU"
        syntax inside <cr> elements instead.
*   Locale identifiers
    *   CLDR now disallows
        `[unicode_language_subtag](http://www.unicode.org/reports/tr35/tr35-41/tr35.html#unicode_language_subtag)`
        values of length 4. None of these have been defined up to now, so it is
        a matter of updating parsers to be future-proof.
    *   Validity data for locale identifier elements moved from
        supplementalMetadata to separate files, with change in structure and
        more complete information.
*   Locale display names
    *   Name for language "ht" changed from "Haitian" to "Haitian Creole" (or
        equivalent) in en, de, fr.
        \[#[8855](http://unicode.org/cldr/trac/ticket/8855)\]
    *   Updated Japanese name for Georgia (affects name for region, language,
        currency, etc.). \[#[8451](http://unicode.org/cldr/trac/ticket/8451)\]
*   Numbers:
    *   Currency symbols changes in root
        *   Currency GEL (Georgian Lari): New LARI SIGN ₾ added as variant.
        *   Currency RUB (Russian Ruble): RUBLE SIGN ₽ moved from variant to be
            the default narrow form.
        *   Currency TWD (Taiwan Dollar): Default narrow form changed from NT$
            to $.
    *   Some other currencies were changed in particular locales, such as: in
        "az", currency AZN now uses the MANAT SIGN.
        \[#[8816](http://unicode.org/cldr/trac/ticket/8816)\]
*   Units
    *   Many short "per" forms were added, such as "per kilogram" that should be
        taken advantage of for better formatting of compound units.
*   Dates/times/calendars/zones:
    *   Withdrew COLON as the pattern character designating the timeSeparator
        symbol; note that currently there is no pattern character for
        timeSeparator.
    *   The [timeSeparator for "arab" digits is now back to colon, not Arabic
        d](http://unicode.org/cldr/trac/ticket/8385)ecimal separator as in ICU
        55. \[#[8385](http://unicode.org/cldr/trac/ticket/8385)\]
    *   The default calendar for Saudi Arabia changed from gregorian to
        islamic-umalqura. \[#[8665](http://unicode.org/cldr/trac/ticket/8665)\]
    *   Timezones Asia/Chongqing, Asia/Harbin, and Asia/Kashgar no longer have
        localizations.
    *   For day periods:
        *   The older ids for day periods such as {afternoon, earlyMorning,
            evening, weeHours...} have been replaced by the new ids {morning1,
            morning2, afternoon1, afternoon2, evening1, evening2, night1,
            night2}.
        *   Deprecated rule attributes 'at' (except for fixed periods), 'after',
            and 'to' and non-zero minutes/seconds, to allow for simpler
            implementations.
        *   The major cleanup and addition of day period information caused rule
            changes for most locales. Few implementations were using the
            previous data, so we don’t anticipate major migration issues.
*   Miscellaneous
    *   Many uses of hyphen between numbers were changed to en-dash, eg 123-456
        change to 123–456.
*   Postal Codes
    *   The deprecated postal codes have now been removed.
*   Plurals
    *   Ordinal rules for Irish and Belarusian have been added.

## Known issues

*   Invalid language codes in annotations/es_419.xml, annotations/zh_Hant.xml.
    \[#[8970](http://unicode.org/cldr/trac/ticket/8970)\]
*   Incorrect symbol in "en_AU" (using Arabic letters) for currency LBP,
    Lebanese Pound. \[#[8971](http://unicode.org/cldr/trac/ticket/8971)\]
*   Kazakh has swapped translations for North and South Korea.
    \[#[8977](http://unicode.org/cldr/trac/ticket/8977)\]
*   Spaces are missing in Gregorian-calendar standard long and medium date
    formats for "en_AU". \[#[9045](http://unicode.org/cldr/trac/ticket/9045)\]
*   The availableFormats patterns for MMMMd have the wrong order in "ar" for
    Generic/Islamic calendars and in "he" for Gregorian/Islamic calendars; the
    availableFormats patterns for yMMMM have the wrong order in "ms" for
    Gregorian/Generic calendars.
    \[#[9075](http://unicode.org/cldr/trac/ticket/9075),
    #[9110](http://unicode.org/cldr/trac/ticket/9110)\]
*   In the territory containment information in supplementalData.xml, territory
    "SS" is incorrectly listed as being contained in Northern Africa (015). The
    correct location is Eastern Africa (014).
    [\[#9068\]](http://unicode.org/cldr/trac/ticket/9068)

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
