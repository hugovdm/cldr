# CLDR 33 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs **DTD Δs** 33
2018-03-26 [v33](http://cldr.unicode.org/index/downloads/cldr-33)
==[CLDR33](http://unicode.org/Public/cldr/33/)==
[Charts33](http://www.unicode.org/cldr/charts/33/)
[LDML33](https://www.unicode.org/reports/tr35/tr35-51/tr35.html)
[Δ33](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=33&group=component&max=999)
[release-33](http://www.unicode.org/repos/cldr/tags/release-33/)
[`ΔDTD33`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-33/common/dtd&old=HEAD@tags/release-32/common/dtd)
[33](http://www.unicode.org/cldr/charts/33/supplemental/dtd_deltas.html)

## Overview

[TOC]

Unicode CLDR 33 provides an update to the key building blocks for software
supporting the world's languages. This data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks.

*This release had a limited submission phase.* The focus was on improvements to
emoji keywords and to the Odia and Assamese locales, addition of typographic
names data, and improvements to the structure for specifying keyboard layouts.

Improvements in this release include:

*   **Structure**
    *   New structure for typographicNames translations (such as terms for Bold,
        Italic, ...), with data for 33 locales.
    *   The structure for specifying keyboard layouts was significantly
        enhanced, with many new elements and attributes, and expanded syntax for
        some preëxisting attribute values. See spec for details:
        [Keyboards](https://www.unicode.org/reports/tr35/tr35-51/tr35-keyboards.html#Contents).
*   **Additional Translations/Data**
    *   Annotations (emoji keywords) for a limited set of locales had a full
        review (ar, en_GB, de, es, ja, ru).
    *   Two additional locales (Odia, Assamese) were brought up to Modern
        coverage level; some missing items were added in other locales.
    *   New typographicNames data added, with translations in 33 locales.
    *   Added 4 new transforms: fa-fa_FONIPA, ha-ha_NE, nv-nv_FONIPA,
        vec-vec_FONIPA.
    *   Added number spellout (RBNF) rules for sw (Swahili), ff (Fulfulde/Fula),
        qu (Quechua), lb (Luxembourgish), ccp (Chakma), su (Sundanese).
*   **Property files**
    *   The emoji property data file ExtendedPictographic.txt has been removed
        from CLDR data, since the contents are now part of the UTS #51 “Unicode
        Emoji” data file:
        [emoji-data.txt](https://www.unicode.org/Public/emoji/latest/emoji-data.txt).
    *   labels.txt was added for emoji categories and subcategories.
*   **Code Updates**
    *   Addition of new currency code MRU for Mauritania; replaces MRO.
    *   Updating of currency display names and narrow symbol for São Tomé &
        Príncipe Dobra (use standard names for STN, names showing older year
        range for STD).
    *   Subdivisions (including all new codes for China).
    *   Update timezone mappings for tzdata 2018c.
*   **Bug fixes**

For information on structural changes, see [Spec
Modifications](https://www.unicode.org/reports/tr35/tr35-51/tr35.html#Modifications).

For changes that may affect migration to this version, see
[Migration](cldr-33.md).

### Charts

The [charts](http://www.unicode.org/cldr/charts/33/) have been updated for the
v33 data. The [Delta
Data](https://www.unicode.org/cldr/charts/33/delta/index.html) will show a
number of changes in annotations that are due to the elimination of redundant
keywords: see [Growth](cldr-33.md).

There will also be new tab-separated-value files for loading the information
into spreadsheets rather than trying to scrape the charts that will be added to
==[CLDR33](http://unicode.org/Public/cldr/33/)==. Currently this is only for a
subset of the charts.

1.  by_type.tsv
2.  delta.tsv — locales w/ inheritance
3.  delta_supp.tsv — supplemental data (eg non locale)
4.  delta_summary.tsv — stats on #2 & #3

### Survey Tool

*   When collecting data for emoji names and annotations, the Survey Tool now
    has the capability to display its own images for emoji that may not yet be
    displayable on the user’s system.

### Other data additions and changes

Some of the fixes and additions include:

*   Locale data:
    *   Added English name for sr_ME, “Montenegrin”.
    *   The cardinal (plural) rules for Macedonian (mk) have been changed so
        that one➞other for {11}.
    *   New seed locale for scn (Sicilian), with plural rules.
    *   Added exemplar characters for ha_NE (distinct from ha), nv (Navajo), cho
        (Choctaw).
*   Supplemental data:
    *   Adjusted the territory containment data for some regions near the South
        Pole, following changes in [UN
        M49](https://unstats.un.org/unsd/methodology/m49/), so several of these
        now have new containing regions.
    *   Updated the `<territoryInfo>` GDP data for various regions.

For more information these and other bug fixes, see [detailed delta
charts](http://www.unicode.org/cldr/charts/33/delta/index.html) and the [list of
bug
fixes](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=33&group=component&max=999).

## Growth

Because v33 was not a data submission release, the chart for growth differs
little from that of the [CLDR 32 Release Note](cldr-32/index.md). Here are the
overall statistics:

addeddeletedchangedtotal0.76%0.83%0.71%1,641,316

The following files showed the largest number of raw changes:

*   annotations/as.xml, main/as.xml, annotations/ru.xml, main/br.xml,
    annotations/or.xml, annotations/br.xml, annotations/ga.xml

Two changes affected the statistics:

*   The keywords (in annotations) are being treated as sets for counting
    purposes.
    *   So old:{a | b | c} → new:{a | c | d | e} counts as one deletion and 2
        additions.
*   The keywords have also had some redundancies removed: if a keyword consisted
    entirely of other keywords, it was removed.
    *   So old:{a, a b, b} → new:{a, b}.

## Migration

*   **Plurals**: ordinal and cardinal rules have been added for scn. The
    cardinal (plural) rules for Macedonian (mk) have been changed so that
    one➞other for {11}. Should not cause migration issues.
*   The emoji property data file ExtendedPictographic.txt has been removed from
    CLDR data, since the contents are now part of the UTS #51 “Unicode Emoji”
    data file:
    [emoji-data.txt](https://www.unicode.org/Public/emoji/latest/emoji-data.txt).
*   Adjusted the territory containment data for some regions near the South
    Pole, following changes in [UN
    M49](https://unstats.un.org/unsd/methodology/m49/), so several of these now
    have new containing regions.

## Known Issues

1.  New macroregions
    *   UN M.49 now includes Sark (680) but ISO rejected the proposed ISO 3166-1
        code, so it is not included.
2.  “Week of” structure
    *   The structure and intended usage for the “week x of y” patterns is still
        being refined and may change. This applies especially to dateFormatItems
        such as the following:
        `<dateFormatItem id="MMMMW" count=...>'week' W 'of'
        MMM</dateFormatItem>`
        `<dateFormatItem id="yw" count=...>'week' w 'of' y</dateFormatItem>`
        Areas of discussion include the use of the count attribute and the use
        of ordinal vs. cardinal numbers. For more information see
        \[#[9801](http://unicode.org/cldr/trac/ticket/9801)\].
3.  Subdivision Names
    *   The draft subdivision names were imported from wikidata. Names that had
        characters outside of the language's exemplars were excluded for now.
        Names that would cause collisions were allowed, but marked with
        superscripted numbers. The goal is to clean up these names over time.
4.  Chinese stroke collation
    *   In CLDR 30 and 31, Chinese stroke collation was missing entries for
        several basic characters. CLDR 32 reverted the stroke collation data to
        the CLDR 29 version; a complete fix for the underlying problem is
        targeted for CLDR 34. See
        #[10497](http://unicode.org/cldr/trac/ticket/10497),
        #[10642](http://unicode.org/cldr/trac/ticket/10642).

## Acknowledgments

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](../acknowledgments.md) page for a full listing.

## Key to Header Links

Rel. Note a general description of the contents of the release, and any relevant
notes about the release Data a set of zip files containing the contents of the
release (the files are complete in themselves, and do not require files from
earlier releases -- for the structure of the zip file, see [Repository
Organization](http://cldr.unicode.org/index/downloads#Repository_Organization))
Charts a set of charts showing some of the data in the release. Spec the version
of [UTS #35: LDML](http://www.unicode.org/reports/tr35/) that corresponds to the
release Delta a list of all the bug fixes and features in the release, which be
used to get the precise corresponding file changes using
[BugDiffs](http://unicode.org/cgi-bin/bugdiffs.pl) SVN Tag the files in the
release, accessible via via [Repository
Access](http://cldr.unicode.org/index/downloads#latest_draft_version). *For more
details see [CLDR Releases (Downloads)](index.md)* DTD Diffs a diff of the DTD
source files DTD Δs a link pointing to a charts of changes in the DTDs over
time.

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
