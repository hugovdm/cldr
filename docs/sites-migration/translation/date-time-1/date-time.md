# Date/Time Symbols

## Symbols

Dates and times are formatted using patterns, like "mm-dd". Each field, like the
month or the hour, is represented by a sequence of letters from A to Z. For
example, one or more M's stand for the month. When the software formats a date
for your language, a value will be substituted for each field, according to the
following table.

*Important: the characters a-z and A-Z are special placeholders; they stand for
date or time fields, NOT real characters. For example, 'y' stands for a numeric
year and will be replaced by a value like '1998'. You must NOT "translate" the
placeholders; for example, don't change 'y' to 'j' even though in your language
the word for "year" starts with a "j".*

Any "real" characters need to be quoted, as in the following where a real
character 'g' needs to be in the pattern.

EEE, yyyy. **'g'**. dd. MMM

Symbol **English Examples** Meaning G AD, BC era
This also covers non-Gregorian calendars, such as Japanese. y, yy 1987 year; use
y to show as many digits as necessary (987, 2017) or yy to always show two
digits (87, 17, 09). M, L September, Sept, S; 11 month
*See below under Stand-Alone vs Format Styles for the difference between M and
L.* E, c Tuesday, Tues, T day of the week (eg Tuesday).
*Note that even if the locale never normally uses 12-hour time, values for the am and pm symbols, as well as flexible time patterns for 12-hour time, must be supplied to support overrides and testing. See [Date/Time Patterns](date-time-patterns/index.md).**See below under Stand-Alone vs Format Styles for the difference between E and c.* d 13 day h, H, K, k 12 hour. h for 12-hour cycle using 1 through 12, H for 24-hour cycle using 0 through 23, K for 12-hour cycle using 0 through 11, k for 24-hour cycle using 1 through 24 m 49 minute s 49 second a, b, B am, a, pm, p, noon, n a indicates am/pm, b indicates am/noon/pm/midnight, B indicates use of day period ranges such as “in the morning” or “in the evening”. Only used with "h" or "K".
*If the examples for day period ranges show them in the wrong position, then the
time formats specific to using day period ranges may be updated. See [Day period
patterns](date-time-patterns/index.md).* z / v Pacific Time, Paris Time time
zone. Don't change v to z or vice versa; just leave the choice the same as in
English.
' Since letters have special meaning, if you want a real letter, you need to put
it in single quotes, such as 'ta'.
For a real single quote, use '' (that is, two adjacent ' characters). Q Q1,
Q3quarter. These are calendar quarters (eg, Jan-Mar) not fiscal quarters (for
languages that distinguish them.

### Symbol Length

The number of letters indicates the format: for example, M or MM for numeric
(eg, 1 or 01), MMM for abbreviated. The following are the available symbol
lengths, and their meaning.

**Symbol** **Examples** **Meaning** M 3, 11 Numeric form, at least 1 digit MM
03, 11 Number form, at least 2 digits (padding with 0) MMM Dec Abbreviated form
MMMM December Full form MMMMM D Narrow form - only used in where context makes
it clear, such as headers in a calendar.
*Should be one character wherever possible.*

For the year, normally the form that should be used is 'y', which will expand
from 1 to 4 digits (the shorter forms occur in some calendars). The form yy' is
special, and is used for exactly two digits: thus "2005" turns into "05".

The longer forms are only relevant for the fields that can have a textual
representation: eras, months, day of the week, and am/pm. For more about the
names of these fields, see [Date/Time Names](date-time-names/index.md).

### Stand-Alone vs. Format Styles

Some languages use two different forms of strings (*stand-alone* and *format*)
depending on the context. Typically the *stand-alone* version is the nominative
form of the word, and the *format* version is in the genitive. Two different
characters are used:

**FieldFormatStand Alone**MonthMLDay of the WeekEc

Make sure that the correct forms are provided, especially for the months, and
used in the patterns. That is, suppose that the language uses "Dezembro" for
December when standing alone (LLLL), but "Dezembru" when with a date (MMMM, when
it means the nth day *of* that month). Then the formats for months could be
something like:

**Format String** **Example1** **Example2** LLLL Dezembro Dez. d MMMM 1 Dezembru
1 Dez. MMMM d yy Dezembru 1 1953 1 Dez. 53

Similarly, suppose that your language formats months differently if they have
vowels, eg "14 de gener de 2008" but "14 d'abril de 2008". In that case, the
stand-alone and format versions of the months should be:

**Format Month** Stand-Alone Month de gener gener d'abril abril

These must be coordinated with the format strings, which can't have the extra
"de" before the month:

**Format String** Date **Result** LLLL 2008-1-14 gener 2008-4-14 abril d MMMM
'de' y 2008-1-14 14 de gener de 2008 2008-4-14 14 d’abril de 2008

That is, if your language uses two different forms, then make sure that there
are two forms of the months or days where necessary, *and* adjust the date
patterns to use the LLL or LLLL stand-alone form or MMM and MMMM format forms,
as needed. See notes on [date formats](date-time-patterns/index.md).

If stand-alone forms are not needed for any grammatical reasons such as the
above, and if your language would always capitalize a date symbol such as month
name or weekday name when it appears by itself on a calendar page or as a menu
item (but not when it appears in the middle of a sentence), then stand-alone
forms may be used for capitalized versions of date symbols. However, there are
other solutions for capitalizing date symbols which provide finer control over
capitalization, see [capitalization
guidelines](../translation-guide-general/capitalization.md).

More details on date/time symbols and patterns may be found in the [Date Field
Symbol
Table](http://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table).
