# Coverage

[TOC]

## Introduction to Coverage Level

*   For an introduction to coverage level, see the appropriate section in TR#35,
    "[Coverage
    Levels](http://unicode.org/repos/cldr/trunk/specs/ldml/tr35-info.html#Coverage_Levels)".
*   To see how coverage level is used in the Survey Tool, see "[Advanced
    Features](http://cldr.unicode.org/index/survey-tool/guide#TOC-Advanced-Features)"
    in the Survey Tool guide

## **To set your organization's default coverage levels**

The **Coverage Level** determines the number of items that your people will see
for translation in each locale. The best target in general is *modern:* some
companies that use CLDR data require coverage at a *modern* level before they
will use the locale; others will use data that is less complete, such as
*moderate* or *basic*. If it is not feasible to attain modern coverage in a
given cycle, it is still best to set the coverage as high as feasible, such as
*moderate*.

The number of items at each level varies by locale, but is roughly the
following:

**Approximate CountCoverage Level** 200 minimal +300basic+200moderate+1500modern

To see your current coverage levels, look for your organization in
[Locales.txt](http://unicode.org/repos/cldr/trunk/tools/java/org/unicode/cldr/util/data/Locales.txt).
It is a simple plaintext file, where each line is of the form:

<organization> ; <language_code> ; <coverage_level> ; <language name - optional>

A # starts a comment, and a \* for the language_code means "all others".

An organization that focuses on a small number of locales will probably want to
have just a line added for those locales, such as:

Breton ; br ; modern Breton ; \* ; moderate To request a change in the default
coverage for your locale, file a [new
ticket](http://unicode.org/cldr/trac/newticket).

As part of CLDR v35, the coverage level has been refined further. See ticket
#[11498](http://unicode.org/cldr/trac/ticket/11498)

1.  *Basic Level*. The flexible date and time formats, such as *day + month*
    patterns, are moved down from *Moderate* to reflect the increased use of
    these patterns for the minimally viable locale data.
2.  *Modern Level.* Some lesser-used language names are pushed up to
    *Comprehensive*. (No data is removed: these are still accessible in the
    *Comprehensive* level.)
3.  Languages. The following languages have higher target levels, and can have
    missing items added.
    1.  *Basic Level :* Cebuano (ceb), Hausa (ha), Igbo (ig), Yoruba (yo)
    2.  *Modern Level:* Somali (so), Javanese (jv)
