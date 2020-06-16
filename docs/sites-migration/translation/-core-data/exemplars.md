# Exemplar Characters

## [TOC]

The exemplar character sets contain the commonly used letters for a given modern
form of a language. These are used for testing and for determining the
appropriate repertoire of letters for various tasks, like choosing charset
converters that can handle a given language. The term “letter” is interpreted
broadly, and includes characters used to form words, such as 是 or 가. It should
not include presentation forms, like
`[U+FE90](http://unicode.org/cldr/utility/character.jsp?a=FE90)` ( ‎ﺐ‎ ) ARABIC
LETTER BEH FINAL FORM, or isolated Jamo characters (for Hangul).

There are different categories:

CategoryEnglish ExampleMeaning*standard*a b c d e f g h i j k l m n o p q r s t
u v w x y z**The minimal characters** required for your language (other than
punctuation).
The test to see whether or not a letter belongs in the main set is based on
whether it is acceptable in your language to always use spellings that avoid
that character. For example, English characters do not contain the accented
letters that are sometimes seen in words like *résumé* or *naïve*, because it is
acceptable in common practice to spell those words without the accents.
If your language has both upper and lowercase letters, only include the
lowercase (and İ for Turkish and similar languages). *punctuation* ‐ – — , ; : !
? . … ‘ ' ’ ′ ″ “ " ” ( ) \[ \] / @ & # § † ‡ \* **The punctuation characters**
customarily used with your language.
For example, compared to the English list, Arabic might remove ; , ? /, and add
؟ \\ ، ؛.
Don't include purely math symbols such as +, =, *±, and so on.* *auxiliary*á à ă
â å ä ã ā æ ç é è ĕ ê ë ē í ì ĭ î ï ī ñ ó ò ŏ ô ö ø ō œ ú ù ŭ û ü ū
ÿ**Additional letters and punctuation** (beyond the minimal set) used in foreign
or technical words found in typical magazines, newspapers, &c.
For example, you could see the name Schröder in English in a magazine, so *ö* is
in the set. However, it is very uncommon to see *ł*, so that isn't in the
auxiliary set for English. Publication style guides, such as *The Economist
Style Guide* for English, are useful for this.
If your language has both upper and lowercase letters, only include the
lowercase (and İ for Turkish and similar languages).*index*A B C D E F G H I J K
L M N O P Q R S T U V W X Y Z**The “shortcut” letters** for quickly jumping to
sections of a sorted, indexed list (for an example, see
[mu.edu](http://www.google.com/url?q=http%3A%2F%2Fwww.mu.edu%2Ftools%2Fsiteindex.shtml&sa=D&sntz=1&usg=AFrqEzfh-HWKMHg_Z1R-AuawwGRrk5PRYA)).
The choice of letters should be appropriate for your language. Unlike the
**minimal** or **additional** characters, it should have either uppercase or
lowercase, depending on what is typical for your language (typically uppercase).

Any range of characters, such as “a b c d e” can be represented compactly as
“a-e”.

*   For charts of the standard (non-CJK) exemplar characters, see a chart of the
    [standard exemplar
    characters](http://www.unicode.org/cldr/charts/latest/by_type/core_data.alphabetic_information.main.html).
*   For more information, please see *[Section 5.6 Character
    Elements](http://unicode.org/reports/tr35/tr35-6.html#Character_Elements)*
    in *UTS#35: Locale Data Markup Language (LDML)*.

## **Non Spacing Marks**

*   If you see an escape sequence such as "\\u0301" in one of the exemplar sets
    in your language, this indicates a non-spacing character (diacritic) or
    control character. You can use the utility at
    <http://unicode.org/cldr/utility/list-unicodeset.jsp> to help you determine
    the meanings of such sequences.

## Handing Warnings in Exemplar characters

There are two kinds of warnings you can get with Exemplar Characters. *While
these are categorized as warnings, every effort should be made to fix them.*

**A. A particular translated item contains characters that aren't in the
exemplars.**
For example:

*   Suppose the currency code XAF is translated as "Φράγκο BEAC CFA" in Greek.
    That raises a warning because the "BEAC CFA" are not in the Greek exemplars.
*   Suppose that a currency symbol contains ৲ (BENGALI RUPEE MARK). That also
    raises a warning, even though it is a symbol and not a letter, because it
    has a script (Bengali).

Three possible solutions:

1.  If the character really is used in the language, add it to the appropriate
    exemplar set (**standard, auxiliary,…**).
    *   For example, the Bengali Rupee mark should be added to the **currency**
        exemplar set.
    *   To add to the Exemplar Characters, go first to the main view for your
        locale, then select **Other Items** \[Characters\]. For example, see
        [German
        characters](http://unicode.org/cldr/apps/survey?_=de&x=characters).
2.  If the character is part of a *'gloss'*, that is, it is parenthetically
    included for reference, and the gloss is all ASCII, then include it in
    brackets. You can use \[square brackets\] or (parentheses) in currencies.
    Everywhere else, please use only square brackets.
    *   So the XAF above can be fixed by changing it to "Φράγκο \[BEAC CFA\]" or
        "Φράγκο (BEAC CFA)". For the timezone name "ACT (Ακρ)", the fix is to
        change to "Ακρ \[ACT\]".
3.  If neither of these approaches is appropriate, try rephrasing the translated
    item to avoid the character.
4.  If it really can't be avoided, then please file a [new
    ticket](http://unicode.org/cldr/trac/newticket) describing the problem.

**B. The exemplar characters shouldn't contain a particular character.**

The **standard** characters shouldn't contain punctuation. They also should not
contain symbols, unless those symbols are only used with the language's writing
system (aka script). For example, the **standard** Bengali currency symbols
should contain the Bengali Rupee mark (which is Bengali-only), but should not
include the $ Dollar Sign (which is common across all scripts).
