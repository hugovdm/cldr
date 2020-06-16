# CLDR 1.9 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases (Downloads)](index.md).

No. Date Rel. Note Data Spec Delta CVS Tag Errata **1.9** **2010-12-01**
**[Version1.9](cldr-1-9.md)**
**[CLDR1.9](http://unicode.org/Public/cldr/1.9.0/)**
**[LDML1.9](http://www.unicode.org/reports/tr35/tr35-17.html)**
**[Changes1.9](http://unicode.org/cldr/trac/query?status=closed&order=priority&milestone=1.9m1&milestone=1.9m2&milestone=1.9RC)**
**`[release-1-9](http://unicode.org/cldr/trac/browser/tags/release-1-9)`** *see
[below](#Errata)*

Unicode CLDR 1.9 contains data for 187 languages and 166 territories: 516
locales in all. This version did not did not have a translation cycle: the focus
was on improving tooling and structure, changes in collation, and data
consistency. The new features include:

### Collation

1.  ****Tailored UCA DUCET.** In a major change, the base ordering for all
    locales is no longer the unmodified UCA 6.0 collation table (DUCET).
    Instead, modified tables are used as described in
    [CollationAuxiliary.html](http://www.unicode.org/Public/UCA/6.0.0/CollationAuxiliary.html).
    This allows implementations to provide customized reordering of scripts,
    symbols, and numbers in sorted lists.**
2.  **Updated Pinyin and Radical stroke collations.** The collations for pinyin,
    stroke, and radical-stroke were all updated to be based on the Unicode 6.0
    [Unihan](http://unicode.org/reports/tr38/) data, with some small additions.
    This affected Chinese (S&T), Japanese, and Korean.
3.  **Locale-specific updates and fixes:** Over 44 other languages had changes
    in collation. In most cases the changes were minor; often confirming
    collation sequences that had been draft. In some cases there were
    significant enhancements or corrections.
4.  **Removing “backwards secondaries”.** The default of "backwards secondaries"
    has been removed from the few locales that had it, allowing for improved
    performance. The one exception to this remains fr-CA.
5.  **Import statements.** Collation rules allow an “import” statement, for size
    reductions in the source strings, better maintenance, and future use of the
    default European Ordering Rules for languages of the European Union.
6.  **Search collators.** Search collators were added, with rules for
    language-specific matching.

### Transliteration

1.  **pinyin transliteration tables:** now based on Unicode 6.0
    [Unihan](http://unicode.org/reports/tr38/) data.
2.  **variant pinyin transliterator:** added for name transliteration.
3.  **language-language transliterators:** many contributed from [Google
    Maps](http://google-opensource.blogspot.com/2010/10/greetings-from-santa-kurara-kariforunia.html).

### Structure

1.  **ellipsis pattern:** for indicating truncation of strings (initial, medial,
    or final).
2.  **moreInformation string:** for indicating when more information is
    available
3.  **punctuation exemplars:** including the punctuation characters customarily
    used with the language
4.  **transformNames:** for localized names of transforms
5.  **abbreviated number patterns:** allowing "3M" for 3,000,000.
6.  **number formats:** for different numbering systems (such as Latin, Arabic,
    Hindi, etc.)

### Data

The data was reviewed for consistency, and a number of changes were made. A a
few selected additions were made, such as date formats and plural rules. There
were also significant updates to the language-territory information, and some
changes to bring the data in line with BCP47. There were updates for Unicode
6.0, such as the default segmentation rules, and collation (mentioned above).
The Thai grapheme break iterator was also fixed. Because 1.9 did not have a
translation cycle, the data for the new structure was not added.

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

### Specification

The changes to the specification are found at [CLDR 1.9
Modifications](http://www.unicode.org/reports/tr35/tr35-17.html#Modifications).

### Errata

*The Collation section of the [Key/Type Definitions
table](http://www.unicode.org/reports/tr35/index.html#Key_Type_Definitions) in
[UTS #35: Locale Data Markup Language
(LDML)](http://www.unicode.org/reports/tr35/) has the following errors:*

1.  *In root, collation type "standard" is based on a modified version of
    \[[UCA](http://www.unicode.org/reports/tr41/#UTS10)\] order, not on the
    default UCA order. The standard collations for other languages are based on
    the modified UCA order in root.*
2.  *However, there is an additional collation type "ducet" (not listed in UTS
    #35) which does provide the unmodified default UCA order; this "ducet"
    collation is provided in root and available in all locales.*
3.  *Though UTS #35 states that the special "search" collation type is only
    available in some locales, it (like "standard" and "ducet") is actually
    available in all locales.*

---

Major contributors to CLDR include Apple, Google, and IBM, plus official
representatives from a number of countries such as Finland (Kotoistus), India
(Department of Information Technology), and France (Office de la Langue
Bretonne). Many other organizations and volunteers around the globe, including
Adobe, Gnome, LISA, OpenOffice, Utilika, and Yahoo! have also made important
contributions to CLDR. For this version, special thanks to Åke Persson for his
contributions to collation, and to Sascha Brawer, Martin Jansche, Hiroshi
Takenaka, and Yui Terashima for their contributions to transliterations. For
more details, see [Acknowledgments](../acknowledgments.md).

Unicode CLDR is by far the largest and most extensive standard repository of
locale data. This data is used by a wide spectrum of companies for their
software internationalization and localization: adapting software to the
conventions of different languages for such common software tasks as formatting
of dates, times, time zones, numbers, and currency values; sorting text;
choosing languages or countries by name; transliterating different alphabets;
and many others. Unicode CLDR 1.9 is part of the Unicode locale data project,
together with the *Unicode Locale Data Markup Language* (LDML:
<http://unicode.org/reports/tr35/>). LDML is an XML format used for general
interchange of locale data, such as in Microsoft's .NET.

For web pages with different views of CLDR data, see
<http://unicode.org/cldr/charts.html>. For more information about the Unicode
CLDR project (including charts) see <http://cldr.unicode.org>.
