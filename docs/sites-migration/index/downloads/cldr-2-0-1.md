# CLDR 2.0.1 Release Note

The following are the files for this release. For a description of their purpose
and format, see the [Key](cldr-2-0.md); for more details see [CLDR Releases
(Downloads)](index.md).

No. Date Rel. Note Data Spec Delta CVS Tag **2.0.1** **2011-07-18**
**[Version2.0.1](cldr-2-0-1.md)**
**[CLDR2.0.1](http://unicode.org/Public/cldr/2.0.1/)**
**[LDML2.0.1](http://www.unicode.org/reports/tr35/tr35-21.html)**
**[Changes2.0.1](http://unicode.org/cldr/trac/query?status=closed&milestone=2.0.1)**
**`[release-2-0-1](http://unicode.org/cldr/trac/browser/tags/release-2-0-1)`**

Unicode CLDR 2.0.1 contains data for 200 languages and 183 territories: 618
locales in all. This is a minor release, with no new translations. It includes
about 80 changes that were not ready for CLDR 2.0.

[TOC]

## ****Features****

The fixes include:

*   Collation for Bengali, Khmer, Thai, Assamese
*   Spellout numbers for French, Ewe; plurals for Breton, Irish, Tyap and Jju
*   General consistency of relative/future/past dates, units, and currencies.
*   General cleanup of items where value = type
*   The name of 419, used in es_419 "Spanish (Latin America)"
*   Inheritance of some varieties of en from en_GB (parentLocales)
*   Changing root linebreak rules to allow breaks between small kana and \\u30FC
*   Removal of commonlyUsed and most short metazone data
*   Additional description attribute for all bcp47 tags

See the Delta link above for a full list of changes.

## Specification

The changes to the specification are found at [LDML
Modifications](http://www.unicode.org/reports/tr35#Modifications).

## Errata

The test XML files are not yet available.

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
