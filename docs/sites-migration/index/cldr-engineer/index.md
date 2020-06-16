# CLDR SW Engineer Posting

# Background

The Unicode CLDR provides key building blocks for software to support the
world's languages, with the largest and most extensive standard repository of
locale data available. (See [cldr.unicode.org](http://cldr.unicode.org/).) It is
a key component of [ICU](http://site.icu-project.org/), which is widely used for
fundamental internationalization support (on every smartphone, for example). The
data is collected in a joint effort by multiple organizations in Unicode’s CLDR
“Survey Tool”; see [Survey tool
guide](http://cldr.unicode.org/index/survey-tool/guide). The tool provides
mechanisms for resolving conflicts, including a voting resolution process, and a
forum for discussing disputes. It also provides many tests on the quality of the
entered data to avoid problems such as [duplicate
names](http://cldr.unicode.org/translation/country-names).

# Goals

Unicode is looking for one or more contract engineers to work on the CLDR survey
tool. The main goals are performance improvement and functional enhancements to
help increase the data quality. The period may last up to the end of 2018. The
tasks can be split among part-time contractors, according to expertise.

    Performance improvement: The tool was designed for a much smaller dataset
    than it currently handles, both in terms of the number of entries per
    language and the [number of
    languages](http://cldr.unicode.org/index/downloads/cldr-32#TOC-Growth). When
    the tool is slow, it materially affects the throughput of translators.
    Speeding up the tool reduces the cost of translations, and provides more
    motivation for others to contribute.

    Functional enhancements: Improving functionalities will make entering
    translations and fixing errors easier and more efficient. The enhancements
    would include UI improvements to make the workflow simpler; make it easier
    for errors to be fixed (such as duplicate names and “logical groupings”);
    and fix some technical debt on bugs that have accumulated.

*For more details, see [Statement of Work for CLDR Contract Engineers](sow.md).*

# Requirements

The role requires expertise in the following areas:

    Java servlet/SQL design and implementation skills (backend)

    HTML/CSS/JavaScript design and implementation skills (frontend)

Bonus skills (not required):

    XML, Unicode

    SVN (Eclipse Subversion) source code management

    Interest in natural languages and/or internationalization

Please send your CV to [jobs@unicode.org](mailto:jobs@unicode.org).
