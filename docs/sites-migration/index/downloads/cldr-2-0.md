# CLDR 2.0 Release Note

The following are the files for this release. For a description of their purpose
and format, see the [Key](cldr-2-0.md); for more details see [CLDR Releases
(Downloads)](index.md).

No. Date Rel. Note Data Spec Delta CVS Tag **2.0.0** **2011-05-25**
**[Version2.0.0](cldr-2-0.md)**
**[CLDR2.0.0](http://unicode.org/Public/cldr/2.0.0/)**
**[LDML2.0](http://www.unicode.org/reports/tr35/tr35-19.html)**
**[Changes2.0.0](http://unicode.org/cldr/trac/query?status=closed&milestone=2.0&milestone=2.0m1&milestone=2.0m2)**
**`[release-2-0](http://unicode.org/cldr/trac/browser/tags/release-2-0)`**

Unicode CLDR 2.0 contains data for 200 languages and 183 territories: 618
locales in all. In this release, there was a concerted effort to flesh out
modern coverage-level data for the top 55 languages, for an increase of over 45%
more data fields in those languages. Overall, there was an increase of over 20%
in the total number of data fields.

[TOC]

## ****Features****

*   Modified coverage levels to be data-driven, and fine-tuned the allocation
*   Added special indexing characters to CJK collations for stable index buckets
    (with radical, stroke-count, or pinyin)
*   Separated locales that are insufficiently fleshed out into /seed/ directory
    (available in the repository, but not the release)
*   Added explicit parent locales, to:
    *   prevent cross-script inheritance (such as no longer inheriting
        Simplified Chinese values in Traditional Chinese)
    *   add es-419 (Latin American Spanish) as a parent for Latin American
        locales, and pt_PT for African pt locales.
*   Added fallbackRegionFormat for improved timezone names
*   Added localeKeyTypePattern and variant script names (for Hans/Hant) for
    improved locale names
*   Plurals (see also [Plural
    Rules](http://unicode.org/repos/cldr-tmp/trunk/diff/supplemental/language_plural_rules.html))
    *   Added explicit count values of 0 and 1 for plural data
    *   Enhanced plural rules to allow for explicit lists, such as "n in
        1,3,5..14"
*   Added to the Key/Type Definitions
    *   calendar type "iso8601" for ISO dates
    *   number type "tamldec" for decimal Tamil numbers
*   Restricted the use of the <alias> element to only two circumstances: in
    root, and as whole-locale aliases
*   Currency
    *   Restricted currency signs in root to only very broadly recognized
        symbols
    *   Made U+20B9 INDIAN RUPEE SIGN the default symbol for INR in root
*   Added data for relative times (such as "3 days ago") with plural support
*   Deprecated and removed references in /common/main/

See the Delta link above for a full list of changes.

## Specification

The changes to the specification are found at [LDML
Modifications](http://www.unicode.org/reports/tr35#Modifications).

## Errata

The following features are not yet documented in the specification:

*   Some new metadata, notably parent locales (
    [#3938](http://unicode.org/cldr/trac/ticket/3938))
*   The special indexing characters added to CJK collations for stable index
    buckets (with radical, stroke-count, or pinyin)
    ([#3952](http://unicode.org/cldr/trac/ticket/3952))
*   Number formats need further specification (
    [#3935](http://unicode.org/cldr/trac/ticket/3935))

Other errata

*   In supplemental data there are typos in language codes for Himachali
    ([#3939](http://unicode.org/cldr/trac/ticket/3939)) and Kurdish
    ([#3947](http://unicode.org/cldr/trac/ticket/3947)).

For more information, see [Open
Tickets](http://unicode.org/cldr/trac/report/44).

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
    [BugDiffs](http://unicode.org/cgi-bin/bugdiffs.pl).)
*   The SVN Tag can be used to get the files via [Repository
    Access](http://cldr.unicode.org/index/downloads#latest_draft_version).

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
