# CLDR 34 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs **DTD Δs** 34
2018-10-15 [v34](http://cldr.unicode.org/index/downloads/cldr-34)
[CLDR34](http://unicode.org/Public/cldr/34/)
[Charts34](http://www.unicode.org/cldr/charts/34/)
[LDML34](http://www.unicode.org/reports/tr35/tr35-53/tr35.html)
[Δ34](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=34&group=component&max=999)
[release-34](http://www.unicode.org/repos/cldr/tags/release-34)
[`ΔDTD34`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-34/common/dtd&old=HEAD@tags/release-33-1/common/dtd)
[34](http://www.unicode.org/cldr/charts/34/supplemental/dtd_deltas.html)

## Overview

Unicode CLDR 34 provides an update to the key building blocks for software
supporting the world's languages. CLDR data is used by all [major software
systems](http://cldr.unicode.org/index#TOC-Who-uses-CLDR-) for their software
internationalization and localization, adapting software to the conventions of
different languages for such common software tasks.

CLDR 34 included a [full Survey Tool data collection
phase](https://www.unicode.org/cldr/charts/34/supplemental/locale_coverage.html),
adding approximately 6M of data overall, resulting in the following language
support:

**Count** **Support Target** 85 full UI and document content 4 general-purpose
document content
🆕: [Somali](https://www.unicode.org/cldr/charts/34/delta/so.html) (so),
[Javanese](https://www.unicode.org/cldr/charts/34/delta/jv.html) (jv) 18 basic
application requirements
🆕: [Tongan](https://www.unicode.org/cldr/charts/34/delta/to.html) (to),
[Konkani](https://www.unicode.org/cldr/charts/34/delta/kok.html) (kok),
[Maori](https://www.unicode.org/cldr/charts/34/delta/mi.html) (mi),
[Dzongkha](https://www.unicode.org/cldr/charts/34/delta/dz.html) (dz),
[Tatar](https://www.unicode.org/cldr/charts/34/delta/tt.html) (tt),
[Kurdish](https://www.unicode.org/cldr/charts/34/delta/ku.html) (ku),
[Xhosa](https://www.unicode.org/cldr/charts/34/delta/xh.html) (xh) ~100languages
with >500 data fields, but that don't satisfy the level definitions

🆕 is for languages reaching the level in this release. Tongan (to), Konkani
(kok), Dzongkha (dz), Tatar (tt) were already in ICU, while Sindhi (sd), Maori
(mi), Turkmen (tk), Javanese (jv), Interlingua (ia), Kurdish (ku), Xhosa (xh)
are being included for the first time in the upcoming [ICU
63](http://site.icu-project.org/download/63). The above counts are just for the
languages (with multiple entries for multi-script languages such as Serbian or
Chinese) — there are many additional regional locales.

Other notable changes include:

*   Data added for locales
    *   New units such as atmosphere, petabyte, and others.
    *   Many new emoji
        [keywords](https://www.unicode.org/cldr/charts/34/annotations/index.html)
        and corrections/refinements of previous keywords and names.
    *   New subdivision data (where available in Wikipedia).
    *   Many typographic terms such as “extrafina” (“ultra light”) for font UI
        interfaces
    *   New 'and' list, short and narrow 'or' lists.
    *   Many other changes depending on the locale: for details, see [Delta
        Data](http://www.unicode.org/cldr/charts/34/delta/index.html).
*   Japanese calendar era
    *   Changes to prepare for the new era starting 2019-05-01. This will affect
        most software shipping in Japan — *see [New Japanese
        Era](http://blog.unicode.org/2018/09/new-japanese-era.html).*
*   Other Emoji
    *   Updates from Emoji Subcommittee for collation and grouping, bringing
        similar emoji closer together — especially affecting smileys.
*   Specification
    *   *Section 3.2 [Unicode Locale
        Identifier](https://www.unicode.org/reports/tr35/tr35-53/tr35.html#Unicode_locale_identifier)*
        — Fixes to syntax, canonical form description, and relation to BCP47
    *   *Section 3.3 [BCP 47
        Conformance](https://www.unicode.org/reports/tr35/tr35-53/tr35.html#BCP_47_Conformance)*
        — Reorganized for clarity, introduced new terms *Unicode BCP 47 locale
        identifier* and *Unicode CLDR locale identifier*, and added a
        conversion.
    *   *Section 3.4 [Language Identifier Field
        Definitions](https://www.unicode.org/reports/tr35/tr35-53/tr35.html#Field_Definitions)*
        — Addition of special Qaag code for Zawgji, documented mis, mul, zxx,
        XA, and XB
    *   *Section 4.2.6 [Inheritance vs Related
        Information](https://www.unicode.org/reports/tr35/tr35-53/tr35.html#Inheritance_vs_Related)*
        — Added table to explain the relationship between Inheritance,
        DefaultContent, LikelySubtags, and LocaleMatching.
    *   *Part 2, Section 6 [Unit
        Elements](https://www.unicode.org/reports/tr35/tr35-53/tr35-general.html#Unit_Elements)*
        — Defined the syntax of unit identifiers.
    *   *Part 3, Section 5 [Language Plural
        Rules](https://www.unicode.org/reports/tr35/tr35-53/tr35-numbers.html#Language_Plural_Rules)*
        — Added a new section covering the language-independent explicit plural
        cases “0” and “1”
    *   *Part 4, Section 2.6.3 [Element
        intervalFormats](https://www.unicode.org/reports/tr35/tr35-53/tr35-dates.html#intervalFormats)*
        — Described how to synthesize intervalFormatItems for skeletons that
        combine date and time fields

For details, see [Detailed Specification Changes](cldr-34.md), [Detailed
Structure Changes](cldr-34.md), [Detailed Data Changes](cldr-34.md),
[Growth](cldr-34.md).

## Detailed Specification Changes

For detailed specification changes, see [LDML34
Modifications](https://www.unicode.org/reports/tr35/tr35-53/tr35.html#Modifications).

## Detailed Structure Changes

*   Calendar
    *   For supplemental calendar <era> elements, a new attribute “named”
        indicates whether the era has been assigned a name (part of preparation
        for Japan era transition). If false, the era will not be used in
        formatting. \[#[10750](https://unicode.org/cldr/trac/ticket/10750)\]
*   Units
    *   Added <displayName> as a subelement for <coordinateUnit>, to provide a
        name such as “cardinal direction” for any of the <coordinateUnitPattern
        > elements. \[#[9986](https://unicode.org/cldr/trac/ticket/9986)\]
*   Patterns
    *   Added short patterns for "at most" and "approximately" (the latter for
        use in smart number ranges)
        \[[#11046](https://unicode.org/cldr/trac/ticket/11046)\] (and data for
        main languages)
*   Misc
    *   Deprecated territoryCodes@internet
        \[[#11072](https://unicode.org/cldr/trac/ticket/11072)\]
    *   The telephone number data (telephoneCodeData.xml) has been deprecated
        and removed from CLDR.
        \[#[10383](http://unicode.org/cldr/trac/ticket/10383)\]

## Detailed Data Changes

*   Data additions and updates from Survey Tool data submission and vetting. For
    details see the [detailed delta
    charts](http://www.unicode.org/cldr/charts/34/delta/index.html).

In addition, the following changes were made. This is not complete: for a full
list see the [list of bug
fixes](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=34&group=component&max=999).

*   Calendar
    *   In supplemental calendar data for Japanese calendar, added era 236
        starting 2019-05-01 with attribute named="false"; in “root” and “ja”
        locales, added placeholder era names for era 236 (part of preparation
        for Japan era transition).
        \[#[10750](https://unicode.org/cldr/trac/ticket/10750)\]
    *   In supplemental calendar data for Japanese calendar, fixed invalid date
        values for some historic Japanese-calendar eras.
        \[#[11399](https://unicode.org/cldr/trac/ticket/11399)\]
    *   Changed the firstDay (first day of week for calendar display)...
        *   from Monday to Sunday for PT Portugal.
            \[#[10716](https://unicode.org/cldr/trac/ticket/10716)\]
        *   from Sunday to Monday for IE Ireland
            \[#[11192](https://unicode.org/cldr/trac/ticket/11192)\]
        *   from Saturday to Monday for MA Morocco.
            \[#[11052](https://unicode.org/cldr/trac/ticket/11052)\]
        *   from Sunday to Monday for TN Tunisia..
            \[#[11052](https://unicode.org/cldr/trac/ticket/11052)\]
    *   Changed weekend from fri-sat to sat-sun for MA Morocco, TN Tunisia.
        \[#[11052](https://unicode.org/cldr/trac/ticket/11052)\]
*   Date formatting
    *   Added intervalFormats for skeletons with era to gregorian and generic
        calendars for “root”, “en”, and “ja” locales (part of preparation for
        Japan era transition).
        \[#[11327](https://unicode.org/cldr/trac/ticket/11327)\]
    *   In Finnish, changed date formats to use either full or numeric months
        names, avoiding the abbreviated names (which are still available as
        symbols). \[#[10870](https://unicode.org/cldr/trac/ticket/10870)\]
    *   In Korean, fixed a problem in which many formatted dates in certain
        calendars (buddhist, japanese, minguo) displayed a doubled character for
        month “월월”. \[#[11347](https://unicode.org/cldr/trac/ticket/11347)\]
*   Currency codes and symbols
    *   Added “¤” as the symbol for unknown currency XXX. This used to be done
        by ICU in code, but it makes more sense to have the data in CLDR.
        \[#[11074](https://unicode.org/cldr/trac/ticket/11074)\]
    *   In Thai locale, changed the symbol for THB from “THB” back to “฿”.
        \[#[10316](https://unicode.org/cldr/trac/review/10316)\]
    *   Support new Venezuelan currency VES as the default starting from
        2018-08-20.
    *   Changed currency patterns for “az” (Latn, Cyrl) to put symbol at the end
    *   Added support for MVP as historic currency of Maldives.
*   Units
    *   Added units for concentr-percent (e.g. “25%)” and concentr-permille
        (e.g. “37‰”). The former may be able to replace some usages of the
        <percentFormats> in <numbers>; it provides different display widths and
        plural forms, through it does not include a number format and cannot
        vary by number system.
        \[#[10632](https://unicode.org/cldr/trac/ticket/10632)\]
    *   Added units for pressure-atmosphere (e.g. “1 atm”) and digital-petabyte
        (e.g. “10 PB”). \[#[10600](https://unicode.org/cldr/trac/ticket/10600),
        #[14075](https://unicode.org/cldr/trac/changeset/14075)\]
*   Plural rules
    *   Rules added for (cardinals) ia, sc ; (ordinals) gd, ia, sc
*   Emoji
    *   Reviewed and revised emoji names and keywords for most languages
        *   The survey tool voting process was adapted to support sets more
            naturally
    *   Updated the emoji ordering to group characters more naturally
        \[[#11227](https://unicode.org/cldr/trac/ticket/11227)\], ...
    *   Revised the derived name generation (for complex emoji) for more
        consistency with the new hair styles
*   Data Cleanup
    *   Modified the input processor for Kyrgyz
        \[[#10738](https://unicode.org/cldr/trac/ticket/10738)\] and Urdu
        \[[#10543](https://unicode.org/cldr/trac/ticket/10543)\]
    *   Improved the Zawgji detection/conversion for input to Survey Tool
    *   Fixed Dutch dayPeriod names to use correct apostrophes.
*   Misc
    *   Added fallbacks for "or" lists
        \[[#11254](https://unicode.org/cldr/trac/ticket/11254)\]
    *   Added English names for Pseudolocales
        \[[#10880](https://unicode.org/cldr/trac/ticket/10880)\]
    *   Cleaned up root parseLenient data
        \[[#11055](https://unicode.org/cldr/trac/ticket/11055)\]
    *   Deprecated the telephone number elements *and removed
        telephoneCodeData.xml from CLDR*
        \[[#10383](https://unicode.org/cldr/trac/ticket/10383)\]
    *   Changed default region for “ia” Interlingua from FR to 001 (World).
    *   Several corrections to number spellout rules for Hungarian.
    *   Added Uighur to IPA transliterator
        \[[#11318](https://unicode.org/cldr/trac/ticket/11318)\]
    *   Added data for England, Scotland, Wales (now done with Survey Tool
        \[[#10252](https://unicode.org/cldr/trac/ticket/10252)\])
    *   The French locale now uses narrow no-break space U+202F is several
        places: as the numeric grouping separator, in many short unit patterns,
        and in the locale display name patterns. It also changed normal space to
        no-break space U+00A0 in the wide unit patterns.

## Growth

The following summarizes the number of changes (additions + corrections) for
languages in the release.

**Lang.** **Changes** **Examples** 12 2,000–5,000
[Pashto](https://www.unicode.org/cldr/charts/34/delta/ps.html),
[French](https://www.unicode.org/cldr/charts/34/delta/fr.html),
[Chinese](https://www.unicode.org/cldr/charts/34/delta/zh.html), … 27
1,000–1,999 52 500–999 48 50–499

The following shows languages with a larger relative number of changes. For the
first line, there are over 20% additions alone, not counting corrections.

**Lang.** **Changes** **Examples** 4 ≥ 20% Pashto, Maori, Uzbek (Arabic), and
Punjabi (Arabic) 5 ≥ 50% Interlingua, Fulah (Adlam), Somali, Javanese, and Maori

TBD: add chart

## Migration

*   French grouping separator changed from no-break space U+00A0 to narrow
    no-break space U+202F.
*   The telephone number data (telephoneCodeData.xml) has been deprecated and
    removed from CLDR. \[#[10383](http://unicode.org/cldr/trac/ticket/10383)\]
*   Locale codes has been changed for Ff (Fular) locales to include the script
    tag Latn in anticipation of expected Adlam support in the upcoming release.
    (e.g. ff_CM has been renamed to ff_Latn_CM).

## Known Issues

(These may addressed in a maintenance update)

*   For en_AU, the timeSeparator symbol has '.', while the actual time formats
    use ':'. \[#[11462](https://unicode.org/cldr/trac/ticket/11462)\]
*   In several locales (en, kl, ksh) the symbol for NaN is “¤¤¤” which in
    incorrect in that it uses number format pattern characters, and thus causes
    problems for currency parsing.
    \[#[11492](https://unicode.org/cldr/trac/ticket/11492)\]
*   For pt_PT, the compact decimal currency formats have the curency symbol at
    the beginning, which is inconsistent with standards currency patterns.
    \[#[11295](https://unicode.org/cldr/trac/ticket/11295)\]

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
