# CLDR 27 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs 27.0.1 2015-03-30
[v27](cldr-27.md) [CLDR27.0.1](http://unicode.org/Public/cldr/27.0.1/)
[Charts27](http://www.unicode.org/cldr/charts/27/)
[LDML27](http://www.unicode.org/reports/tr35/tr35-39/tr35.html)
[Δ27.0.1](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=27.0.1&group=component&max=999&col=id&col=summary)
`[release-27-0-1](http://unicode.org/cldr/trac/browser/tags/release-27-0-1)`
NONE
27 2015-03-19 [v27](cldr-27.md) [CLDR27](http://unicode.org/Public/cldr/27/)
[Charts27](http://www.unicode.org/cldr/charts/27/)
[LDML27](http://www.unicode.org/reports/tr35/tr35-39/tr35.html)
[Δ27](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=27&group=component&max=999&col=id&col=summary)
`[release-27](http://unicode.org/cldr/trac/browser/tags/release-27)`
`[ΔDTD27](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-27/common/dtd&old=HEAD@tags/release-26/common/dtd)`

## Overview

[TOC]

Unicode CLDR 27 has been released, providing an update to the key building
blocks for software supporting the world's languages. This data is used by all
[major software systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for
their software internationalization and localization, adapting software to the
conventions of different languages for such common software tasks.

There was no Survey Tool data collection phase for CLDR 27. Instead, the release
focused primarily on stability—cleaning up data inheritance and making specific
fixes—as well as improvements to the JSON format of the data. Changes include
the following:

*   **Cleanup of region locales:** A major cleanup effort was undertaken to
    resolve gratuitous differences between region-specific locales and the
    parent from which they inherit. In regional locales, it was determined where
    the parent value was an acceptable replacement for a child-specific value
    which could then be removed, providing greater consistency in behavior in
    the various region locales. A special effort was made to clean up country
    names in certain locales.
*   **Changes to English inheritance:** As an outcome of the cleanup effort
    above, the inheritance model for English locales is now simplified, making
    all en_XX locales inherit from either “en” directly ( for current or former
    U.S. territories ), or from British-influenced “en_001 - World English”.
    This is also reflected in some changes for measurement systems. See the
    migration section below for a detailed description of “en_001”.
*   **Emoji:** Data for emoji annotations and an emoji collation were added, to
    accompany [Unicode Technical Report #51, Unicode
    Emoji](http://www.unicode.org/reports/tr51/).
*   **Collation:** There are new sort orders for emoji (as noted above), and an
    Austrian phonebook sort order. Scripts can be reordered individually, rather
    than only in specific groups. Fractional tertiary weights are now used that
    are lower than *common*, to allow shorter sort-keys with normal Hiragana
    letters.
*   **Specification:** The LDML specification has descriptions of new or
    modified structure, plus a number of fixes and clarifications. See
    [Modifications](http://www.unicode.org/reports/tr35/tr35-39/tr35.html#Modifications)
    for a list of changes.
    *   Improved documentation of locale inheritance and matching, bundle versus
        item lookup, and parent locale information.
    *   Extensive clarifications to the intended use of the language matching
        data.
    *   Explicit new definitions of Unicode identifiers, such as [Unicode
        Calendar
        Identifier](http://www.unicode.org/reports/tr35/tr35-39/tr35.html#UnicodeCalendarIdentifier),
        for use in citations.
*   **Charts:** The navigation within charts has been improved, and new ones
    added:
    *   [Day
        periods](http://unicode.org/repos/cldr-aux/charts/27/supplemental/day_periods.html),
        showing the new day period selectors.
    *   [Language
        Matching](http://unicode.org/repos/cldr-aux/charts/27/supplemental/language_matching.html),
        showing data for matching a user’s desired languages against an
        application’s supported languages.
    *   [Emoji
        Annotations](http://unicode.org/repos/cldr-aux/charts/27/annotations/index.html),
        showing provisional annotations in English and 21 other locales.
    *   [Collation
        Tailorings](http://www.unicode.org/cldr/charts/27/collation/index.html),
        showing a view of all the collation data in CLDR for different
        languages.
        *   The
            [Root](http://www.unicode.org/cldr/charts/27/collation/root.html)
            chart shows the new emoji collation (for input palettes).
    *   [Territory
        Information](http://unicode.org/repos/cldr-aux/charts/27/supplemental/territory_information.html),
        split out of [Language Territory
        Information](http://unicode.org/repos/cldr-aux/charts/27/supplemental/language_territory_information.html)
        for easier viewing.
    *   [Delta
        charts,](http://unicode.org/repos/cldr-aux/charts/27/delta/index.html)
        showing detailed changes from v26 to v27.
*   **JSON on github:** The JSON form of the data is now available on
    [Github](https://github.com/unicode-cldr/cldr-json), rather than being found
    through the above **Data** link.

The table at the top of this page lists the files for this release. For a
description of their purpose and format, and for the coverage graphic, see the
[Key](cldr-26.md). For a full list of ticketed changes, see the Delta link in
the table above. Most translation data is entered in through the Survey Tool,
and isn't ticketed.

## BCP47 changes

*   Added segmentation.xml, which defines a new key for controlling line break
    behavior per the CSS line-break property:
    *   “lb”, with type values “strict”, “normal”, and “loose”
*   Added collation (“co”) type value: “emoji”
*   Added timezone (“tz”) type value: “pgraw” (Pacific/Bougainville)

## Structural additions and changes

*Data additions and changes that are more likely to cause migration issues are
listed in the [Migration](cldr-27.md) section below.*

### For main locale data

*   Added the top-level **<annotations>** element, whose <annotation>
    subelements provide information about characters, currently focusing on
    emoji. This information can be used as an input aid, for example.
*   For **<contextTransform>** elements, defined a new value “no-change” to
    designate the case in which it is known that no change from the raw CLDR
    text (middle-of-sentence form) is needed.
*   Deprecated the standard ***validSublocales*** attribute everywhere; it
    allowed sublocales in a given tree to be treated as though a file for them
    were present when none in fact was. Now it is recommended to simply add
    empty “stub” files to specify which sublocales are valid.
*   There is an additional temperature-generic unit, which can be used where the
    context makes it clear whether Celsius or Fahrenheit are being used.

### For supplemental data

*   Added the **<unicodeVersion>** element which defines the version of the
    Unicode standard that is used to interpret data, particularly the data in
    UnicodeSets.
*   Allow multiple **<dayPeriodRuleSet>** elements, distinguished by a new
    ***type*** attribute. A <dayPeriodRuleSet> with type=“selection” provides
    the time period data used for selecting among phrases such as “Your email
    arrived yesterday evening” or “Your email arrived last night”.
*   For the **<measurementSystem>** element, added a new ***category***
    attribute. This is used to indicate the measurementSystem for a specific
    category such as temperature; this may be different than the default
    measurementSystem for a region.
*   For the **<alias>** element subelements languageAlias, scriptAlias,
    territoryAlias, variantAlias, and zoneAlias, the ***type*** and
    ***replacement*** attributes are now required.
*   Deprecated the **<postalCodeData>** element and its **<postCodeRegex>**
    subelement. The data was not being maintained and there are other sources of
    such information that are kept up to date.

## Data additions and changes

*Data additions and changes that are more likely to cause migration issues are
listed in the [Migration](cldr-27.md) section below.*

### Region sublocales, inheritance for English

*   Extensive cleanup of region sublocales (e.g. fr_CA and fr_CH, es_419 and
    es_MX) to eliminate gratuitous differences from parent locale data
*   Changed “en_001” to represent British-influenced “world English”; changed
    the inheritance for many locales that use British-influenced English to
    inherit directly from en_001 instead of directly or indirectly from en_GB.
*   Regularized certain spellings (like St.), spacing in currencies, interval
    formats (Nov 3 – 5)

### Emoji-related data

*   Added annotations data for emoji in several languages
*   Added data for a new “emoji” collation in root. Added a display name for it
    in English.

### Date/time symbols and formats

*   Added new standard availableFormats items for skeletons hmsv, Hmsv, hmv, Hmv
*   In several locales (ca, es, th) made more consistent distinctions between
    patterns using MMM vs MMMM or between patterns using E vs patterns using
    EEEE; where relevant, the MMMM patterns use 'de', the MMM patterns do not.
*   For Catalan, restored format wide month names with article (“de març”,
    “d’abril”) as in CDLR 23; the date patterns now handle them correctly (date
    formats with wide month use MMMM if d is present and LLLL otherwise).
*   For Chinese-calendar date formats in root, en, zh, and zh_Hant, patterns
    with year now include 'r' for related Gregorian year.
*   Add supplemental data for <dayPeriodRuleSet type="selection">.

### Collation

*   The CLDR 27 root collation order is still based on the UCA 7.0 DUCET, but
    with most of the Cyrillic contractions removed as in UCA 8.0. The Cyrillic
    tailorings have been updated.
*   New Austrian phonebook sort order and Emoji symbols sort order.
*   FractionalUCA.txt supports reordering of single scripts rather than groups
    of scripts. Implementations that support script reordering should base it on
    the script-first-primary boundaries and use the new reorder-reserved ranges.
    Some Recommended Scripts may share primary lead bytes.
*   FractionalUCA.txt tertiary weights: Some fractional root collation elements
    have below-common tertiary weights (e.g., 03), in particular to allow normal
    Hiragana letters to have common tertiary weights. This is the first time
    that the root collation data uses below-common tertiary weights.
*   Simpler handling of U+FFFE (merge separator); FractionalUCA.txt now uses
    common secondary & tertiary weights for its CE, rather than unique low ones.

### Line break variants

*   Defined a new -u- locale key for controlling line break tightness (how many
    break opportunities are available), and added English display names for
    these:
    *   “lb”, with possible values “strict” (fewer break opportunities, when
        long lines are okay),
    *   “normal”, and
    *   “loose” (more break opportunities, for small displays).
*   However, the CLDR line break rules have not been updated to support the
    additional break variants.
    *   For an example of where the rules are used, see ICU.

### Supplemental data

*   Regular updates to language/script/territory info (population, literacy,
    etc.) and likely subtags (which scripts / territories are defaults for
    languages).

## Growth

The following shows the additional coverage in this release. Because there was
no major data collection this release, the difference from the previous release
is very small.

*   The horizontal axis shows the number of languages. The area between lines
    are the additional data added in that release.
*   The vertical axis shows the percentage of modern coverage.

<iframe src="javascript:void(0);" width="800" height="450" allow="fullscreen"
/>document.getElementById('form464388373').submit();

The definition of “modern coverage” increases over time, as new structure and
requirements are added. This chart is using the most recent definition, but
applying it to previous versions. In late 2009 we introduced the coverage
levels, and thus the data starts to hit certain plateaux. The plateaux tend to
“slump” across versions because of plurals; that is, when a new field with
plurals is introduced, it counts as 1 missing string in Japanese (with only one
plural form), and 6 missing strings in Arabic (with six plural forms).

For consistency, the current versioning convention is applied to versions 2.0
and previous; thus they appear as 20, 19, etc. The odd-numbered versions (25,
23, ...) tend to be consolidation releases, which don't have a major data
submission phase. Some languages don't quite hit 100% because of the way
coverage is measured.

## Coverage

The following chart shows the coverage levels for this release.

*   The vertical axis is percent of modern coverage. Three different coverage
    levels are shown in the chart, **modern**, **moderate**, and **basic**.
    *   There are horizontal lines showing the **moderate target%** and the
        **basic target%**.
    *   The light lines show where data is available, but unconfirmed.
*   The horizontal axis is the number of languages in the *common* directory of
    CLDR. There are additional directories:
    *   *seed* for locales that have just started, and don't have enough data to
        be included here, and
    *   *exemplar* for locales that just have exemplar data (that is, the
        characters are used in the language).

The definition of the various levels of coverage increases over time, as new
structure and requirements are added (see [**Growth**](cldr-27.md)).

<iframe src="javascript:void(0);" width="800" height="450" allow="fullscreen"
/>document.getElementById('form1379800005').submit();

## Charts

The version 27 [Charts](http://www.unicode.org/cldr/charts/27/) have been
updated for the new data. Navigation has been improved, and some new charts have
been added.

*   [Day
    periods](http://unicode.org/repos/cldr-aux/charts/27/supplemental/day_periods.html),
    showing the new day period selectors.
*   [Language
    Matching](http://unicode.org/repos/cldr-aux/charts/27/supplemental/language_matching.html),
    showing data for matching a user’s desired languages against an
    application’s supported languages.
*   [Emoji
    Annotations](http://unicode.org/repos/cldr-aux/charts/27/annotations/index.html),
    showing provisional annotations in English and 21 other locales.
*   [Collation
    Tailorings](http://www.unicode.org/cldr/charts/27/collation/index.html),
    showing a view of all the collation data in CLDR for different languages.
*   [Territory
    Information](http://unicode.org/repos/cldr-aux/charts/27/supplemental/territory_information.html),
    split out of [Language Territory
    Information](http://unicode.org/repos/cldr-aux/charts/27/supplemental/language_territory_information.html)
    for easier viewing.
*   [Delta
    charts,](http://unicode.org/repos/cldr-aux/charts/27/delta/index.html)
    showing detailed changes from v26 to v27.

## Specification changes

The specification changes are detailed in [LDML
Modifications](http://www.unicode.org/reports/tr35/tr35-39/tr35.html#Modifications).
Other than documentation of the new structure, enhancements include:

*   Improved documentation of locale inheritance and matching, bundle versus
    item lookup, and parent locale information.
*   Extensive clarifications to the intended use of the language matching data.
*   For transform rules, documented the use of $ in contexts to mean “off the
    end of the string”
*   For number systems, document that “latn” is always an acceptable numbering
    system
*   Clarify usage of doubled or tripled ¤ (U+00A4) in currency patterns.
*   Clarify the construction of long (displayName) formats using the plural
    rules.

## Changes to JSON structure and data

All JSON data has been regenerated to correspond to the XML as published in the
27 release. Note: Per CLDR committee decision, all JSON data is now generated to
include only those data fields that are marked “draft='contributed'” or higher.
Unconfirmed or provisional data will not be included in the resulting JSON. This
is the same threshhold that is used by the [ICU Project](http://icu-project.org)
for consuming CLDR's data.

Beginning with the CLDR 27 release, the CLDR committee is pleased to announce a
restructuring of the published JSON data, in an attempt to make it more
consumable to the JavaScript development community. The JSON data has been
organized into installable packages, that can be installed using
[bower](http://bower.io). In addition, the JSON data packages are available via
[Github](http://github.com). To access the CLDR JSON data, please view our
[Github](http://github.com) repository at

*   <https://github.com/unicode-cldr/cldr-json>

## Survey Tool

No significant changes.

## Migration

The main “pain points” for migration have typically been changes in:

*   **plural/ordinal forms:** since the categories are used for translation of
    system or application messages, and may require retranslation.
*   **collation:** because if sort keys are stored in a database, the database
    requires reindexing.
*   **date/time/number formatting:** typically only because of “Golden Data”
    tests; where people store a snapshot of formatted dates (for example), and
    compare results against that snapshot.

### Changes to Inheritance

*   Changed “en_001” to represent British-influenced “World English”. English
    sublocales whose territory has a strong historical relationship with the
    U.S., or is a territory of the U.S. will continue to inherit the bulk of
    their locale data directly from “en” (U.S. English). Otherwise, the locale
    will inherit the bulk of its data from “en_001 - World English”. Locale
    “en_001 - World English” has the following general characteristics:
    *   British influenced spellings for units (i.e. “metre” instead of “meter”
        ).
    *   Celsius as the default temperature scale.
    *   European-style date ordering (“18 March” instead of “March 18”)
    *   12 hour clock
    *   No specifically recognized short timezone abbreviations.

### Changes to Collation

*   Cyrillic contractions moved from root to tailorings.
*   This is the first time that the FractionalUCA.txt root collation data uses
    below-common tertiary weights.
*   The FractionalUCA.txt collation element for U+FFFE (merge separator) now
    uses common secondary & tertiary weights, rather than unique low ones.
*   Implementations which support script reordering should be modified to
    reorder single scripts, not groups of scripts.

### Changes to Day Period types

*   The dayPeriodRule type values (other than am, pm, noon, midnight) have
    changed to a more generally useful set (there is not a 1-1 matchup):
    *   from: earlyMorning, morning, lateMorning, midDay, afternoon, evening,
        lateEvening, night, weeHours
    *   to: morning1, morning2, afternoon1, afternoon2, evening1, evening2,
        night1, night2

### Changes to measurementSystem

*   The default measurement system for the UK has been changed from "metric" to
    "UK" (Imperial). The situation in the UK is quite complex: see [Metrication
    in the United
    Kingdom](http://en.wikipedia.org/wiki/Metrication_in_the_United_Kingdom).
    Imperial units are used for many commonplace measures, while for others
    metric units are the norm. If their primary focus is on the latter,
    implementations have fewer problems if they revert the value to "metric".
    Note: the choice of which unit is used in which domain is complex: even with
    the metric system, in one country a person’s height may be expressed as
    188cm, while in another as 1.88m. CLDR is moving toward support of such
    context with the new category attribute, but more research is needed.

### Changes to Language Matching

*   There are a number of language rules that are used for last-resort
    fallbacks, such as Abkhazian→Russian. These were previously given inverted
    values (10 instead of 90), which caused them to be — in effect —
    inoperative. The values are now fixed, which means that they will now cause
    matches that didn't formerly occur.
*   Language matching among regions has been changed for the new inheritance
    structure in English, which will change some matches.

### Changes to Plurals/Ordinals

*   Assamese ordinal types are changed to be the same as Bengali. This should
    not cause migration problems, since the set of categories is identical.

### Changes in Date/Time/Number formatting

*   For Catalan, restored format wide month names with article ("de març”,
    "d’abril”) as in CDLR 23; the date patterns now handle them correctly (date
    formats with wide month use MMMM if d is present and LLLL otherwise).
*   For Chinese-calendar date formats in root, en, zh, and zh_Hant, patterns
    with year now include 'r' for related Gregorian year.

### Other Data changes

*   The cleanup of regional locales caused some general changes
    *   Regularized certain spellings (like St.), spacing in currencies,
        interval formats (Nov 3 – 5)
    *   General changes to the name for British Pound
    *   Spacing changes in Chinese units
    *   More consistent use of en-dash (intervals, also date ranges such as in
        Japanese era names in Swedish)
*   There were a large number of casing changes for Russian (scripts
    lowercased), Portuguese
*   Locale swc (Congo Swahili) has now been merged into locale sw_CD (Swahili;
    Congo - Kinshasa). See CLDR Ticket
    [#8079](http://unicode.org/cldr/trac/ticket/8079) for a detailed discussion
    on the rationale.
*   In English (en = en-US), the units/short plural forms for
    duration-hour/minute/second are changed to “hr”, “min”, and “sec”; en_001
    overrides this to keep using “hrs”, “mins”, and “secs”.
*   Misc. other changes, such as some Korean territory names.
*   Some metazone periods

## Known issues

*   In Afrikaans data, there is inconsistent use of periods for Gregorian format
    & stand-alone abbreviated month names
    \[#[8240](http://unicode.org/cldr/trac/ticket/8240)\].
*   In English (en), the narrow symbol for "volume-liter" inconsistently uses
    "l", through "L" is used elsewhere in "en"
    \[#[8296](http://unicode.org/cldr/trac/ticket/8296)\].

## [CLDR 27.0.1 Maintenance Release](#27-0-1)

Unicode CLDR 27.0.1 is a very small maintenance release
that is intended to fix some specific problems that were
found shortly after CLDR 27 was published. If you have
already downloaded version 27 and are not impacted by any of
the specific issues mentioned below, then there is no
specific need to upgrade from 27 to 27.0.1. All data
in common/main is identical between version 27 and version
27.0.1.

The following specific problems are addressed in CLDR
27.0.1

*   **Problems with language matching:** A
    significant problem was found in the way language
    matching data was being converted to ICU, which
    required an update to
    common/supplemental/languageInfo.xml, as well as the
    tooling used to convert data from CLDR to ICU. See
    [
    \[#8297\]](http://unicode.org/cldr/trac/ticket/8297)
*   **JSON Installation Problems**:
    *   When installing via NPM, need to use
        peerDependencies instead of dependencies, so
        that dependent packages will align at the same
        directory level as the installed package. See
        [
        \[#8301\]](http://unicode.org/cldr/trac/ticket/8301)
    *   [ 								\[#8302\]](http://unicode.org/cldr/trac/ticket/8302)The 								[ 								approved JSON packaging document](../../development/development-process/design-proposals/json-packaging.md) stated that 								the cldr-core package would contain 								"defaultContent.json", which would list the 								locale identifiers that were omitted from the 								JSON packaging because they were identical to 								the parent. This file was inadvertently omitted 								from the v27 distribution. See

## [CLDR 27.0.3 Maintenance Release (Github tag only)](cldr-27.md)

[The
](http://unicode.org/cldr/trac/ticket/8302)[
approved JSON packaging
document](../../development/development-process/design-proposals/json-packaging.md)
stated that                                                                 the
cldr-core package would contain
"defaultContent.json", which would list the
locale identifiers that were omitted from the
JSON packaging because they were identical to
the parent. This file should have been pushed to Github in the 27.0.1
Maintenance Release but was not. The file has been pushed to Github and all
packages have been tagged as 27.0.3. The only difference between 27.0.1 and
27.0.3 is the addition of defaultContent.json.

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
