# CLDR 32 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs **DTD Δs**
32.0.12017-12-08[v32](http://cldr.unicode.org/index/downloads/cldr-32)[CLDR32.0.1](http://unicode.org/Public/cldr/32.0.1/)[Charts32](http://www.unicode.org/cldr/charts/32/)[LDML32](https://www.unicode.org/reports/tr35/tr35-49/tr35.html)[Δ32.0.1](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=32.0.1&group=component&max=999)[release-32-0-1](http://www.unicode.org/repos/cldr/tags/release-32-0-1/)[`ΔDTD32`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-32/common/dtd&old=HEAD@tags/release-31/common/dtd)[∆DTD32](http://www.unicode.org/cldr/charts/32/supplemental/dtd_deltas.html)
32 2017-11-01 [v32](http://cldr.unicode.org/index/downloads/cldr-32)
[==CLDR32==](http://unicode.org/Public/cldr/32/)
[Charts32](http://www.unicode.org/cldr/charts/32/)
[LDML32](https://www.unicode.org/reports/tr35/tr35-49/tr35.html)
[Δ32](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=32&group=component&max=999)
[release-32](http://www.unicode.org/repos/cldr/tags/release-32/)
[`ΔDTD32`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-32/common/dtd&old=HEAD@tags/release-31/common/dtd)
[∆DTD32](http://www.unicode.org/cldr/charts/32/supplemental/dtd_deltas.html)

## Overview

Unicode CLDR 32 provides an update to the key building blocks for software
supporting the world's languages. This data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks.

Improvements in this release include:

*   Major contributions of main locale data for Chakma (ccp), Sindhi (sd), Odia
    (or), Kabyle (kab), Pashto (ps), Turkmen (tk), Norwegian Nynorsk (nn),
    Assamese (as), and others. See [Growth](index.md).
    *   Inclusion of four locales in *common* (from *seed*): Wolof, Tatar,
        Tajik, Chakma
*   Major additions for Emoji
    *   Emoji names and keywords updates for Unicode 10.0 (Emoji 5)
    *   Emoji keywords now in UCA order for consistency.
    *   English name and keywords updates as per Emoji Subcommittee
    *   Emoji collation update: emoji are now sorted between regular symbols and
        currency symbols. (Previously in v31, emoji were after all other
        characters.)
*   Import of draft subdivision names and language groups from
    [wikidata](https://www.wikidata.org). (See Known issues section blow)
*   Rule-based number formats for Indian English, Akan, Hindi (oblique),
    Cherokee; revisions to some others.
*   New numeric exemplars. For example, in zh: \[\\- , . % ‰ + 0 1 2 3 4 5 6 7 8
    9 〇 一 七 三 九 二 五 八 六 四\]
*   New “disjunctive” list style (eg “a, b, ==or== c”)
*   New availableFormats items for day periods (skeleton “`Bhm`” `→ pattern
    “h:mm B`” → “1:30 in the afternoon”)
*   Many fixes and small additions to certain preexisting data: day periods,
    date/time formats, Chinese collation / transliteration, transforms
*   Chinese stroke collation was reverted to the data from CLDR 29. See
    [Migration](index.md).

For information on structural changes, see [Spec
Modifications](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35.html#Modifications).

### Charts

The [charts](http://www.unicode.org/cldr/charts/32/) have been updated for the
v32 data, and there are two new charts:

*   [Language
    Groups](http://www.unicode.org/cldr/charts/32/supplemental/language_groups.html)
    — showing the new language groups
*   [Locale
    Coverage](http://www.unicode.org/cldr/charts/32/supplemental/locale_coverage.html)
    — showing the data coverage of locales, by Modern, Moderate, Basic, and
    Core.

### Survey Tool

*   The Moderate level has been changed to align with *content language*
    requirements.
*   A new Survey Tool Ref site is avaialbe for use as v32 release data
    reference: <http://cldr-ref.unicode.org/cldr-apps/>

For changes that may affect migration to this version, see
[Migration](index.md).

### Other data additions and changes

The following summarizes some of the other changes in non-locale data.

*   [charts/32/delta/bcp47.html](http://www.unicode.org/cldr/charts/32/delta/bcp47.html)
    *   Added CNH currency, Masaram Gondi numbering system (gonm).
*   [charts/32/delta/supplemental-data.html](http://www.unicode.org/cldr/charts/32/delta/supplemental-data.html)
    *   Added currency CNH
    *   Added currency changes from STD to STN, and PHP based on [iso-4217
        amendment](https://www.currency-iso.org/en/shared/amendments/iso-4217-amendment.html).
    *   Addition of some language codes, 202 macroregion, scripts, variants
    *   Changes to WZoneMapping mapping
    *   Some additional transforms.
    *   For language distance/matching, en-GB is now the best choice from the GB
        cluster. Eg, en-SA is closer to en-GB instead of enON
    *   Various updates / additions of language/territory data, GDP data
    *   Language Groups added
    *   Addition of plural or ordinal rules for for io, sd, or, ps, sd, tk.
        pt-PT now behaves differently.
    *   Added plural ranges for ak, as, io, or, ps, sd, tk.
    *   Added containment for 202
    *   Added explicit currency info for CNH, DKK, NOK, SEK
    *   Changed week data (min days, first day, preferred hours) for RU, NZ, GL
    *   Added day periods for ccp, cy
*   [charts/32/delta/transforms.html](http://www.unicode.org/cldr/charts/32/delta/transforms.html)
    *   Transform additions / fixes for blt→blt_FONIPA, cy→cy_FONIPA, de→ASCII,
        Hani→Latn, ...
    *   \[32.0.1\] Moved several BGN transforms from status “provisional” to
        status “contributed”.
        \[#[10728](https://unicode.org/cldr/trac/ticket/10728)\]

For more information, see [detailed delta
charts](http://www.unicode.org/cldr/charts/32/delta/index.html).

## Growth

The following gives the total overview of the change in data items in CLDR. Most
of the increase in data was from the addition of new locales, more emoji names
and keywords across many locales, and the import of draft
[wikidata](https://www.wikidata.org/) subdivision names. The following table
shows the increase in total CLDR data items (including locale-based and
non-locale-based) compared to the last release.

added items 18.62% deleted items\* 0.33% changed items 12.44% *total items*
1,318,816

*\* The measurement of the number of items is reflects the different ways that
the information is represented. A single data field (element or attribute value)
may result in multiple data items. For example, plural rules may be shared by
multiple languages, and a single data field contains all the languages to which
those rules apply. Sometimes a changed item appears as a deletion+addition, and
sequences of items (such as sort order) are not counted as different even if the
order changes.*

The following chart shows the increase in locale-based data over time.

document.getElementById('form1237620627').submit();

For more details, see the [Delta
Data](http://www.unicode.org/cldr/charts/32/delta/index.html) charts.

There is a new chart that shows the [current coverage
levels](http://www.unicode.org/cldr/charts/32/supplemental/locale_coverage.html)
for CLDR locales. The locales that are not as complete are marked 'seed', and
available in a separate CLDR source directory.

## Migration

*   **Plural rules**
    *   The plural rules for pt_PT changed to be different than pt (=pt_BR). The
        "one" case is now only the integer 1.
*   **Timezones**
    *   Persian (fa) localized GMT hour pattern contains bidi control character
        LRM before signs.
*   **Currencies**
    *   The new code for
        [STN](https://www.currency-iso.org/en/shared/amendments/iso-4217-amendment.html)
        (SAO TOME AND PRINCIPE) has been released, and will be valid as of
        2018-09-01. It is included in the release with that effective date.
        However, it was too late to provide names for the locales.
*   **Language/Region data**
    *   The UN code 202 (Sub-Saharan Africa) was added late in the process, and
        doesn't have names (except in English).
*   **Other**
    *   Chakma is the first CLDR locale that uses completely supplemental
        (non-BMP) characters, which may expose some bugs in implementations.
    *   Chinese stroke collation was reverted to the data from CLDR 29 as a
        short-term fix for problems introduced in CLDR 30 that resulted in
        missing entries for several basic characters. A complete fix for the
        underlying problem is targeted for CLDR 33. See
        #[10497](http://unicode.org/cldr/trac/ticket/10497),
        #[10642](http://unicode.org/cldr/trac/ticket/10642).

## Known Issues

1.  New macroregions
    1.  The UN code 202 (Sub-Saharan Africa) was added late in the process, and
        doesn't have names (except in English).
    2.  The UN is now including Sark (680) which didn't get into the release.
2.  “Week of” structure
    1.  The structure and intended usage for the “week x of y” patterns is still
        being refined and may change. This applies especially to dateFormatItems
        such as the following:
        `<dateFormatItem id="MMMMW" count=...>'week' W 'of'
        MMM</dateFormatItem>`
        `<dateFormatItem id="yw" count=...>'week' w 'of' y</dateFormatItem>`
        Areas of discussion include the use of the count attribute and the use
        of ordinal vs. cardinal numbers. For more information see
        \[#[9801](http://unicode.org/cldr/trac/ticket/9801)\].
3.  Subdivision Names
    1.  The draft subdivision names were imported from wikidata. Names that had
        characters outside of the language's exemplars were excluded for now.
        Names that would cause collisions were allowed, but marked with
        superscripted numbers. The goal is to clean up these names over time.
4.  German AM/PM \[reverted in CLDR 32.0.1\]
    1.  In CLDR 32, the German AM/PM symbols were changed from “vorm.”/“nachm.”
        to “AM”/“PM”. This was reverted in CLDR 32.0.1
        \[#[10735](https://unicode.org/cldr/trac/ticket/10735)\] but will be
        reconsidered in a future version of CLDR
        \[#[10789](https://unicode.org/cldr/trac/ticket/10789)\].

## Acknowledgments

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](../../acknowledgments.md) page for a full listing.

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
details see [CLDR Releases (Downloads)](../index.md)* DTD Diffs a diff of the
DTD source files DTD Δs a link pointing to a charts of changes in the DTDs over
time.

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
