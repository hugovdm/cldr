# Unicode CLDR Project

![image](http://cldr.org)

## News

2020-06-04CLDR v38 General Submission began — see
[InfoHub](../translation/_index.md) 2020-04-23 [CLDR
v37](downloads/cldr-37/index.md) released 2020-03-11 [CLDR
v36.1](http://cldr.unicode.org/index/downloads/cldr-36?pli=1#TOC-CLDR-36.1)
released 2020-01-10 New CLDR subcommittee: [Message
Formatting](http://blog.unicode.org/2020/01/new-unicode-working-group-message.html)

## What is CLDR?

[TOC]

The Unicode CLDR provides key building blocks for software to support the
world's languages, with the largest and most extensive standard repository of
locale data available. This data is used by a [wide spectrum of
companies](#TOC-Who-uses-CLDR-) for their software internationalization and
localization, adapting software to the conventions of different languages for
such common software tasks. It includes:

*   **Locale-specific patterns for formatting and parsing:** dates, times,
    timezones, numbers and currency values, measurement units,…
*   **Translations of names:** languages, scripts, countries and regions,
    currencies, eras, months, weekdays, day periods, time zones, cities, and
    time units, emoji characters and sequences (and search keywords),…
*   **Language & script information:** characters used; plural cases; gender of
    lists; capitalization; rules for sorting & searching; writing direction;
    transliteration rules; rules for spelling out numbers; rules for segmenting
    text into graphemes, words, and sentences; keyboard layouts…
*   **Country information:** language usage, currency information, calendar
    preference, week conventions,…
*   **Validity:** Definitions, aliases, and validity information for Unicode
    locales, languages, scripts, regions, and extensions,…

CLDR uses the XML format provided by *[UTS #35: Unicode Locale Data Markup
Language (LDML)](http://www.unicode.org/reports/tr35/)*. LDML is a format used
not only for CLDR, but also for general interchange of locale data, such as in
Microsoft's .NET.

## Who uses CLDR?

[Presentation](https://docs.google.com/presentation/d/1LDXP-LYQpaVJRWWX6EejgkRGFUaFwo83t8Ly-IPll8Y/edit?usp=sharing)
![Presentation
](https://docs.google.com/presentation/d/1LDXP-LYQpaVJRWWX6EejgkRGFUaFwo83t8Ly-IPll8Y/edit?usp=sharing){width="200"
height="124"}

Some of the companies and organizations that use CLDR are:

*   Apple (macOS, iOS, watchOS, tvOS, and several applications; Apple Mobile
    Device Support and iTunes for Windows; …)
*   Google (Web Search, Chrome, Android, Adwords, Google+, Google Maps, Blogger,
    Google Analytics, …)
*   IBM (DB2, Lotus, Websphere, Tivoli, Rational, AIX, i/OS, z/OS,…)
*   Microsoft (Windows, Office, Visual Studio, …)

*and many others, including:*

*   ABAS Software, Adobe, Amazon (Kindle), Amdocs, Apache, Appian, Argonne
    National Laboratory, Avaya, Babel (Pocoo library), BAE Systems Geospatial
    eXploitation Products, BEA, BluePhoenix Solutions, BMC Software, Boost,
    BroadJump, Business Objects, caris, CERN, Debian Linux, Dell, Eclipse, eBay,
    EMC Corporation, ESRI, Firebird RDBMS, FreeBSD, Gentoo Linux, GroundWork
    Open Source, GTK+, Harman/Becker Automotive Systems GmbH, HP, Hyperion,
    Inktomi, Innodata Isogen, Informatica, Intel, Interlogics, IONA, IXOS,
    Jikes, jQuery, Library of Congress, Mathworks, Mozilla, Netezza, OpenOffice,
    Oracle (Solaris, Java), Lawson Software, Leica Geosystems GIS & Mapping LLC,
    Mandrake Linux, OCLC, Perl, Progress Software, Python, Qt, QNX, Rogue Wave,
    SAP, Shutterstock, SIL, SPSS, Software AG, SuSE, Symantec, Teradata (NCR),
    ToolAware, Trend Micro, Twitter, Virage, webMethods, Wikimedia Foundation
    (Wikipedia), Wine, WMS Gaming, XyEnterprise, Yahoo!, Yelp

## How to Use?

Most developers will use CLDR indirectly, via a set of software libraries, such
as [ICU](http://site.icu-project.org/),
[Closure](https://developers.google.com/closure/library/), or
[TwitterCLDR](https://blog.twitter.com/2012/twittercldr-improving-internationalization-support-in-ruby).
These libraries typically compile the CLDR data into a format that is compact
and easy for the library to load and use.

For those interested in the source CLDR data, it is available for each release
in the XML format specified by *[LDML](http://www.unicode.org/reports/tr35/)*.
There are also tools that will convert to JSON and POSIX format. For more
information, see [CLDR Releases/Downloads](downloads/index.md).

## How to Contribute?

CLDR is a collaborative project, which benefits by having people join and
contribute. There are multiple ways to contribute to CLDR.

### Translations and other language data

CLDR has an online tool to gather data from multiple sources, called the [Survey
Tool](survey-tool/index.md). It is deployed twice a year to gather data for new
structure, and make corrections in previously-released data. Multiple people can
contribute for the same data item, with a resolution process deciding the
outcome.

Individuals (vetters) can contribute data for their language by [setting up an
account](survey-tool/accounts.md). They can also organize a community of
speakers of their languages to contribute data, discuss issues, etc.

Qualifying organizations (companies, governments, institutions, etc) can ask to
be set up as Organizations. Vetters added by the organizations manager get the
organization’s vote count. Please file a
[ticket](http://cldr.unicode.org/index/bug-reports) for this.

Unicode [voting members](https://unicode.org/consortium/members.html) can get
more heavily involved, and join the technical committee, which is the ultimate
arbiter for the structure and content of CLDR. That committee is responsible for
assessing the Survey Tool features, proposals for additions or changes to
structure, bug fixes, and final resolution of each release of CLDR.

### Code and Structure

The CLDR tooling supports the interactive Survey Tool, plus all of the tooling
necessary to test and process the release. Programmers interested in
contributing to the tooling are welcome; they may also be interested in
contributing to [ICU](http://site.icu-project.org/), which uses CLDR data. For
more information, see <http://cldr.unicode.org/development>.

CLDR covers many different types of data, but not everything. For projects which
may cover other types of data, see [Other Projects](../other-projects.md).

### Tickets

People may file [tickets](http://cldr.unicode.org/index/bug-reports) with bug
fixes or feature requests. Once a ticket is approved, they can also create pull
requests on [GitHub](https://github.com/unicode-org/cldr).

## Who has contributed?

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](http://cldr.unicode.org/index/acknowledgments) page for a full
listing.

## What is the Schedule?

CLDR has a regular schedule, with two cycles per year. There is a consistent
release schedule each year so that implementations can plan ahead. The actual
dates for each phase are somewhat adjusted for each release: in particular, the
dates will usually fall on Wednesdays, and may change for holidays.

The two important periods for translators are:

*   ***Submission***: translators are asked to flesh out missing data, and check
    for consistency.
*   ***Vetting***: translators are asked to review all changed or conflicted
    values, and reach consensus.

The details for the current release are found in [Current CLDR
Cycle](https://docs.google.com/spreadsheets/d/1N6inI5R84UoYlRwuCNPBOAP7ri4q2CmJmh8DC5g-S6c/edit#gid=1680747936).
