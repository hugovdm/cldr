# CLDR Charts

The Unicode CLDR Charts provide different ways to view the Common Locale Data
Repository data.

**Version** **Link** Description latest <http://unicode.org/cldr/charts/latest>
The latest release version dev <http://unicode.org/cldr/charts/dev> A snapshot
of data under development previous [CLDR
Releases/Downloads](../downloads/index.md)
Previous available charts (back to CLDR v22.1)

The format of most of the fields in the charts will be clear from the Name and
ID, such as the months of the year. The format for others, such as the date or
time formats, is structured and requires more interpretation. For more
information, see [UTS #35: Locale Data Markup Language
(LDML)](http://www.unicode.org/reports/tr35/).

Most charts have "double links" somewhere in each row. These are links that put
the address of that row into the address bar of the browser for copying.

*Note that not all CLDR data is included in the charts.*

## **Summary**

Provides a summary view of the main locale data. Language locales (those with no
territory or variant) are presented with fully resolved data; the inherited or
aliased data can be hidden if desired. Other locales do not show inherited or
aliased data, just the differences from the respective language locale. The
English value is provided for comparison (shown as "=" if it is equal to the
localized value, and *n/a* if not available).

The Sublocales column shows variations across locales. Hovering over each
Sublocale value shows a pop-up with the locales that have that value.

## **By-Type**

Provides a side-by-side comparison of data from different locales for each
field. For example, one can see all the locales that are left-to-right, or all
the different translations of the Arabic script across languages. Data that is
unconfirmed or provisional is marked by a red-italic locale ID, such as
*·bn_BD·*.

## **Transform**

Shows some of the transforms in CLDR: the transliterations between different
scripts. For more on transliterations, see [Transliteration
Guidelines](http://www.unicode.org/cldr/transliteration_guidelines.html).

## **Survey Tool**

Provides a view of the CLDR data designed for collecting and vetting data during
certain periods. Most proposed data (new or corrections) is entered via this
tool.

## **Keyboards**

Provide a view of keyboard data: layouts for different locales, mappings from
characters to keyboards, and from keyboards to characters.

## **BCP47 Extension**

Shows the Unicode BCP47 extension data in IANA registry-style files:

*   **bcp47-t.txt**
*   **bcp47-u.txt**

## **Supplemental Data**

Shows other data that is not part of the locale hierarchy but is still part of
CLDR. Includes:

### Locale Coverage

### Language Plural Rules

### Likely Subtags

### Territory-Language Information

### Language-Territory Information

### Detailed Territory-Currency Information

### Languages and Scripts

### Scripts and Languages

### Scripts, Languages, and Territories

### Territory Containment (UN M.49)

### Zone → Tzid

### Aliases

For more details on the locale data collection process, please see the [CLDR
process](http://www.unicode.org/cldr/process.html). For filing or viewing bug
reports, see [CLDR Bug
Reports](http://www.unicode.org/cldr/filing_bug_reports.html).
