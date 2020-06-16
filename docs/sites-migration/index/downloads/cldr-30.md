# CLDR 30 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs
30.0.32016-12-02[v30](cldr-30.md)[CLDR30.0.3](http://unicode.org/Public/cldr/30.0.3/)[Charts30](http://www.unicode.org/cldr/charts/30/)[LDML30](http://www.unicode.org/reports/tr35/tr35-45/tr35.html)[Δ30.0.3](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&revw=!&milestone=30.0.3&group=component&max=999&col=id&col=summary&order=priority)[release-30-0-3](http://unicode.org/cldr/trac/browser/tags/release-30-0-3)[`ΔDTD30`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-30/common/dtd&old=HEAD@tags/release-29/common/dtd)
30.0.2 2016-10-17 [v30](cldr-30.md)
[CLDR30.0.2](http://unicode.org/Public/cldr/30.0.2/)
[Charts30](http://www.unicode.org/cldr/charts/30/)
[LDML30](http://www.unicode.org/reports/tr35/tr35-45/tr35.html)
[Δ30.0.2](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&revw=!&milestone=30.0.2&group=component&max=999&col=id&col=summary&order=priority)
[release-30-0-2](http://unicode.org/cldr/trac/browser/tags/release-30-0-2)
[`ΔDTD30`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-30/common/dtd&old=HEAD@tags/release-29/common/dtd)
30.0.1 2016-10-14 [v30](cldr-30.md)
[CLDR30.0.1](http://unicode.org/Public/cldr/30.0.1/)
[Charts30](http://www.unicode.org/cldr/charts/30/)
[LDML30](http://www.unicode.org/reports/tr35/tr35-45/tr35.html)
[Δ30.0.1](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&revw=!&milestone=30.0.1&group=component&max=999&col=id&col=summary&order=priority)
[release-30-0-1](http://unicode.org/cldr/trac/browser/tags/release-30-0-1)
[`ΔDTD30`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-30/common/dtd&old=HEAD@tags/release-29/common/dtd)
30 2016-10-05 [v30](cldr-30.md) [CLDR30](http://unicode.org/Public/cldr/30/)
[Charts30](http://www.unicode.org/cldr/charts/30/)
[LDML30](http://www.unicode.org/reports/tr35/tr35-45/tr35.html)
[Δ30](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=30&group=component&max=999&col=id&col=summary)
[release-30](http://unicode.org/cldr/trac/browser/tags/release-30)
[`ΔDTD30`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-30/common/dtd&old=HEAD@tags/release-29/common/dtd)

## Overview

[TOC]

Unicode CLDR 30 provides an update to the key building blocks for software
supporting the world's languages. This data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks. The following summarizes the
main improvements in the release:

*   Unicode support is updated to 9.0, including updated Unihan readings for the
    pinyin collation and Han-Latin transforms, and support for new script codes
    and number systems.
*   New
    [characterLabels](http://www.unicode.org/cldr/charts/30/by_type/miscellaneous.linguistic_elements.html#Character_Label)
    data can be used to generate labels for groups of related characters in
    character pickers.
*   The structure for emoji annotations has been revised, and the data has been
    [significantly
    updated](http://www.unicode.org/cldr/charts/30/annotations/index.html). The
    emoji collation has been updated, and data is added for improved
    segmentation behavior. Added a specification for synthesizing ZWJ sequence
    names.
*   The set of language codes for translation has been updated, with a
    significant increase in the total number of translated language names.
*   Substantial new data has been added for likely subtags (e.g., to get the
    main script for each language).
*   New data items have been added to support relative times such as “3 Fridays
    ago” or “this hour”.
*   New draft format and preference structure has been added to support week
    designations such as “the week of August 10” or “week 3 of March”.
*   The CLDR 30 Survey Tool [data collection](cldr-30.md) resulted in a net
    increase in data items of about 9.2%, with an additional 5.9% of items
    changed.

## Structural additions and changes

The new data fields being added to the release are:

> In locale data,
> new element
> **[<relativePeriod>](http://www.unicode.org/reports/tr35/tr35-45/tr35-dates.html#Calendar_Fields)**,
> new attribute **count** for
> **<dateFormatItem>**;
> In supplemental data,
> new element
> **[<weekOfPreference>](http://www.unicode.org/reports/tr35/tr35-45/tr35-dates.html#Week_Data)**
> For generated periods like “the week of August 10”. Data examples:
> <availableFormats>
> <dateFormatItem id="MMMMW" count=...>'week' W 'of' MMM</dateFormatItem>
> <dateFormatItem id="yw" count=...>'week' w 'of' y</dateFormatItem>
> ...
> <field type="week">
> <relativePeriod>the week of {0}</relativePeriod>
> **Note:** the structure and intended usage for these items is still being
> refined, see [Warnings and Errata](cldr-30.md). New [relative data
> items](http://www.unicode.org/reports/tr35/tr35-45/tr35-dates.html#Calendar_Fields)
> for weekdays,
> and for “this hour”, “this minute” Examples:
> <field type="sun">
> <relativeTime type="future">
> <relativeTimePattern count=...>in {0} Sundays</relativeTimePattern>
> ...
> <field type="hour">
> <relative type="0">this hour</relative> New [unit
> patterns](http://www.unicode.org/reports/tr35/tr35-45/tr35-general.html#perUnitPatterns)
> for
> “per square kilometer”, “per square mile” In locale data, new elements
> **[<characterLabel>](http://www.unicode.org/reports/tr35/tr35-45/tr35-general.html#Character_Labels)**,
> **[<characterLabelPatterns>](http://www.unicode.org/reports/tr35/tr35-45/tr35-general.html#Character_Labels)**
> To generate labels for groups of related characters in character pickers In
> [annotation
> data](http://www.unicode.org/reports/tr35/tr35-45/tr35-general.html#Annotations),
> new attribute **type** for **<annotation>,**
> deprecated attribute **tts** for **<annotation>** Restructured to make the
> difference clearer between short names (text-to-speech) and other keywords
> (for predictive typing, search, etc.). See detail below. New data file
> [ExtendedPictographic.txt](http://unicode.org/cldr/trac/browser/tags/release-30-0-2/common/properties/ExtendedPictographic.txt)
> Specifies property data for “future-proofing” [emoji
> segmentation](http://www.unicode.org/reports/tr35/#Extended_Pictographic).

The structure for annotations has changed to make processing simpler:

> OLD: <annotation cp='\[😀\]' tts='grinning face'>face; grin</annotation> NEW:
> <annotation cp="😀">face | grin</annotation>
> <annotation cp="😀" type="tts">grinning face</annotation

Other changes:

*   The formerly-deprecated [number
    symbols](http://www.unicode.org/reports/tr35/tr35-45/tr35-numbers.html#Number_Symbols)
    <currencyGroup> element was un-deprecated since it is needed for de_AT
*   The <transformNames> element and its subelements have been deprecated. In
    their stead, some additional key/type names are added.

For more details, see [DTD
Deltas](http://www.unicode.org/cldr/charts/30/supplemental/dtd_deltas.html),
[Modifications](http://www.unicode.org/reports/tr35/tr35-45/tr35.html#Modifications).

## Data additions and changes

### **Unicode 9**

Support was added for Unicode 9.0; this includes:

*   Updating to Unicode 9.0 Unihan data (significant kMandarin reading
    improvements) for the pinyin collation and Han-Latin transform
*   New script codes for Adlam, Bhaiksuki, Marchen, Newa, Osage
*   New numbering systems adlm, bhks, newa

### **Locale item codes and names**

Other updates for locale item codes and names, in addition to those for Unicode
9:

*   Some support for new region codes EZ, UN (though names for EZ are not
    available in languages other than English).
*   Support for new timezones uasf “Europe/Astrakhan”,rubax “Asia/Barnaul”,
    rukvx “Europe/Kirov”, rutof “Asia/Tomsk”, ruuly “Europe/Ulyanovs”.
*   Support for new Belarusian ruble code BYN.
*   Updated english names for bn/Beng “Bangla”, mic “Mi'kmaq”, or “Odia”.
*   Documented the use of script subtag “Zxxx” to indicate spoken or otherwise
    unwritten content.
*   The set of language and script names for which translations are requested
    was revamped, leading to a substantial increase in the number of such names.
*   Substantial new data has been added for likely subtags (e.g. to get the main
    script for each language).

### **Emoji**

**Note:** The emoji data items listed below were updated to cover the upcoming
[Emoji 4.0](http://www.unicode.org/reports/tr51/proposed.html) release, based on
a *draft* version of the emoji 4.0 data. The emoji 4.0 data may be revised after
CLDR 30 is released.

*   Emoji short names and keywords were fleshed out for nearly 80 languages.
*   Added data files to support improved and “future-proofed” text segmentation
    behavior for emoji.
*   Updated emoji collation.

### **Other**

Some other items of note:

*   Support for IANA timezone data through 2016g.
*   The time separator for Norwegian locales (nb, nn) was changed to be ‘:’
    throughout.
*   The preferred time cycle has been changed from 12- to 24-hour for several
    regions in southern Africa.
*   Number symbols (plus, minus, percent) and formats (currency, percent) were
    updated for ar, fa, he in an effort to produce better results. Note that
    depending on locale and numbering system, those number symbols and currency
    patterns may contain bidi controls LRM, RLM, and ALM. Use of the ALM is new
    in CLDR 30; CLDR clients who will be using this data on systems that do not
    yet support the bidi algorithm of Unicode 6.3 and later should map instances
    of ALM (U+061C) to RLM (U+200F).
*   Use “lei” as narrow currency symbol for Romanian Leu (RON).
*   Collation: Uzbek (uz) collation added, Church Slavic (cu) collation fixed,
    Czech (cs) search collation now uses the standard search collator.
*   Some number spellout (RBNF) fixes for French, Portuguese, Spanish, Hebrew,
    Vietnamese.
*   Transforms:
    *   Adds transform from Zawgyi-encoded Myanmar (Burmese) to standard Unicode
        representation.
    *   Adds transliteration of 9 Indic languages to Urdu and Arabic.
    *   Adds transliteration between Cherokee and IPA, used in transliteration
        of 21 languages to Cherokee.

## Growth

CLDR 30 included a Survey Tool data collection phase, and collection of
annotation data. The following shows the growth of locale-data over time.

<iframe src="javascript:void(0);" width="800" height="400" allow="fullscreen"
/>document.getElementById('form343939591').submit();

This graph does not include data outside of the main and annotations
directories, such as sorting order, transliterations, validity data, and so
forth. The following gives the total overview of the change in data items in
CLDR.

> added items 9.32% deleted items\* 0.12% changed items 5.90% *total items*
> 818,314

The measurement of the number of items is reflects the different ways that the
information is represented. A single data field (element or attribute value) may
result in multiple data items. For example, plural rules may be shared by
multiple languages, and a single data field contains all the languages to which
those rules apply. Sometimes a changed item appears as a deletion+addition, and
sequences of items (such as sort order) are not counted as different even if the
order changes. For more details, see the [Delta
Data](http://www.unicode.org/cldr/charts/30/delta/index.html) charts.

## JSON data

The JSON data has been enhanced to include dayPeriod data.
\[#[9029](http://unicode.org/cldr/trac/ticket/9029)\]

## Survey Tool

*   The Survey Tool is now hosted on Microsoft Azure.
*   The Survey Tool now shows a link to where inherited data is aliased from.
    \[#[9489](http://unicode.org/cldr/trac/ticket/9489)\].
*   Voting resolution has been changed within organizations so that the latest
    vote wins.
*   Added 8-vote requirement to et, fa, en_GB, en_AU.

## Specification changes

*   Documented the use of script subtag “Zxxx” to indicate spoken or otherwise
    unwritten content.
*   Documented the Unicode locale extension key "em" to control emoji
    presentation.
*   Described the DTD annotations used in CLDR.
*   Noted that number patterns may contain bidi controls.
*   Described how to handle fractional seconds S when matching skeletons and
    adjusting corresponding patterns.
*   Added a specification for synthesizing emoji ZWJ sequence names.

For details, see
[Modifications](http://www.unicode.org/reports/tr35/tr35-45/tr35.html#Modifications).

## Migration

Users of the annotation data need to move to the new structure, described above.

There are changes to the bidirectional control characters in number symbols and
number patterns for number systems 'arab' and 'arabext', and for number system
'latn' in some locales. These include use of the ALM (Arabic Letter Mark)
character, which was new in Unicode 6.3.

## Known Issues

### “Week of” structure

The structure and intended usage for the “week x of y” patterns is still being
refined and may change. This applies especially to dateFormatItems such as the
following:

<dateFormatItem id="MMMMW" count=...>'week' W 'of' MMM</dateFormatItem>
<dateFormatItem id="yw" count=...>'week' w 'of' y</dateFormatItem>

Areas of discussion include the use of the count attribute and the use of
ordinal vs. cardinal numbers.

### Emoji data

The emoji-related data in CLDR 30 is based on a draft version of emoji 4.0 data,
which may change before it is finalized.

### Emoji annotation short names

The process described in LDML 30 for synthesizing short names of emoji sequences
may be updated; if so, details will be provided here.

### Chinese stroke collation

Chinese stroke collation is missing entries for several basic characters. CLDR
32 reverts the stroke collation data to the CLDR 29 version; a complete fix for
the underlying problem is targeted for CLDR 33. See
#[10497](http://unicode.org/cldr/trac/ticket/10497),
#[10642](http://unicode.org/cldr/trac/ticket/10642).

### Other data errors

*   In locale “eu”, dayPeriod names need review and may be updated.
    \[#[9820](http://unicode.org/cldr/trac/ticket/9820)\]

### Errors fixed in Maintenance Releases

Several errors in CLDR 30 were fixed in the CLDR 30.0.1 and CLDR 30.0.2
Maintenance Releases, see below.

## ==CLDR 30.0.1 Maintenance Release==

Unicode CLDR 30.0.1 is a maintenance release that is intended to fix some
specific problems that were found shortly after CLDR 30 was published. If you
have already downloaded version 30 and are not impacted by any of the specific
issues mentioned below, then there is no specific need to upgrade from 30 to
30.0.1.

*   In locale “my”, the name for region “MM” incorrectly appends a parenthesized
    English name.
*   In locale “en_AU”, incorrect format for dateFormatItem with skeleton yMMMEd.
*   Some errors in the root grapheme and line break rules for Regional
    Indicators.
*   Several other fixes; for details on all of the fixes see
    [Δ30.0.1](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=30.0.1&group=component&max=999&col=id&col=summary)

## ==CLDR 30.0.2 Maintenance Release==

Unicode CLDR 30.0.2 fixes one more problem with currency formats for Arabic that
was discovered after CLDR 30.0.1 was published; for details see
[Δ30.02](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=30.0.2&group=component&max=999&col=id&col=summary)

## ==CLDR 30.0.3 Maintenance Release==

Unicode CLDR 30.0.3 addresses the following:

*   #[9924](http://unicode.org/cldr/trac/ticket/9924), incorrect data for number
    of Cantonese speakers in China
*   #[9925](http://unicode.org/cldr/trac/ticket/9925), Hani_Latn transform was
    not updated with Unihan 9.0 kMandarin readings

## Acknowledgments

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](../acknowledgments.md) page for a full listing.

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
