# CLDR 33.1

No. Date Rel. Note Data Charts Spec Delta SVN Tag DTD Diffs **DTD Δs** 33.1
2018-06-20 [v33.1](http://cldr.unicode.org/index/downloads/cldr-33-1)
[CLDR33.1](http://unicode.org/Public/cldr/33.1/)
[Charts34](http://www.unicode.org/cldr/charts/34)\*
[LDML33](https://www.unicode.org/reports/tr35/tr35-51/tr35.html)\*
[Δ33.1](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=33.1&group=component&max=999)
[release-33-1](http://www.unicode.org/repos/cldr/tags/release-33-1/)
[`ΔDTD33.1`](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-33/common/dtd&old=HEAD@tags/release-33-1/common/dtd)
[33](http://www.unicode.org/cldr/charts/33/supplemental/dtd_deltas.html)\*

## Overview

Unicode CLDR 33.1 is an update to CLDR 33 that focuses on [Unicode
11.0](http://blog.unicode.org/2018/06/announcing-unicode-standard-version-110.html)
support. Improvements in this release include:

*   **Data**
    *   Updates to Unicode 11.0
    *   Adds annotations (names and keywords) for Unicode 11.0 emoji, and makes
        improvements to previously-existing annotations.
    *   Updates Chinese collation stroke order from Unicode 7.0 to Unicode 11.0,
        after tooling bug fixes
*   **Structure\***
    *   No changes. The **DTD Δs** and **DTD Diffs** links above point to v33.
*   **Specification\***
    *   There is no LDML 33.1 document. Instead, only amendments to v33 are
        provided, as described below in [**Specification
        Amendments**](cldr-33-1.md).
*   **Charts\***
    *   There are no charts specifically for v33.1. The link above provides the
        [Charts34](http://www.unicode.org/cldr/charts/34/) (currently under
        development). The differences from
        [Charts33](http://www.unicode.org/cldr/charts/33/) are mostly captured
        in the [annotations
        charts](https://www.unicode.org/cldr/charts/34/annotations/index.html)
        and in the annotations fields of other charts such as [delta for
        German](https://www.unicode.org/cldr/charts/34/delta/de.html) or [By
        Type:
        smileys](https://www.unicode.org/cldr/charts/34/by_type/characters.smileys.html).

For more details, see the [list of bug
fixes](http://unicode.org/cldr/trac/query?resolution=fixed&milestone=33.1&group=component&max=999).

## Specification Amendments

There is not a new version of the LDML spec. Instead, the following are
amendments to [LDML33](https://www.unicode.org/reports/tr35/tr35-51/tr35.html).
The changed text is indicated below by green highlighting

### 14.1 Synthesizing Sequence Names

…

1.  If **sequence** is an **emoji flag sequence**, look up the territory name in
    CLDR for the corresponding ASCII characters. Set **suffixName** to that, and
    **prefixName** to the characterLabel for "flag", and go to step 10.
    *   For example, "🇵🇫" has the regional indicator symbols **PF** and would
        map to “Flagge: Französisch-Polynesien” in German.
2.  If **sequence** is an **emoji tag sequence**, look up the subdivision name
    in CLDR for the corresponding ASCII characters and compose as for **emoji
    flag sequence**.
    *   For example, "🏴󠁧󠁢󠁳󠁣󠁴󠁿" has TAG characters **gbsct** and would map to
        “Flagge: Schottland” in German.
3.  If **sequence** is a keycap sequence or 🔟, use the characterLabel for
    "keycap" as the **prefixName** and set the **suffix** to be the ASCII
    characters in the sequence (or "10" in the case of 🔟), then go to step 8.
    *   For example, "#⃣" would map to "Taste: #" in German.
4.  …
5.  If **sequence** contains any emoji modifiers or hair components, move them
    (in order) into **suffix**, removing them from **sequence**.
    *   For example, "👨🏿‍🦰" would map to "Mann: dunkle Hautfarbe, rotes Haar".
6.  …
7.  …
8.  Transform **sequence** and append to **prefixName**, by successively getting
    names for the longest subsequences, skipping any singleton ZWJ characters.
    If there is more than one name, use the listPatterns for "unit-short" to
    link them. This uses the patterns for "2", "start", "middle", and "end".
9.  …
10. …

The /annotationsDerived/ folder has the available composed names, pre-built.

…

## Migration

*   Updates German AM/PM strings to follow the English, to meet most common
    expectations of users of 12hr formats.

## Known Issues

1.  Some of the main CLDR locales are missing a few Unicode 11.0 annotations
    (should be fixed in v34):
    [#11193](https://unicode.org/cldr/trac/ticket/11193)
2.  The segmentation rules have not been updated for changes in Unicode 11.0.
    This does not affect ICU, since the rules there were changed manually.
    Implementers may wish to patch their v33.1 versions with the data in
    [#11203](https://unicode.org/cldr/trac/ticket/11203) if they use the
    segmentation rules independent of ICU. The changes include simplifying the
    break rules for Emoji and not breaking within strings of white space.
3.  The ICU4J libraries included in v33.1 were not updated to ICU 62.0. There
    are no known problems with using ICU 61.0, but implementers may want to
    update their copies to ICU 62.0.

## Acknowledgments

Many people have made significant contributions to CLDR and LDML; see the
[Acknowledgments](../acknowledgments.md) page for a full listing. The
contributors to v33.1 will appear on the page later, when v34 is released.

## Key to Header Links

Rel. Note a general description of the contents of the release, and any relevant
notes about the release Data a set of zip files containing the contents of the
release (the files are complete in themselves, and do not require files from
earlier releases -- for the structure of the zip file, see [Repository
Organization](http://cldr.unicode.org/index/downloads#Repository_Organization))
Charts a set of charts showing some of the data in the release. Spec the version
of [UTS #35: LDML](http://www.unicode.org/reports/tr35/) that corresponds to the
release Delta a list of all the bug fixes and features in the release, which be
used to get the precise corresponding file changes using
[BugDiffs](http://unicode.org/cgi-bin/bugdiffs.pl) SVN Tag the files in the
release, accessible via via [Repository
Access](http://cldr.unicode.org/index/downloads#latest_draft_version). *For more
details see [CLDR Releases (Downloads)](index.md)* DTD Diffs a diff of the DTD
source files DTD Δs a link pointing to a charts of changes in the DTDs over
time.

---

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to CLDR
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).

For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.
