# Core Data Submission Form

*Please use this form to provide the "[Core XML Data](index.md)" for a new
locale.*

## 0. Administrative / Locale Identifier

0.a) Requester's Name and Email address:

0.b) Locale name:

0.c) Locale identifier(s) (include scripts and territories):

*   *See [Picking the Right Language
    Identifier](http://cldr.unicode.org/index/cldr-spec/picking-the-right-language-code).*

## 1. Exemplar Sets

*   *See [Exemplar
    Characters](../../../translation/-core-data/characters/index.md)*

1.a) **Main**: The minimal characters required for your language (other than
punctuation)

1.b) **Auxiliary**: Additional letters and punctuation (beyond the minimal set)
used in foreign or technical words found in typical magazines, newspapers, &c.

1.c) **Index**: The “shortcut” letters for quickly jumping to sections of a
sorted, indexed list (for an example, see
[mu.edu](http://www.mu.edu/tools/siteindex.shtml)).

1.d) **Punctuation**: The punctuation characters customarily used with your
language.

## 2. Orientation

*   *See [Layout
    Elements](http://www.unicode.org/reports/tr35/#Layout_Elements)*

2.a) **Characters**: Which direction are characters written in the language?

( **left-to-right** (*most)*, **right-to-left** (*Arabic, Hebrew, ...)*,
**top-to-bottom,** or **bottom-to-top** )

2.b) **Lines:** Which direction are lines written in the language?

( **top-to-bottom** (*most)*, **bottom-to-top, left-to-right, right-to-left** )

## 3. Plural Rules

3.a) What are the plural rules for this language?

*   *If your language behaves just like another one that we have plurals for,
    please supply it.*
*   *Otherwise, follow the guidelines in [Plural
    Rules](http://cldr.unicode.org/index/cldr-spec/plural-rules). Note, plurals
    are complex—if you get stuck, please contact us or simply note in this
    section that you are having difficulty.*

## 4. Country Data and Default Content

4.a) Is the data in
<http://www.unicode.org/cldr/charts/latest/supplemental/language_territory_information.html>
correct for the language and territory? If not, please provide correct data:

4.b) What should the default content locale be for the language? For example,
German, Germany (`de_DE`) is the default content for German (`de`). This is
usually the country with largest population using that language, and the normal
script for that country's use of that language:

*   *See: <http://cldr.unicode.org/translation/default-content>*

## 5. Romanization (for non-Latin scripts only)

5.a) What is the Romanization table for transforming the script into Latin?

*   *If you can link to a chart with Unicode characters (such as
    <http://www.eki.ee/wgrs/rom1_mnc.htm>), please do so.*
*   *Otherwise, please attach a spreadsheet.*
