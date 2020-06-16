# CLDR 29 Release Note

No. Date Rel. Note Data Charts Spec Tickets SVN Tag DTD Diffs **29**
**2016-03-16** **[v29](cldr-29.md)**
**[CLDR29](http://unicode.org/Public/cldr/29/)**
**[Charts29](http://www.unicode.org/cldr/charts/29/)**
**[LDML29](http://www.unicode.org/reports/tr35/tr35-43/tr35.html)**
**[Δ29](http://unicode.org/cldr/trac/query?status=closed&status=reviewing&resolution=fixed&milestone=29&group=component&max=999&col=id&col=summary)**
`[release-29](http://unicode.org/cldr/trac/browser/tags/release-29)`
**`[ΔDTD29](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-29/common/dtd&old=HEAD@tags/release-28/common/dtd)`**

## Overview

[TOC]

Unicode CLDR 29 provides an update to the key building blocks for software
supporting the world's languages. This data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks.The following summarizes the
main improvements in the release:

*   **BCP47 extensions.** New keys for specifying transliteration and emoji
    presentation, and for customizing locales with region-specific settings;
    extra structure for complete validity testing.
*   **Transliterators.** Major cleanup, including BCP47 IDs for all transforms,
    simpler rule format, additional transforms and unit tests.
*   **Date/time.** Data on regional preferences for day periods such as “6:00 in
    the morning” and “7:00 in the evening”.
*   **Units.** New structure for choosing appropriate units based on locale and
    usage; new units for concentration and imperial gallons.
*   **Locales.** Added Cantonese, selected fixes to other locales.
*   **Emoji.** Enhanced emoji ordering, improved annotations (for more emoji and
    more locales).
*   **JSON Data.** Extended to include number spellout (RBNF) and script
    metadata.
*   **DTD:** Many enhancements to clarify usage.

The [specification](http://www.unicode.org/reports/tr35/tr35-43/tr35.html) and
[charts](http://www.unicode.org/cldr/charts/29/) have also been updated.

### **Summary of data items**

> added items 17.70% deleted items\* 3.26% changed items 2.92% *total items*
> 702,794

> *\* Sometimes a changed item appears as a deletion+addition. For details, see
> [Delta Data](http://www.unicode.org/cldr/charts/29/delta/index.html).*

## Structural additions and changes

### BCP47 -u and -t extension changes

*   New keys and types for locale id -u- extension:
    *   key "em" to use in a locale ID for controlling presentation of
        characters that may have either text or emoji presentation
    *   key "rg" to explicitly s"pecify the region for lookup of region-based
        data in supplemental info (e.g. preference for calendar, measurement
        units, etc.) instead of inferring that region from the region or
        language sub tags.
*   New timezone value "cafne" (for Fort Nelson, Canada).
*   New data for locale id -t- extension keys and types
    *   key "d0"
    *   key "s0"
*   In the extension data files, a new “value” attribute is available for the
    <key> element to provide more information about the value(s) that may be
    used with the key.

### Main locale data

*   Code updates: Updated to latest IANA data (BCP47, timezones), ISO data
    (subdivisions/currencies). Some specifics below.
    *   Changes to use of language, region and script codes:
        *   For Congo Swahili, use "sw_CD" instead of "swc"
        *   Remove translation of region AN, Netherlands Antilles
        *   Add support for pseudo-script code Zsye, used to specify emoji-style
            presentation
    *   New metazone "Pyongyang"
*   Measurement unit additions and changes
    *   "concentr-karat" (new, replaces "proportion-karat")
    *   "concentr-milligram-per-deciliter" (new)
    *   "concentr-millimole-per-liter" (new)
    *   "concentr-part-per-million" (new)
    *   "consumption-mile-per-gallon" (clarify that this is specifically for US
        gallon)
    *   "consumption-mile-per-gallon-imperial" (new)
    *   "proportion-karat" (removed, replaced by "concentr-karat")
    *   "volume-gallon" (clarify that this is specifically for US gallon)
    *   "volume-gallon-imperial (new)
*   Rule-based number formatting (RBNF)
    *   New syntax to permit rules to use locale-specific decimal separator
    *   Rules for infinity and NaN (not a number)

### Supplemental data

*   <timeData> preferences updated to include day periods b and B
*   Added new <unitPreferenceData> element, which maps several specific
    measurement unit usages to the specific unit or unit combination used for
    them in different locales.
*   Added new <rgScope> element to specify which data paths are affected by the
    value of a "rg" locale key.
*   Deprecated “after” in day period rules.

### DTDs

*   For the <key> element, a new value attribute.
*   For the <transform> element, new alias and backwardAlias attributes were
    added to facilitate mapping to BCP47-compatible IDs.
*   New supplemental <unitPreferenceData> and <rgScope> as noted above.
*   Enhancements to the DTD annotations to distinguish metadata elements and
    fine-tune value attributes: Regularized and corrected the usage of tags to
    provide more information about attributes (and elements): <!--@METADATA-->,
    <!--@VALUE--> , <!--@DEPRECATED-->

## Data additions and changes

*   Added data for new locale “yue”
*   Transforms
    *   Many new transforms were added.
    *   BCP47-compatible IDs were added as aliases for all transforms
    *   All of the rules and comments are now represented in a CDATA block
        inside a single <trule> element, instead of using separate <trule> and
        <comment> elements for each rule and comment respectively.
*   English names for Chinese calendar changed from "Month1", "Month2", ... to
    "First Month", "Second Month", ...
*   Emoji:
    *   Improved emoji collation
    *   Annotation data extended to more locales
*   Updated population/literacy data (from Worldbank, etc.).

## Growth

The following shows the additional coverage in CLDR 28; it will be updated soon
for CLDR 29.

<iframe src="javascript:void(0);" width="800" height="450" allow="fullscreen"
/>document.getElementById('form735344901').submit();

## Coverage

The following chart shows the coverage levels in CLDR 28; it will be updated
soon for CLDR 29.

<iframe src="javascript:void(0);" width="800" height="450" allow="fullscreen"
/>document.getElementById('form444172397').submit();

## JSON data

*   New to the JSON version of the data
    *   RBNF data
    *   script metadata

## Specification changes

*   Modified some locale id terminology to improve clarity:
    *   subdivision_attribute → unicode_subdivision_id
    *   unicode_subdivision_subtag → unicode_subdivision_suffix
*   Documented the use of the script tags "Zsym" and "Zsye" in Unicode locale
    identifiers as a way to control the presentation of characters that may have
    both a text-style and emoji-style presentation available: "Zsym" requests
    text style, "Zsye" requests emoji style.
*   Documented the new “value” attribute for the <key> element used in the data
    files for the -u and -t extensions, and improved the documentation of
    special values that are used in those files.
*   Added a new section with recommendations on handling invalid patterns (for
    date and number formatters)
*   For transforms, documented the new BCP47 aliases, and described the pivot
    mechanism to use when direct transforms are not available.
*   Documented more specifically which locale preferences depend on region
    alone.
*   Improved documentation of the plural rule syntax.
*   IMproved documentation on restrictions for and usage of day period rules.

## Migration

*   The measurement unit "proportion-karat" was renamed to "concentr-karat"
*   Transform rules and comments are now represented in a CDATA block inside a
    single <trule> element, instead of using separate <trule> and <comment>
    elements for each rule and comment respectively.
*   Deprecated “after” in day period rules.

## Infrastructure

*   Moved to cloud server, with build tasks run in parallel
*   Removed dependencies on Dojo
*   Enhanced import of subdivision data.
*   Updated to use Java 8.

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
