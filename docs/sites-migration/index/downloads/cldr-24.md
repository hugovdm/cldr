# CLDR 24 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs **24**
**2013-09-18** **[v24](cldr-24.md)** [**CLDR24**
](http://unicode.org/Public/cldr/24/)
**[Charts24](http://www.unicode.org/repos/cldr-aux/charts/24/index.html)**
**[LDML24](http://www.unicode.org/reports/tr35/tr35-33/tr35.html)**
[**Δ24**](http://unicode.org/cldr/trac/query?status=closed&resolution=fixed&resolution=duplicate&resolution=as-designed&resolution=moot&resolution=fix-in-surveytool&milestone=24dsub&milestone=24dsub2&milestone=24dvet&milestone=24rc&milestone=24final&max=900)
` [ release-24](http://unicode.org/cldr/trac/browser/tags/release-24)` `
[ΔDTD24](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-24/common/dtd&old=HEAD@tags/release-23-1/common/dtd)`

[TOC]

Unicode CLDR 24 focused on additional structure for formatting units, dates, and
times, and improving data coverage. This version contains data for **238**
languages and **259** territories—**740** locales in all. Ten languages were
added to the 100%-modern-coverage list, for a total of 70 languages. Between the
new languages, and the new structure, more data was entered than any previous
release.

The new structure focused primarily on formatting of units and improvements to
date and time formatting.

*   **fractional plural forms.** major extension to handle fractions (eg, some
    languages use the equivalent of “1.**2** teaspoon**s**” but “2.**1**
    teaspoon”)
*   **measurement units.** many additional unit types (“10.3 kg”), in up to 6
    plural forms per language
*   **compound units.** video length: "23 hrs, 7 mins", or "23:07"
*   **dates/times.** new relative fields such as "last Sunday", and "now"; 12
    hour time formats that omit "am/pm"; neutral eras ("405 BCE"); additional
    timezone falback regional patterns ("*{city}* Daylight Time")
*   **number formatting.** exponential notation (1.42×1023), at-least ("99+"),
    ranges ("3.5-4.5 kg"), narrow currency symbols (both "US$12.23" and
    "$12.23").
*   **collation.** major simplification of rule syntax, updated root files to
    Unicode 6.3; preliminary version of European Ordering Rules; documentation
    of the CLDR Collation Algorithm (extending UCA)
*   **JSON**. improved support, including new structure and data.

In addition, the data already present in CLDR v23 was reviewed for the supported
languages, and many improvements made.

Details of coverage improvements and new features are provided below, along with
a detailed Migration section.

> The table above lists the files for this release. For a description of their
> purpose and format, and for the coverage graphic, see the [Key](#TOC-Key).

## Coverage improvements

The following shows the additional coverage in this release. The horizontal axis
shows the number of languages. The shaded areas show additional data in each
release. The axis shows the percentage of modern coverage.

<iframe src="javascript:void(0);" width="600" height="500" allow="fullscreen"
/>document.getElementById('form564716603').submit();

The definition of “modern coverage” increases over time, as new structure and
requirements are added. This chart is using the most recent definition, but
applying it to previous versions. In late 2009 we introduced the coverage
levels, and thus the data starts to hit certain plateaus, one at 100% and one at
around 30%. Some languages don't quite hit 100% because of the way coverage is
measured.

For consistency, the current release numbering scheme is used for all versions.

## Known Errors

***The plural rules for version 24 remove the category "few" for Russian. This
was an error: implementations should not remove that category. The category will
be restored in version 25.***

## New/modified structure and data

The main features include the following (see the Delta link above for a full
list of changes other than data additions or corrections made via the Survey
Tool).

### Plural rule changes

The plural rules were significantly extended in order to provide the capability
to handle fractions correctly. Previously rules could only be written in terms
of conditions on a single value 'n', representing the (absolute value of the)
complete decimal value (both integer and fraction part). However, plural rules
in many languages take into account not only the value, but also how it is
presented (whether and how many fraction digits are shown, and what those digits
are). For example, U.S. English makes a distinction between “1 dollar” and “1.00
dollars” though both examples are for the same numeric value (represented by 'n'
in the rules). To extend the rules, several new values can be used in the rules:

Symbol Value i integer digits of n. v number of visible fraction digits in n,
*with* trailing zeros. w number of visible fraction digits in n, *without*
trailing zeros. f visible fractional digits in n, *with* trailing zeros. t
visible fractional digits in n, *without* trailing zeros.

The plural rules were also extended to specify sample data values for the rule
as part of the rule itself.

#### Plural rules data

With the new rules available, a detailed review of all the language plural rules
was done, resulting in the following changes.

1.  **New plural categories were added:**
    1.  *****1 ➞ *one****:** Azerbaijani, Georgian, Hungarian, Turkish
    2.  **0, 1 ➞ *one:*** Kannada, Persian
    3.  ***0, …* ➞ *few:*** Manx
    4.  ***fractions **➞** many*:** Czech, Slovak, and Lithuanian
2.  **Some plural categories were merged:**
    1.  ***few* (2-4,…)** ➞ ***other* (all fractions):** Russian
    2.  ***many* (0, 5-21,…) ➞ *other* (all fractions):** Bosnian, Croatian,
        Serbian
3.  **Some other categories changed for some integers:**
    1.  **0 ➞ *one:*** Armenian, Bengali, Gujarati, Marathi, Punjabi, Zulu
    2.  **10 ➞ *other:*** Hebrew
    3.  **11 ➞ *one:*** Macedonian
    4.  **10, … ➞ *zero:*** Latvian
    5.  **21, … ➞ one:** Icelandic

See [CLDR24 Plural
Rules](http://www.unicode.org/cldr/charts/24/supplemental/language_plural_rules.html).

### Enhanced <units> structure

The <units> structure has been enhanced in several ways (and new data collected
for these items):

*   It now supports many additional unit types besides time durations, including
    units for acceleration, angle, area, length, mass, power, pressure, speed,
    temperature, and volume (with plural forms for each). The unit type is now
    compound, with the first part indicating the type of unit, such as <unit
    type="**length**-yard">.
*   The individual <unit> elements are available in multiple widths under a new
    <unitLength> element: long, short, and narrow (previously some units had
    alt="short" forms)
*   A <compoundUnit> element specifies ways of combining multiple units, such as
    “kilometers per second” or “km/s”.
*   A new <durationUnit> element specifies patterns for time durations involving
    combinations of hours, minutes, and seconds, such as "Video length: 93:45".

In addition, under <listPatterns>, three new types of <listPattern> may be
provided: "unit" (for use with long units), "unit-short", and "unit-narrow".
These are intended to be used for constructing formats such as “2 hours, 5
minutes”, “2 hrs, 5 mins”, or “2h 5m”. If separate <listPattern> data for these
are not provided, the standard <listPattern> will be used.
\[[#5997](http://unicode.org/cldr/trac/ticket/5997)\].

The relative time units formerly under <units> with types ending in "-future" or
"-past" (e.g. "day-future" and "day-past") have been moved to new <relativeTime>
elements under <fields>, see next section.

Notes:

*   This first pass only covers a basic selection of units used on the web. We
    anticipate adding more in future releases.
*   English units (foot, Fahrenheit) are not often used outside of English,
    except in for special purposes: eg, "Die besten Flachbildfernseher ab 46
    Zoll (117 cm)" \["Zoll" = inch\].
*   The narrow forms are intended to be as narrow as possible, however, there
    may be no good narrow term for some units in some languages. As always,
    narrow forms are not necessary unique; they should only be used where the
    context is sufficiently clear (eg, it is a length).

### Enhanced <fields> structure

The <fields> structure has been enhanced in several ways (and new data collected
for these items):

*   The relative time units formerly under <units> with types ending in
    "-future" or "-past" have been moved to new <relativeTime> elements under
    <fields>. See the Migration section for details.

*   New fields types have been added for weekdays (sun, mon, tue, wed, the, fri,
    sat) to enable specifying relative times for these, for example:
    > <field type="mon"> <relative type="-1">last Monday</relative> <relative
    > type="0">this Monday</relative> <relative type="1">next Monday</relative>
    > </field>

    Usage is defined as follows:
    *   "Last…" is the greatest before today.
    *   "This" is the least after today, but in the same week;
    *   "Next…" is the least after today but in the next week.
    With these, relative days can now be formatted as (for example): Today,
    Yesterday, Last Sunday, April 15

*   Added data to provide relative times for more field types (in addition to
    day), such as week, month, year:
    > <field type="week"> <relative type="-1">last week</relative> <relative
    > type="0">this week</relative> <relative type="1">next week</relative>
    > </field>

*   The term for "now" has been added (with the path <field
    type="second">/<relative type="0">now</relative>
*   The English data for all field items was changed to use middle-of-sentence
    capitalization.

Note: Relative periods, are ∅∅∅ (unused) if not normally used in the language.
Languages may have the same values for "this" and "next".

### Number format additions & data changes

Under <numbers>, a new <miscPatterns> element provides various additional number
patterns; in CLDR 24, these are:

*   type="atLeast": A short way of indicating greater than or equal to a value,
    such as “⩾{0}” or “{0}+”, such as 99+
    \[[#5272](http://unicode.org/cldr/trac/ticket/5272)\].
*   type="range": Pattern for a numeric range, such as “{0}–{1}”, such as
    3.5–4.6 \[[#5958](http://unicode.org/cldr/trac/ticket/5958)\].

Under <numbers>/<symbols>, a new <superscriptingExponent> element supports more
natural scientific notation, providing a character for use between the
significand and the exponent—for example, the character ‘×’ to produce e.g.
“1.42×1023” \[[#5815](http://unicode.org/cldr/trac/ticket/5815)\].

The <currencyFormat> element now supports both type="standard" and
type="accounting"; the latter is intended for formats specific to accounting,
such as the use of parentheses to indicate a negative or debit value:
“(175.50)”. Moved existing standard patterns that used accounting style to the
"accounting" variant \[[#5674](http://unicode.org/cldr/trac/ticket/5674)\].

Under <currencies>/<currency>, the <symbol> element now supports an additional
alt="narrow" form when the currency type can be understood from context, such a
“$” instead of “US$”.

Under supplemental <currencyData>/<fractions>, the <info> element can now have
two additional attributes for formatting amounts in case transactions (as
opposed to more formal contexts such as bank statements)
\[[#5548](http://unicode.org/cldr/trac/ticket/5548)\]:

*   cashDigits: the number of decimal digits to be used when formatting
    quantities used in cash transactions
*   cashRounding: the rounding increment to be used when formatting quantities
    used in cash transactions

To improve layout and editing of signed numbers in bidi locales: (a) changed
number and currency patterns in bidi locales to have sign logically preceding
the amount; (b) added bidi marks to plus & minus signs for "arab" and "arabext"
number systems—and "latn" in bidi locales. Note that these symbols may now use
more than one character \[[#6078](http://unicode.org/cldr/trac/ticket/6078)\].

### Date format additions & data changes

The <regionFormat> element used for fallback zone formatting can now have
additional type="standard" and type="daylight" forms, for example:

*   <regionFormat>: "{0} Time", such as "Los Angeles Time"
*   <regionFormat type="daylight">: "{0} Daylight Time", such as "Los Angeles
    Daylight Time"
*   <regionFormat type="standard">: "{0} Standard Time", such as "Los Angeles
    Standard Time"

There is a new pattern character 'J' for use in flexible date format skeletons;
it behaves like 'j', but also eliminates any day period marker that would be
appended. For example, with the “en_US” locale, a time of 13:00 would be
formatted with a skeleton of “jmm” as “1:00 PM”, and with a skeleton of “Jmm” as
just “1:00” \[[#5413](http://unicode.org/cldr/trac/ticket/5413)\].

Short metazone names were cleaned up and rationalized for certain regions
\[[#5175](http://unicode.org/cldr/trac/ticket/5175)\].

For the Gregorian calendar, an alt="variant" form for eras was added which can
provide a more neutral or non-religious name
\[[#649](http://unicode.org/cldr/trac/ticket/649)\], for example:

> <eras> <eraAbbr> <era type="0">BC</era> <era type="0" alt="variant">BCE</era>
> <era type="1">AD</era> <era type="1" alt="variant">CE</era> </eraAbbr> </eras>

The default month names in the root locale changed from “Month1”..“Month12” to
“M01”..“M12” to be more neutral.
\[[#5932](http://unicode.org/cldr/trac/ticket/5932)\].

<availableFormats> items for the following additional skeletons were added in
many locales: "Ehm", "EHm", "Ehms", "EHms".

### Core & linguistic element additions

For the <ellipsis> element, added new types "word-initial", "word-medial", and
"word-final" for cases where the breaks are on a word boundary, where some
languages include a space.
\[[#4694](http://unicode.org/cldr/trac/ticket/4694)\].

Exemplar set data has been improved for many locales. In particular; punctuation
exemplar sets have been added for many locales that did not have them.

### Collation

Deprecated the XML collation syntax (the <rules> element and its subelements) in
favor of ICU-style basic syntax, except that the <import> element is now moved
up from under <rules> to be just under <collation>; changed all CLDR collations
to use the new syntax \[[#5551](http://unicode.org/cldr/trac/ticket/5551)\].

Deprecated the <default> element for collation in favor of new
<defaultCollation> element
\[[#5679](http://unicode.org/cldr/trac/ticket/5679)\]; deprecated the unneeded
<base> element under <collation>
\[[#6332](http://unicode.org/cldr/trac/ticket/6332)\].

Updated collation root files to Unicode 6.3, added a SHORT version, and made
other improvements \[[#5568](http://unicode.org/cldr/trac/ticket/5568),
others\]. Note that because the UCA now doesn't distinguish decimal digits with
the same value, a by-product is sometimes strange-looking generated rules, such
as:

> OLD&2 <<< ㉓ / 3**NEW**&2 <<< ㉓ / &#x1d362;

The character "㉓" is expanding to a tertiary difference from "23". There is now
no functional difference between these, because for the UCA, "3" = "&#x1d362;".

Added preliminary version of European Ordering Rules
\[[#4142](http://unicode.org/cldr/trac/ticket/4142)\].
Improved [tailoring
semantics](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-collation.html#Collation_Tailorings),
especially for expansions/extensions, and case weights.
\[[#5909](http://unicode.org/cldr/trac/ticket/5909)\],
\[[#5915](http://unicode.org/cldr/trac/ticket/5915)\]

Changes for specific collations:

*   For Vietnamese, add traditional collation.
    \[[#5843](http://unicode.org/cldr/trac/ticket/5843)\]
*   For Japanese collations, Latn script now sorts before Kana and Hani (per JIS
    4061). \[[#6086](http://unicode.org/cldr/trac/ticket/6086)\]
*   Also for Japanese collation, fix the collation of fullwidth backslash.
    \[[#6256](http://unicode.org/cldr/trac/ticket/6256)\]
*   For Chinese Zhuyin collation, tone marks now have only secondary difference.
    \[[#6511](http://unicode.org/cldr/trac/ticket/6511)\]
*   Remove the Catalan standard tailoring, equivalent to root collation order.
    \[[#6258](http://unicode.org/cldr/trac/ticket/6258)\]
*   Fixed Finnish collation to correctly handle U+0335 COMBINING SHORT STROKE
    OVERLAY. \[[#6276](http://unicode.org/cldr/trac/ticket/6276)\]

### Data organization

Added en_001 for better inheritance model for English locales. This inherits
from en but removes or generalizes US-specific content (removes US timezone,
uses US$ instead of $ as symbol for USD, etc.). Most non-US-related English
locales inherit directly or indirectly from this
([#6039](http://unicode.org/cldr/trac/ticket/6039)).

Changed the default script for Uzbek (uz) to be Latn instead of Cyrl.
\[[#6360](http://unicode.org/cldr/trac/ticket/6360)\]

### Language & region display names and other support

Changes names to be shorter or added short variants, to help with UI overflow:

*   Added alt="short" names for more languages, e.g. en_GB ("U.K. English"),
    en_US ("U.S. English").
*   Added alt="short" names for more territories, e.g. GB ("U.K."), PS
    ("Palestine"), US ("U.S.").
*   Used shorter standard names in en and some other locales for some regions,
    e.g. VC “Saint Vincent and the Grenadines”→“St. Vincent & Grenadines”
    \[[#4752](http://unicode.org/cldr/trac/ticket/4752)\].

Also added data for territory XK ("Kosovo"): display name and supplemental data.

Several territory names in English and other languages formerly contained square
brackets “\[\]” to indicate an alternate name, e.g. “Cocos \[Keeling\] Islands”.
The square brackets were used to minimize confusion when such names were
combined with language names using the <localePattern>, e.g. “English (Cocos
\[Keeling\] Islands)”. However, when the territory name is used by itself,
parentheses are preferred to square brackets. Therefore the square brackets in
territory names have been changed to parentheses; software that substitutes such
a name in the {1} section of a <localePattern> should change the parentheses to
square brackets.

### BCP47 extension enhancements

Defined the relation between keywords that share the prefixes, and defined 3 new
islamic calendar variants \[[#5726](http://unicode.org/cldr/trac/ticket/5726)\]:

*   "islamic-umalqura", Islamic calendar, Umm al-Qura
*   "islamic-tbla", Islamic calendar, tabular (intercalary years
    \[2,5,7,10,13,16,18,21,24,26,29\] - astronomical epoch)
*   "islamic-rgsa", Islamic calendar, Saudi Arabia sighting-based

Added the preferred attribute for <ldmlBCP47> <type> elements to specify the
canonical replacement for deprecated type names
\[[#5726](http://unicode.org/cldr/trac/ticket/5726)\].

### Segmentation

Added a new <exceptions> element under <segmentation>; this can provide a list
of strings that are exceptions to the standard rules—terms within which a break
of the specified type should not occur, though the rules would find a break.
Added a technology preview of segmentation exceptions data from the [ULI
project](http://uli.unicode.org/) for a small number of locales: de, en, es, fr,
it, pt, ru \[[#6336](http://unicode.org/cldr/trac/ticket/6336)\].

Prevent line break after '/' (SY) before Hebrew letter (HL); this is currently a
CLDR tailoring of root line break.
\[[#6116](http://unicode.org/cldr/trac/ticket/6116)\]

## LDML Specification changes

Specification changes are listed in the
[Modifications](http://www.unicode.org/reports/tr35/tr35-33/tr35.html#Modifications)
section. In addition to documenting new LDML structure, this version adds
documentation of the CLDR Collation Algorithm (which extends the Unicode
Collation Algorithm), and improves the specification of various settings and
rules. \[#5962\], \[#5850\]

## Survey Tool improvements

The [Survey Tool](../survey-tool/index.md) is used to gather the data and
achieve consensus on the best choice for each language. It has had major
improvements for v24 in UI and performance, and was used to collect more data
than in previous releases
([Statistics](http://st.unicode.org/cldr-apps/statistics.jsp)). To view the
locales, see [Browsing](http://st.unicode.org/cldr-apps/survey).

## JSON Support

The JSON conversion utility, located at org.unicode.cldr.json.Ldml2JsonConverter
in the tools.zip, had major work done in the 23.1 maintenance release, and has
been further enhanced to correctly process the new structural changes introduced
in CLDR 24. This tool allows consumers of CLDR data to convert data from the
LDML format to a more directly consumable JSON format (for use in JavaScript
environments) in a standardized way, according to the[ CLDR Specification for
JSON Bindings](../cldr-spec/json.md). It allows users to create a customized
configuration to filter and organize the resulting JSON data, converting just
those pieces of data that are needed. The utility also allows users to create
JSON for a selected list of locales, and also to filter data by draft status or
coverage level.

A sample of the JSON produced by this tool is available by clicking the link in
the "Data" column on the download page and downloading "json.zip". The JSON
sample contains data only for a subset of the published CLDR locales, and is
intended for reference purposes only, because different implementations will
filter in different ways.

For more details on the JSON conversion utility, refer to the README file
located in the downloadable JSON sample.

## Migration Issues

While the LDML XML structure itself remains backwards compatible, in some cases
CLDR data is moved to different structure, or the interpretation or contents of
fields may change.

### **Units**

The <units> structure has changed. In CLDR 23 it looked like
> <units> <unit type="day"> <unitPattern count="one">{0} day</unitPattern>
> <unitPattern count="one" alt="short">{0} day</unitPattern> <unitPattern
> count="other">{0} days</unitPattern> <unitPattern count="other"
> alt="short">{0} days</unitPattern> </unit> <unit type="day-future">
> <unitPattern count="one">In {0} day</unitPattern> <unitPattern
> count="other">In {0} days</unitPattern> </unit> <unit type="day-past">
> <unitPattern count="one">{0} day ago</unitPattern> <unitPattern
> count="other">{0} days ago</unitPattern> </unit> ... </units>

Beginning in CLDR 24 there are several changes:

*   The "-future" and "-past" forms have moved to a new <relativeTime> element
    under <fields>.
*   The old unit types, which were all for time units such as "day" and "hour",
    now have a prefix "duration-".
*   There is an additional <unitLength> element in the structure; the old
    standard forms are now under <unitLength type="long">, and the the old
    alt="short" forms are now under <unitLength type="short">.

The <units> structure now looks like this:
> <units> <unitLength type="long"> <unit type="duration-day"> <unitPattern
> count="one">{0} day</unitPattern> <unitPattern count="other">{0}
> days</unitPattern> </unit> ... </unitLength> <unitLength type="short"> <unit
> type="duration-day"> <unitPattern count="one">{0} day</unitPattern>
> <unitPattern count="other">{0} days</unitPattern> </unit> ... </unitLength>
> </units>

The <fields> structure now has added items as follows:
> <fields> <field type="day"> ... <relativeTime type="future">
> <relativeTimePattern count="one">in {0} day</relativeTimePattern>
> <relativeTimePattern count="other">in {0} days</relativeTimePattern>
> </relativeTime> <relativeTime type="past"> <relativeTimePattern
> count="one">{0} day ago</relativeTimePattern> <relativeTimePattern
> count="other">{0} days ago</relativeTimePattern> </relativeTime> </field> ...
> </fields>

### **Collation**

*   The XML syntax for collation rules is deprecated in favor of the ICU-style
    “basic” syntax rules, all contained within a new <cr> element. The <import>
    element is moved up from under the now-deprecated <rules> element to just
    under the <collation> element
    ([#5551](http://unicode.org/cldr/trac/ticket/5551)).
*   The <default> element for collation is deprecated and replaced with the new
    <defaultCollation> element
    ([#5679](http://unicode.org/cldr/trac/ticket/5679)).

### Formatting

*   The plural rules have changed for a number of languages, with additional
    syntax, and also resulting in the addition or removal of plural categories,
    or the movement of certain numeric values from one category to another. For
    details of the changes, see [Plural rule changes](#TOC-Plural-rules) above.
    For help with migrating messages, see [Plural
    Rules](../cldr-spec/plural-rules.md), under Migration.
    *   The chief issues for migration are the new plural categories, what is
        **Split Other** on [Plural Rules](../cldr-spec/plural-rules.md).
    *   Types 1.1, 1.2 (Azerbaijani, Georgian, Hungarian, Turkish, Kannada,
        Persian) will not normally require message changes. these languages
        typically don't show changes in nouns or adjectives, just in references,
        so any real instances where messages need to be changed are likely to be
        very few in number.
    *   Type 3 (Manx) is an unusual language, unlikely to be translated in many
        implementations.
    *   Type 4 (Czech/Slovak/Lithuanian) should be reviewed, since they may have
        used a generic format that needs correction. *In addition, if **many**
        was an unused form, then it may have bad stand-in text.*
*   The <localeSeparator> element has changed in CLDR 24 from a string (e.g. “,
    ”) to a pattern (e.g. “{0}, {1}”). In most cases the change is just adding
    “{0}” at the beginning and “{1}” at the end of the previous string
    ([#4915](http://unicode.org/cldr/trac/ticket/4915)).
*   In CLDR 23, many of the currency formats used a negative format that was
    specific to accounting usage. In CLDR 24 these negative formats have been
    moved to a new <currencyFormat type="accounting">, so that the standard
    currencyFormat uses a negative format more typical of most common usage
    ([#5674](http://unicode.org/cldr/trac/ticket/5674)).
*   The element <fallbackRegionFormat> has been deprecated and removed.
*   Several territory names in English and other languages formerly contained
    square brackets “\[\]” to indicate an alternate name, e.g. “Cocos
    \[Keeling\] Islands”.
    *   The square brackets were used to minimize confusion when such names were
        combined with language names using the <localePattern>, e.g. “English
        (Cocos \[Keeling\] Islands)”. However, when the territory name is used
        by itself, parentheses are preferred to square brackets. Therefore the
        square brackets in territory names have been changed to parentheses.
    *   *Implementations that substitute such a name in the {1} section of a
        <localePattern> should change the parentheses to square brackets.*

### “Golden File” Test Changes

Several changes were introduced in root and English data (which will also
percolate into other locales via inheritance or translation), and may cause
“Golden File” tests to fail. These are tests that capture a snapshot of the
results from a previous version, such as a formatted date, and compare for
regression.

*   The negative forms such as "(1)" for -1 will change to use the <minusSign>.
*   The <plusSign> and <minusSign> will have an LRM or RLM in them for
    arab/arabext numbering systems. In bidi locales only, this includes the latn
    numbering system, and negative formats with trailing '-' were changed to use
    leading '-'.
*   Fractions formatted with previous plural rules, and integers in some
    locales, will now have different (better) results.
*   The default month names in the root locale changed from “Month1”..“Month12”
    to “M01”..“M12”, for a more neutral form
    ([#5932](http://unicode.org/cldr/trac/ticket/5932)).
*   To reduce UI overflow, some names have been shortened in English (and their
    translations in other languages): eg, Heard Island and McDonald Islands ➞
    Heard & McDonald Islands
*   The stand-alone names of regions that had \[...\] now have (...), such as
    "Cocos \[Keeling\] Islands".
*   In "en", time intervals use consistent spacing, so "HH–HH" ➞ "HH – HH"
*   Terms like <relative type="-1">Last year</relative> were changed to not use
    "sentence-casing", so <relative type="-1">last year</relative>.
    *   *Implementations are now expected to convert to sentence-case where
        necessary.*
*   Date ranges in old currency names more consistently use en-dash: eg, Afghan
    Afghani (1927–2002)

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
