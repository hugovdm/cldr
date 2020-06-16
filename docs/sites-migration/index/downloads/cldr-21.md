# CLDR 21.0 Release Note

The following are the files for this release. For a description of their purpose
and format, see the [Key](key.md); for more details see [CLDR Releases
(Downloads)](index.md).

No. Date Rel. Note Data Spec Delta CVS Tag **21.0** **2012-02-10**
**[Version21](cldr-21.md)** **[CLDR21](http://unicode.org/Public/cldr/21/)**
**[LDML21](http://www.unicode.org/reports/tr35/tr35-23.html)**
**[Changes21](http://unicode.org/cldr/trac/query?status=closed&milestone=21m1&milestone=21m2&milestone=21)**
**`[release-21](http://unicode.org/cldr/trac/browser/tags/release-21)`**

Unicode CLDR 21.0 contains data for 193 languages and 170 territories: 528
locales in all. This release did not include a public data submission phase, and
focused on improvements to the LDML structure and tools, and consistency of
data. Approximately 10,000 data items were removed, and 15,000 added (change in
value counts as a removal plus an addition).

## ****Features****

The main features include the following (see the Delta link above for a full
list of changes):

### Structural additions

*   Ordinal categories (1st, 2nd,…)
*   Context Transforms for context-dependent capitalization behavior.
*   Structure for support of Chinese lunar calendars
*   Gender of lists of people
*   Territory Containment of deprecated territories
*   ISO 8601 time zone formatting
*   Collation reordering (eg, putting Cyrillic before Latin)
*   Support of parent-locale data in supplemental data
*   Multiple number systems for locales.

### Data changes

*   Updates for Unicode 6.1 (segmentation, collation)
*   Major cleanup of timezone names and date format data; new timezone IDs
*   Abbreviated numbers (eg, “1.2 B” for 1,200,000,000)
*   Added South Sudan (new country)
*   Updated collations
*   Cleaned up delimiter data (“…” vs ”…” vs „…“ vs „…” vs «…» vs「…」…)
*   New default content locale for Arabic: **ar_001** (Modern Standard Arabic)
*   Deprecation and removal of whole-locale aliasing, and commonlyUsed elements.
*   Data for Chinese lunar calendar support.

### BCP47 Enhancements

*   The -t- BCP47 extension for transformed content
*   Enhanced number system support.

### SurveyTool

*   Major performance enhancements
*   New <metadata> element in locales for use by Survey Tool (eg, checking
    capitalization consistency)

### Release Numbering

The release numbering changed in this release, from x.y.z to xy.z. Thus the new
release number is 21.0 (rather than 2.1.0). This change was made to allow
implementations to use 2 numeric subfields for internal numbering, such as
21.0==.3.4==.

### Seed Locales

Locales with insufficient coverage were moved into the "seed" directory, and are
not part of the release. The data is available via SVN. There are now 16 such
languages and associated regions. When coverage for a seed language improves
sufficiently, it will be moved into the release.

## Specification

The changes to the specification are found at [LDML
Modifications](http://www.unicode.org/reports/tr35#Modifications). Main features
include:

*   Descriptions of the above features.
*   Many clarifications of existing features, such as the use of YY, h, H, K, k
    in date patterns and skeletons, restrictions on parentLocale, Windows TZID
    mapping, use of the region code 'UK', the status of non-decimal numbering
    systems
*   Deprecation of some structure, such as the 'l' (SMALL LETTER L) pattern
    character for leap month marker and the commonlyUsed element in formatting
    short time zone names.

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
