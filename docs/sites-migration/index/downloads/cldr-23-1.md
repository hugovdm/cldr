# CLDR 23.1 Release Note

No. Date Rel. Note Data Charts Spec Delta SVN Tag **DTD Diffs**
**23.1** **2013-05-15** **[v23.1](cldr-23-1.md)**
[CLDR23.1](http://unicode.org/Public/cldr/23.1/)
**[Charts23.1](http://www.unicode.org/repos/cldr-aux/charts/23.1/index.html)**
**[LDML23](http://www.unicode.org/reports/tr35/tr35-31/tr35.html)**
**[Δ23.1](http://unicode.org/cldr/trac/query?status=closed&milestone=23.1)** `
**[release-23-1](http://unicode.org/cldr/trac/browser/tags/release-23-1)**`
`
**[ΔDTD23.1](http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-23-1/common/dtd&old=HEAD@tags/release-23/common/dtd)**`

Unicode CLDR 23.1 is an update release, designed to address specific issues that
have been arisen since the initial publish of CLDR 23.

Major features are described below. The table above points to the files for this
release. For a description of their purpose and format, see the
[Key](cldr-23.md).

[TOC]

## Features

The main features include the following (see the Delta link above for a full
list of changes, aside from data additions and corrections):

### Structural additions and changes

*   None

### Data changes

*   Fix the ordering of the digits in the N'ko numbering system.
    \[[#5791](http://unicode.org/cldr/trac/ticket/5791)\]
*   Reinstatement of data supporting the Suriname Time Zone, which was
    incorrectly deleted in CLDR 23.
    \[[#5931](http://unicode.org/cldr/trac/ticket/5931)\]
*   Additions to support Kosovo as a separate territory with territory code
    "XK". This is currently a private use code which is not in the IANA language
    subtag registry. 3 new locales have been added: sq_XK (Albanian), sr_Cyrl_XK
    (Serbian - Cyrillic), and sr_Latn_XK (Serbian - Latin). Translations of the
    territory name "Kosovo" have also been added to many locales.
    \[[#5865](http://unicode.org/cldr/trac/ticket/5865)\]

### Spec changes

*   None - The CLDR 23 LDML specification also applies to CLDR 23.1 data.

### Conversion tools (including JSON support)

*   Many fixes and enhancements have been made to the JSON conversion utility,
    located at org.unicode.cldr.json.Ldml2JsonConverter in the tools.zip. This
    tool allows consumers of CLDR data to convert data from the LDML format to a
    more directly consumable JSON format in a standardized way, according to
    the[ CLDR Specification for JSON Bindings](../cldr-spec/json.md). A sample
    of the JSON produced by this tool can be downloaded
    [here](http://unicode.org/Public/cldr/23.1/json.zip). The JSON sample
    contains data only for a subset of the published CLDR locales, and is
    intended for reference purposes only. The JSON conversion utility allows
    users to create a customized configuration to filter and organize the
    resulting JSON data, converting just those pieces of data that are needed.
    The utility also allows users to create JSON for a selected list of locales,
    and also to filter data by draft status or coverage level. For more details
    on the JSON conversion utility, refer to the README file located in the[
    downloadable JSON sample
    data](http://unicode.org/Public/cldr/23.1/json.zip).

### BCP47 enhancements (since CLDR 23)

*   None

### Key

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
