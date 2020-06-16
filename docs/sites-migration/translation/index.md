# Information Hub for Linguists

2020-1-29 Survey tool is closed 2020-1-27 Known issues section. Tip on "same as
code" errors

The pages listed to the left provide guidelines for translation of CLDR strings.
For an overview of the tools, please read the [Survey Tool
Guide](getting-started/guide/index.md) before starting.

**Current Survey Tool stage: v37 CLOSED**

Thank you to all contributors for your work during this contribution period!
Your efforts help make the language data in CLDR be rich and relevant.

Please refer to the Milestone Schedule in the left navigation. *However, the
exact dates will be refined by the committee as we look across different needs
and availability.*

CLDR 37 is a limited release in terms of data updates. This is a unique cycle
where we will be announcing two releases:

*   **v37**: This is a scoped data collection, which means that the data points
    that are scoped for contribution will be editable to you. Please read[ full
    vs. limited-submission](getting-started/survey-tool-phases/index.md).
*   **v36.1**: An update to v36 with certain cherry-picked data from v37. There
    is no impact to data contribution using the survey tool. You can ignore any
    communication around this dot release.

## Prerequisites

1.  Know[ Data stability](getting-started/data-stabli.md) expectations
2.  Know topics under @**Getting Started** to ensure familiarity on what you may
    encounter working in the Survey Tool.
3.  @**General translation guides** are the customary expectations for all the
    vetting work.
4.  Please visit this page (*Information hub for linguists)* every other day,
    and check for news at the top. The information on this page will be updated
    at least weekly. [Bookmark it](index.md)!

## What's new in this cycle

### Survey Tool

There are no new/updates to Survey tool features introduced for this cycle.
However, there's an on-going effort for performance improvements that you'll
mostly notice in the right information pane.

*   V37 is a scoped release and only those data points that are scoped for your
    language will be enabled. Please read[ full vs.
    limited-submission](getting-started/survey-tool-phases/index.md).
    For example, the [Dari language
    name](https://st.unicode.org/cldr-apps/v#/USER/Languages_O_S/51846c8690c6cf1b):

*   Errors in **Others** column can be ignored. In this scoped release, the
    errors in the Others column may be distracting when they appear in fields
    where the data is not open for contribution. Ignore Errors in **Others**
    column. See [Handling Errors and
    Warnings](getting-started/errors-and-warnings/index.md).

### New data

Following are new data that have been added for data collection in this release.
There are approximately 180 items in total: as all other data in CLDR, the exact
number of items may vary by locale. *You should also fix any Missing values
showing in the
[Dashboard](https://st.unicode.org/cldr-apps/v#r_vetting_json/USER//) that were
not addressed in the last release.*

*   Units
    *   Compound Units for composing unit names for fallbacks. The short and
        long forms are only to be used for fallbacks, because composition may
        not be grammatically correct. See the
        [Units](http://cldr.unicode.org/translation/units-1/units) page for more
        information on Compound Units and fallbacks.
        There are two new types of Compound Units in v37. These are used used
        with a unit like
        [meter](https://st.unicode.org/cldr-apps/v#/USER/Length/3553a6f8542abcf8)
        to form [square
        meter](https://st.unicode.org/cldr-apps/v#/USER/Area/5888c3421f06626c),
        etc.:
        *   [square
            {0}](https://st.unicode.org/cldr-apps/v#/USER/CompoundUnits/445021b5baa595e7)
        *   cubic {0}
    *   Metric Unit (International System of Unit) prefixes. These are used used
        with a unit like
        [meter](https://st.unicode.org/cldr-apps/v#/USER/Length/3553a6f8542abcf8)
        to form
        [decimeter](https://st.unicode.org/cldr-apps/v#/USER/Length/ce4591152ece6f2),
        etc. The short and long forms are only to be used for fallbacks, because
        composition may not be grammatically correct.
        *   [deci{0}](https://st.unicode.org/cldr-apps/v#/USER/CompoundUnits/30817f9542747e57),
            mega{0}, ...
    *   Please read the new documentation under [Compound
        Units](units-1/units.md)
*   Emoji & Symbols
    *   Continuing from the CLDR v36 release, where the Emoji 13 data was
        collected, in this version, you will find New and Updates to the work
        that was done to in v36.
        *   Final v13.0 Emoji: including [black
            cat](https://cldr-smoke.unicode.org/smoketest/v#/fr/Animals_Nature/52a5f12dbada71f6),
            polar bear, person feeding baby, ...
        *   There are some changes to English names for clarity. Be sure to
            watch out for those and review the English changes section in the
            Dashboard.
    *   New symbols
        *   Plain character symbols and punctuation, such as
            [€](https://cldr-smoke.unicode.org/smoketest/v#/fr/Symbols2/47925556fd2904b5),
            √, », ¹, §, ...
*   The following languages are open for contribution in all areas:
    *   **new:** Maithili (mai), Manipuri (mni), Santali (sat), Konkani (kok),
        Sindhi (sd_Deva), Sundanese (su), and Nigerian Pidgin (pcm).
    *   **address problems:** Cebuano (ceb)
    *   *Many languages are not included in the limited release, and need to
        wait for the full release in the CLDR v38 cycle.*

## Translation quality

Following are areas where we have seen data quality issues or those that need
your attention more carefully.

*   Avoiding English
    *   For items that do not work in your language, please don't simply use
        English. Find a solution that works for your language. For example, if
        your language doesn't have a concept of "quarters", use a translation
        that describes the concept "three-month period" rather than
        “quarter-of-a-year”.
    *   For example, a number of Pashto items were found to be in English and
        has been removed. Please correct the situation and supply the missing
        data, reviewing the others for consistency.
        (#[11565](http://unicode.org/cldr/trac/ticket/11565))

## Translation guides: updated sections

The following topics have been updated.

*   The Translation Guide's navigation has been restructured, and many of the
    old pages have been either consolidated, removed, or updated. See the left
    Table of Contents under Translation Guides. If you are new to CLDR, use the
    [@Getting Started](getting-started/index.md) topics to get started.

## Known Issues

Please review this list before getting started to avoid creating duplicate
tickets. This list will be updated as fixes are made available in Survey Tool
Production. If you hit a problem, please [file a
ticket](http://unicode.org/cldr/trac/newticket).

**Updated on 2020-01-27**

1.  Dealing with "Same as code" errors:
    1.  If the error appears under Typography, you can ignore.
        \[[CLDR-13552](https://unicode-org.atlassian.net/browse/CLDR-13552)\]
    2.  We also made a fix recently to enable the Error in the Winning column,
        where they only appeared in Others column, which prevented you from
        being able to work on them.
        \[[CLDR-13551](https://unicode-org.atlassian.net/browse/CLDR-13551)\]
    3.  If you are working in Hausa, Yoruba, Igbo, or Malay, please note that
        the committee is planning to clean up with post processing.
        \[[CLDR-13553](https://unicode-org.atlassian.net/browse/CLDR-13553)\]
2.  Conflict with existing Gender neutral Emoji. If your languages used a gender
    specific names for existing gender neutral emoji (e.g. "person in tuxedo),
    correct names for the new gender specific emoji couldn't be handled due to
    the Uniqueness Error.
    *   **Revisit the gender specific/neutral names**: The older gender neutral
        emoji data points are NOW open in the Survey Tool.
3.  Some language names in the Comprehensive coverage are showing up with Error
    "The value is same as the code".
    [CLDR-13499](https://unicode-org.atlassian.net/browse/CLDR-13499)
    *   **Workaround:** Abstain your votes on Code
        1.  Go to Dashboard
        2.  Click on the item and go to the item
        3.  If the background color is grey and you have voted on the item,
            Abstain your vote. If you did not vote, ignore.
            **Note:** The Vetter who voted on the Code item needs to clear this
            error!
        4.  If the background color is not grey (i.e. the item is not in
            comprehensive), review the item and add in the Real value.
            1.  If the code value is truly correct, open a bug to report or Flag
                the item if available.
4.  Dashboard is working in a *Scoped* mode, which means: If you are late in
    getting started, you will not see Missing item to easily find the new data
    points.
    *   **Workaround**: Go to the New data point items directly
        1.  [Dari language
            name](https://st.unicode.org/cldr-apps/v#/USER/Languages_O_S/51846c8690c6cf1b):
        2.  [Compound
            Units](https://st.unicode.org/cldr-apps/v#/USER/CompoundUnits/)
        3.  Emoji: Start from [People &
            Body](https://st.unicode.org/cldr-apps/v#/USER/People/) and look for
            items that are open for contributions.
        4.  [Symbols](https://st.unicode.org/cldr-apps/v#/USER/Symbols2/)
        5.  At the top of a page, the Abstain vote count will tell you how many
            data point on a particular page needs your
            attention.![image](Abstain.PNG)

**Older**

1.  Some languages are not open for contribution.
    [CLDR-13506](https://unicode-org.atlassian.net/browse/CLDR-13506)
    *   **Workaround:** If your language is locked, please wait until v38
        contribution cycle.
2.  Images for the plain symbols, such as
    [€](https://cldr-smoke.unicode.org/smoketest/v#/fr/Symbols2/47925556fd2904b5),
    √, », ¹, §, ... do not have images in the info pane.
    *   **Workaround:** Unlike the new emoji, your browser should display them
        in the Code column.
3.  Brackets "\[ \]" under Alphabetic information are used to group the
    alphabetic information and they are not part of the data. Ticket
    [CLDR-13180](https://unicode-org.atlassian.net/browse/CLDR-13180)
    *   **Workaround:** Please ignore the \[ \] in the Alphabetic information
        and do not try to update the data to exclude the \[\].

## Resolved Issues

The following list of previously listed on the known issues have now been
resolved:

**2019-12-19**

1.  Some languages are not open for contribution,
    [CLDR-13503](https://unicode-org.atlassian.net/browse/CLDR-13503), has been
    resolved for Nigerian Pidgin and Caddo.
2.  Some of the links to Translation guides from Survey tool information pane
    didn't work. Ticket
    [CLDR-13452](https://unicode-org.atlassian.net/browse/CLDR-13452)
3.  Dashboard showed false errors. Ticket
    [CLDR-13457](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Funicode-org.atlassian.net%2Fbrowse%2FCLDR-13457&data=02%7C01%7Ckristil%40microsoft.com%7Cc737f92bcff044b85c9f08d77a7b483e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637112542240243599&sdata=SsvcDY4fgbI450cZYmX%2FifkSZ%2BJnKJuixY%2FaNoe096A%3D&reserved=0).
    *   For compound languages — those with _ such as \[Portuguese ► pt_BR\] —
        the Dashboard used to incorrectly show an error.
4.  [CLDR-13360](https://unicode-org.atlassian.net/browse/CLDR-13360)English name of the symbol \[∞ -name\] needed to be changed to to distinguish it from the emoji \[♾ -name\]:
5.  Dashboard appeared to be empty/broken:
    [CLDR-13478](https://unicode-org.atlassian.net/browse/CLDR-13478)
    *   When there are no items to report, the page used to look like it isn't
        working right.
        **NOTE**: you may have to [clear your browser's Javascript
        cache](http://cldr.unicode.org/translation/getting-started/empty-cache)
        to see it correctly.
6.  Emoji gender images in the information pane on the right were incorrect:
    [CLDR-13476](https://unicode-org.atlassian.net/browse/CLDR-13476)
7.  The examples for the new
    [CompoundUnits](https://st.unicode.org/cldr-apps/v#/USER/CompoundUnits/)
    were incorrect. Ticket
    [CLDR-13479](https://unicode-org.atlassian.net/browse/CLDR-13479)
    *   Instead of \[1.5 gigameters\] and \[1.5 square meters\], people were
        seeing the incorrect examples \[giga1.5 meters\] and \[square 1.5
        meters\]

**Older resolved issues**

1.  False Errors are showing up for Compound Units. Ticket
    [CLDR-13460](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Funicode-org.atlassian.net%2Fbrowse%2FCLDR-13460&data=02%7C01%7Ckristil%40microsoft.com%7Cc737f92bcff044b85c9f08d77a7b483e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637112542240243599&sdata=7c9CRm5rOJLkT2m50wpDl9Oq4kdxKRwqdnnDk48kPjQ%3D&reserved=0).
    *   The tests for duplicate names should be *case-sensitive* for the
        compound unit prefixes (such as
        [m{0}](https://cldr-smoke.unicode.org/smoketest/v#/USER/CompoundUnits/252f75ed97f14297)).
        It thus shows false errors when two items differ by case.
2.  Dashboard does not show all Error/Missing values. Ticket
    [CLDR-13457](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Funicode-org.atlassian.net%2Fbrowse%2FCLDR-13457&data=02%7C01%7Ckristil%40microsoft.com%7Cc737f92bcff044b85c9f08d77a7b483e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637112542240243599&sdata=SsvcDY4fgbI450cZYmX%2FifkSZ%2BJnKJuixY%2FaNoe096A%3D&reserved=0).
