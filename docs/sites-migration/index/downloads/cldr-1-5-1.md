# CLDR 1.5.1 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases
(Downloads)](http://unicode.org/cldr/data/docs/web/repository_access.html). *In
terms of license, the Unicode                   [Terms of
Use](http://unicode.org/copyright.html) apply; in particular,
[Exhibit 1](http://unicode.org/copyright.html#Exhibit1).*

No.                                                              Date
Rel. Note                                                               Data
Spec                                                            Delta
CVS Tag
**1.5.1** **2007-12-21**
**[Version1.5.1](http://unicode.org/cldr/data/docs/web/version/1.5.1.html)**
**[CLDR1.5.1](http://unicode.org/Public/cldr/1.5.1/)**
**[LDML1.5.1](http://www.unicode.org/reports/tr35/tr35-9.html)**
**[Changes1.5.1](http://www.unicode.org/cldr/bugs/locale-bugs/closed?expression=target.*1%5C.5%5C.1)**
**`release-1-5-1`**

CLDR 1.5.1 is an update release, with no new translations.
The main changes are a significant additions to the data structure and
process for computing timezone names, and additional data for finding
default script or country given a language, or the converse. The structure
has also been updated for the latest version of BCP 47, and new currency
codes.

The main changes in the LDML specification were:

    Extensive rewrite of *Appendix J: Time Zone Display Names*,
    primarily due to refinements to the metazone process. This also caused some
    changes in Appendix F: Date Format Patterns.

    Made the date           range handling uniform, with new *Section 5.2.1
    Dates and Date Ranges,*                 and related changes particularly to
    C.1 and C.5 in Appendix C: Supplemental Data.

    Added *Appendix C10.            [Likely
    Subtags](http://www.unicode.org/reports/tr35/tr35-9.html#Likely_Subtags)*
