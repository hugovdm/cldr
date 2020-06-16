# Number and currency patterns

## Pattern Characters

Numbers are formatted using patterns, like "#,###.00". For example, the pattern
"#,###.00" when used to format the number 12345.678 could result in "12'345,67".
That would happen if the grouping separator for your language is an apostrophe
('), and the decimal separator is a comma (,).
Also see [Number Symbols](number-symbols/index.md).

*Important: The characters . , 0 # (and others below) are special placeholders;
they stand for the decimal separator, and so on, and are NOT real characters.
You must NOT "translate" the placeholders; for example, don't change '.' to ','
even though in your language the decimal point is written with a comma.*

Here are the special characters used in number patterns.

Whenever any of these symbols are in the English pattern, they **must** be
retained in the pattern for your language. The positions of some of them (%, ¤)
may be changed, or spaces added or removed. The symbols will be replaced by the
local equivalents, using the [Number Symbols](number-symbols/index.md) for your
language. Verify results by reviewing the dynamic examples in the right-hand
pane.

Symbol Meaning . Replaced automatically by the character used for the decimal
point in your language. **Not a real period; must be retained!** , Replaced by
the "grouping" (thousands) separator in your language. **Not a real comma; must
be retained!** 0 Replaced by a digit (or zero if there aren't enough digits). #
Replaced by a digit (or nothing if there aren't enough). Often used to show the
position of the ",". ¤ This will be replaced by a currency symbol, such as $ or
USD. Note: by default a space is automatically added between letters in a
currency symbol and adjacent numbers. So you don't need to add a space between
them if your language writes "$12" but "USD 12". % This marks a percent format.
The % symbol may change position, but **must be retained.** E This marks a
scientific format. The E symbol may change position, but **must be retained.** '
If any of the above characters are used as literal characters, they must be
quoted with ASCII single quotes. For example, in the [**Short
Numbers**](number-patterns.md) if a period needs to be used to mark an
abbreviation, it would appear as:
**0.0 tis'.'** ***not***
**0.0 tis.** ...;... If your language uses different formats for negative
numbers than just adding "-" at the front, you can put in two patterns,
separated by a semicolon. The first will be used for zero and positive values,
while the second will be used for negative values.

*   For example: #,##0.00¤;(#,##0.00¤) is used to make negative currencies
    appear like "(1'234,56£)" instead of "-1'234,56£". That is used for
    formatting currency amounts in English, but not for general-purpose decimal
    numbers.

Translators should ***not*** change the pattern of zeros (0) or hash marks (#)
after a decimal point (for example, #,##**0.###**); those will be reset by
software. This is true also for currency formats. Even if your currency doesn't
use any decimal points, the currency format will have them in the pattern.
Again, the best way to verify the expected end result is to review the examples
in the right pan.

**When to update patterns**

*   The grouping separation is not by thousands. In this case, move the comma
    separator in the format to the correct placement.
    *   For example, if your language expects to see the separator in the first
        group of 3 and 2s there after: 1,00,00,000.00, the patter to use is:
        #**,##,**##0.###.
*   Negative patterns can be handled two ways:
    *   Do not specify a negative pattern. This will simply add a minus sign to
        the positive format.
        *   For example leave the pattern as #,##0.### if you simply expect the
            negative sign to be appended in at the beginning. (See examples in
            the information pane)
    *   Specify use for the negative format separated with "**;**".
        *   For example, if the negative is indicated by using the parenthesis
            as done commonly in accounting formats: **#,##0.###;(#,##0.###)**.
            The semicolon after the positive pattern indicates a separate format
            for the negative pattern.
    *   Specify the position of the negative sign
        *   For example is the position of the negative sign is before the %
            symbol, you'd specify: #,##0**%;**#,##0**-%**.
*   The currency symbol (¤) or percent sign (%) is used in a different position.

## General Purpose Numbers

There are four general-purpose number patterns. Remember that the "." and ","
*do not* mean the literal characters: programs that use CLDR will change them to
the right number symbols for your language.

You must **NOT** "localize" the placeholders. See Important note at the top of
this page.

Type **English Example** Meaning currency¤#,##0.00 Used for currency values. A
currency symbol (¤) is will be replaced by the appropriate currency symbol for
whatever currency is being formatted. The choice of whether to use the
international currency symbols (USD, EUR, JAY, RUB,…) or localized symbols ($,
€, ¥, руб.,…) is up to the application program that uses CLDR. Note: the number
of decimals will be set by programs that use CLDR to whatever is appropriate for
the currency, so do not change them; keep exactly 2 decimals.
currency-accounting ¤#,##0.00;(¤#,##0.00)Used for currency formats in accounting
contexts. decimal

#,##0.###

Used for formatting general decimal numbers. The number of decimals will be set
by programs that use CLDR, so don't alter them. Typically the only change is to
the position of the thousands separator (see above). percent

#,##0%

Used for percent values, such as 12%. The number of decimals will be set by
programs that use CLDR, so don't alter them. scientific

#E0

Used for scientific notation. Typically not translated.

## Short Numbers

There are also patterns for compact forms of numbers, such as the such as "1M"
and "1 million". The pattern may be substantially different across languages, as
can be seen by comparing the English patterns to the Japanese patterns in the
table below.

The patterns have plural categories, because in some languages the text will
inflect according to the number: that is, in those languages one writes "1
million" but "2 million**==s==**". The patterns do not allow for gender
inflection, so the most neutral form should be chosen.

Remember that these are number patterns, so certain characters like a period
(".") *must* be quoted if they are not the placeholder standing for the decimal
period. See [**Pattern Characters**](number-patterns.md).

Code Meaning English
Pattern English
Formatted
Example Japanese
Pattern Japanese
Formatted
Example 1000 **1 thousand = 1,000** 0.0K 1.2K 0千 1千 10000 **10,000** 00K 12K
0.0万 1,2万 100000 **100,000** 000K 123K 00万 12万 1000000 **1,000,000** 0.0M 1.2M
000万 123万 10000000 **10,000,000** 00M 12M 0000万 **1234万** 100000000
**100,000,000** 000M 123M 0.0億 **1.2億** 1000000000 **1,000,000,000** 0.0B 1.2B
00億 **12億** 10000000000 **10,000,000,000** 00B 12B 000億 ****123億****
100000000000 **100,000,000,000** 000B 123B 0000億 ****1234億**** 1000000000000
**1,000,000,000,000** 0.0T 1.2T 0.0兆 1.2兆 10000000000000 **10,000,000,000,000**
00T 12T 00兆 12兆 100000000000000 **100,000,000,000,000** 000T 123T 000兆 123兆

If it is impossible to abbreviate numbers in that way in your language, then use
a single 0 (zero digit) in your result. For example, the Japanese pattern for
1000 uses that. This should be avoided wherever possible, however, in that it
may cause bad displays in devices with small screens, such as mobile phones.

The number of decimals can be changed by programs that use CLDR according to the
task. For example, the pattern for 10,000 above (00K for English, 0.0万 for
Japanese) may be modified to have more or fewer decimals — it could be changed
to have 3 digits of accuracy: 00.0K for English, 0.00万 for Japanese.

## Plural Forms of Numbers

Some languages have multiple plural forms for numbers, and will have multiple
plural categories for each number. In such cases, look at the [Plural Rules and
Tool](http://cldr.org/translation/plurals#TOC-Rules-and-Tool) to see what
numbers are mapped to the various plural categories.
