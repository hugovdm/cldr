# CLDR 22 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag **22** **2012-09-10**
**[Version22](cldr-22.md)** **[CLDR22](http://unicode.org/Public/cldr/22/)** **[
Charts22](http://www.unicode.org/repos/cldr-aux/charts/22/index.html)**
**[LDML22](http://www.unicode.org/reports/tr35/tr35-27.html)**
[**Changes22**](http://unicode.org/cldr/trac/query?max=900&milestone=22dsub&milestone=22dvet&milestone=22dres&milestone=22&order=id&col=id&col=summary&col=milestone&col=type&col=status&col=priority&col=component&revw=%21)
`[**release-22**](http://unicode.org/cldr/trac/browser/tags/release-22)`

Unicode CLDR 22.0 contains data for 215 languages and 227 territories—654
locales in all. The main focus for this release is to flesh out data items in
major languages and locales: yielding an increase of over 100% in the total
number of data fields. Other major features include the addition of keyboard
mapping data for different platforms, the new Zhuyin (Bopomofo) sort order for
Chinese, and script metadata. There are also enhancements to compact decimals
(such as formatting 1,000,000 as “1 million” or “1M”) for different languages
and to rule-based number formats (such as writing 423 as "four hundred and
twenty-three").

The table above points to the files for this release. For a description of their
purpose and format, see the [Key](cldr-22.md).

## Features

The main features include the following (see the Delta link above for a full
list of changes, aside from data additions and corrections):

### Data changes

*   Very significant increase in data
    *   Over 197,600 language-based data entries (new, revised, or confirmed)
        through the Survey Tool. Top languages were **French** (9,688),
        **Chinese** (8,379), **Indonesian** (6,561) and **Thai** (6,471); with
        89 others.
    *   Many missing translations added to locales: **Japanese, Arabic,
        Indonesian, Hebrew, Thai, Lao, Khmer, Dzongkha, Ewe, Nepali, Slovak,
        Amharic, Vietnamese, Sinhala, Estonian, Latvian, Catalan, Macedonian**,
        and many others.
    *   New language locales: Bosnian (Cyrillic), Kashmiri, Asturian, Tachelhit
        (Latin), Ossetic, Ngomba, Meta', Ngiemboon, Volapük, Kako.
    *   Over 300,000 data items added in this release; an increase of over 100%
        in the total number of data fields. This does not count inherited items,
        which would result in a much larger figure.
*   New or improved collation (sorting order): new Zhuyin (Bopomofo) collation
    for Chinese, the preferred collation order for many users of traditional
    Chinese; updated Thai collation.
*   Over 370 new files of [keyboard
    mappings](http://unicode.org/cldr/trac/browser/tags/release-22/keyboards),
    collected from publicly available data for four different platforms:
    Android, Chrome OS, OS X, and Windows.
*   Script metadata property values for all 107 scripts in Unicode: web-rank,
    sample characters, bidi-order, casing, spaces-used, etc.
*   For compact decimals (powers-of-ten notation), the addition of long forms
    (“1 million” vs “1M”) and plurals (“1 million” vs “2 millions”, used by many
    languages).
*   Significant vetting of rule-based number format data (such as writing 423 as
    "four hundred and twenty-three") to correct spellings and add missing data
    for common word inflections and some numeric values.
*   Many new region locales for existing languages, including new **en_150**
    locale for European English.

### Structural additions

*   [Structure for keyboard
    mappings](http://www.unicode.org/reports/tr35/#Keyboards), providing a
    format for interoperable interchange of keyboard data.
*   New short width for weekday names (e.g. Mo, Tu, We), useful for date/time
    formats with limited display space.
*   For compact decimals (powers-of-ten notation), the addition of long forms
    and plural categories.
*   Script metadata properties

### BCP47 enhancements (after CLDR 21.0)

*   Several new subtags for the -t- extension were added in CLDR 21.0.2:
    *   -k0: Keyboard transform, with [29 new subfields for distinguishing
        keyboards](http://unicode.org/cldr/trac/browser/tags/release-22/common/bcp47/transform_keyboard.xml),
        in addition to the language/locale.
    *   -i0: Input Method Engine transform
    *   -t0: Machine translation
    *   -x0: Private use

### Survey Tool

*   Over 200 enhancements or fixes.
*   Major rewrite for further performance enhancements.
*   Smoother navigation.
*   Votes recorded immediately for each item.
*   New Date/Time review for cross-checking date/time format.
*   Voting data preserved for use in future releases.
*   Improved examples, showing sample usage of data.
*   Many new tests of data consistency.

### Other tools and tests

*   Completely new LDML converter to convert CLDR data for ICU; converts many
    more data types, and designed to serve as the basis for conversion to other
    formats.
*   More rigorous tests, automated unit tests.

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
