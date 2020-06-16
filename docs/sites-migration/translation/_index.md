# Information Hub for Linguists

2020-06-15New information on [Compound Units](units-1/units.md) 2020-06-03 CLDR
v38 open for General submission
2020-05-29 CLDR v38 shakedown start

[TOC]

This page and the pages listed to the left provide guidelines for translation of
CLDR strings.

*   Please read this page completely before starting, and visit this page
    (*Information hub for linguists)* every other day, and check for news at the
    top. The information on this page will be updated at least weekly. [Bookmark
    it](_index.md)!
*   If you are new to the online tool (or just want to refresh your memory),
    please read the [Survey Tool Guide](getting-started/guide/index.md) before
    starting.
*   Once you are ready, go to the [Survey
    Tool](https://st.unicode.org/cldr-apps/) and log in.

---

**Current Survey Tool stage: v38 is open for General submission**

Please refer to the Milestone Schedule in the left navigation for detailed
schedule. *However, please note that the exact dates will be refined by the
committee as we look across different needs and availability.*

Prerequisites

1.  Know[ Data stability](getting-started/data-stabli.md) expectations
2.  Know topics under @**Getting Started** to ensure familiarity on what you may
    encounter working in the Survey Tool.
3.  @**General translation guides** are the customary expectations for all the
    vetting work.
4.  **Disconnect error.** If you see a persistent Loading error with a
    disconnect message or other odd behavior, please [empty your
    cache](http://cldr.unicode.org/translation/getting-started/empty-cache).
5.  Survey Tool email notification may be going to your spam folder. Check your
    spam folder regularly.

## What's new in this cycle

*   If you are new to CLDR contribution, please read the prerequisites above
    first.
*   If you have contributed to CLDR in the past, below are the information
    that's new or have changed since the last release.

## Notation

💡marks important translation tipsgreenmarks items that need special
attentionyellowmarks new or changed text

### Survey Tool

*   In the Dashboard, the category "New" has been misleading and it's been
    renamed to "**Changed**" to reflect the category accurately. See details
    under
    [Changed](http://cldr.unicode.org/translation/getting-started/guide#TOC-Changed-)
    in the Survey Tool Guides.
*   Major updates with the forum feature in the Survey Tool to incorporate a
    workflow.
    💡 Please read the details under [Forum](getting-started/guide/index.md) in
    the Survey Tool Guide.
    The enhancements include:

    *   [Forum workflow](getting-started/guide/index.md) from creating new posts
        to closing
    *   [How to create new posts](getting-started/guide/index.md): **Request**
        or **Discuss**
    *   [Responding to Request posts](getting-started/guide/index.md):
        **Agree**, **Decline**, **Comment**
    *   [Responding to Discuss posts](getting-started/guide/index.md):
        **Comment**
    *   [New Filters in the Forum view](getting-started/guide/index.md):Needing
        action, Open requests by you, Open topics, All topics
    *   [Forum posts integration in Dashboard](getting-started/guide/index.md).
        The categories include: **Needing action**, **Open requests by you**,
        and **Open topics.**
    *   Note that all forum posts prior to v38 are considered as Closed. If
        there were postings that people did not respond to, please post a new
        forum posting by copying over the pertinent information to the new post.

### New data

Following are new data that have been added for data collection in this release.

*   **Unicode Symbols**
    \[[CLDR-13705](https://unicode-org.atlassian.net/browse/CLDR-13705)\]
    *   There are ~100 new symbols under Characters\\Symbols2.
    *   💡 Translation Tips for Unicode symbols:
        *   To find established names in your language, use common research
            methods or translator applications.
        *   Use Wikipedia documentations of Unicode symbols when available.
        *   Research the symbol using the symbol (e.g. ‰) or the name (per
            mille) or the Unicode code point (U+2030 ).
        *   You can copy/paste the symbols shown in the Code column in the
            survey tool into your preferred search method.
        *   On Windows, you can convert the symbol to the Unicode code point by
            selecting the symbol in an editor application (e.g. Word) with
            Alt+x.
        *   Search examples: [Wikipedia per
            mille](https://en.wikipedia.org/wiki/Per_mille) or [Google search
            for ‰](https://www.google.com/search?q=%E2%80%B0) or [Bing search
            for
            U+2030](https://www.bing.com/search?q=u%2B2030&cvid=62dd90b5dfe441c98c335fcd36b83fb9&FORM=ANNTA9&PC=U531)
            or [Wikitonary](https://en.wiktionary.org/wiki/%E2%80%B0).
    *   There are also ~200 additional symbols under the comprehensive coverage
        level if you have the time to contribute additional data.
*   **Emoji 13.1**
    \[[CLDR-13779](https://unicode-org.atlassian.net/browse/CLDR-13779)\]
*   **Compact decimals and Units.** A few new data are also requested in compact
    decimal and units.
*   **New CLDR target languages**
    *   *Basic Level:* Dogri, Sanskrit
    *   *Moderate Level:* Norwegian Nynorsk
*   **Inflections.**
    \[[CLDR-13756](https://unicode-org.atlassian.net/browse/CLDR-13756)\] For a
    limited number of locales and units of measurement, we are adding support
    for inflections for noun case and gender. The following is the limited set
    of locales in v38:

    Grammatical Feature

    Locales

    Case

    pl, ru, de, hi

    Gender

    pl, ru, de, nb, da, sv, hi, es, fr, it, nl, pt

    Not all units will have the extra information: only a subset of about 75.
    For these units, many (but not all) forms have “seed” data, marked as
    provisional. *Before starting, be sure to read* [Grammatical
    Inflection](grammatical-inflection.md) *for instructions if your locale is
    one of the above.*

## Translation quality

Following are areas where we have seen data quality issues or those that need
your attention more carefully.

*   Avoiding voting for English
    *   For items that do not work in your language, please don't simply use
        English. Find a solution that works for your language. For example, if
        your language doesn't have a concept of "quarters", use a translation
        that describes the concept "three-month period" rather than
        “quarter-of-a-year”.
*   Dealing with “**Same as code**” errors:
    *   Since v37, if you voted for the Code, a Same as Code error will raise.
    *   When translating codes for items such as languages, regions, scripts,
        and keys, it is normally an error to select the code itself as the
        translated name (such as “en” as the translated name for code “en”
        English), except for some specific cases including certain script codes
        (for example, code “Thai” is also the name for script Thai in several
        languages).
    *   If the error appears under Typography, you can ignore.
        \[[CLDR-13552](https://unicode-org.atlassian.net/browse/CLDR-13552)\]
*   Bidi example limitations
    \[[CLDR-10674\]](https://unicode-org.atlassian.net/browse/CLDR-10674). If
    you are working with a bi-directional languages, be aware of the
    Right-to-Left and Neutral context. Survey Tool only shows examples with a
    strong RL context, and we have been issues where vetters removed the ALM
    bidi marks or modify the patterns without considering the neutral context.
    Please be cautious of changing the bi-di formatting data.
*   Handling Display name [menu variants](displaynames/language-names/index.md)

## Translation guides: updated sections

If you are new to CLDR, use the [@Getting Started](getting-started/index.md)
topics to get started and review the left Table of Contents under Translation
Guides.

Major updates have been done to the following list of translation guides for
clarity:

*   [Date and time patterns](date-time-1/date-time-patterns/index.md)
*   [Date and time names](date-time-1/date-time-names/index.md)
*   [Number and currency patterns](numbers-currency/number-patterns/index.md)

Two new sections are provided for guidance with units of measurement.

*   [Compound Units](units-1/units.md) (for all locales translating units, not
    just the limited locales with inflections)
*   [Grammatical Inflection](grammatical-inflection.md) (only needed for the
    limited locales listed above under **Inflections**)

## Known Issues

Please review this list before getting started to avoid creating duplicate
tickets. This list will be updated as fixes are made available in Survey Tool
Production. If you hit a problem, please [file a
ticket](http://unicode.org/cldr/trac/newticket).

**Updated on 2020-06-04**

1.  **Same name collision error.** If two items differ only by upper/lower case
    or punctuation, it still counts as a collision. However, currently, only one
    of them is flagged as an error. \[CLDR-11274\]
2.  **Images for the plain symbols.** Non-emoji such as
    [€](https://cldr-smoke.unicode.org/smoketest/v#/fr/Symbols2/47925556fd2904b5),
    √, », ¹, §, ... do not have images in the info pane.
    *   **Workaround:** Look at the Code column; unlike the new emoji, your
        browser should display them there.
3.  **English changed.** This warning is not working correctly. It is supposed
    to show that there was a change in English after the last change in your
    native language. It is for a possible semantic change that you want to
    account for in your language.
    \[[CLDR-13853](https://unicode-org.atlassian.net/browse/CLDR-13853)\]
    1.  **Workaround.** The most important cases to look at are:
    2.  [person with
        beard](https://st.unicode.org/cldr-apps/v#/USER/People/20a49c6ad428d880)
        — name and keywords changed because there are now 3 genders.
    3.  [knocked-out
        face](https://st.unicode.org/cldr-apps/v#/USER/Smileys/5b3aeb99ddb7f6aa)
        — name and keywords changed because there is a new face with spiral eyes
        for dizzy, and this face is more a [dead
        ](https://www.google.com/search?q=cartoon+face+dead&tbm=isch)or
        [unconscious](https://www.google.com/search?q=cartoon+face+unconscious&tbm=isch)
        cartoon face. The semantics may be different in your language, or you
        can use a purely descriptive term like "face with X eyes".

**Older known issues**

1.  Brackets "\[ \]" under Alphabetic information are used to group the
    alphabetic information and they are not part of the data.
    \[[CLDR-13180](https://unicode-org.atlassian.net/browse/CLDR-13180)\]
    *   **Workaround:** Please ignore the \[ \] in the Alphabetic information
        and do not try to update the data to exclude the \[ \].

## Resolved Issues

The following list of previously listed on the Known Issues have now been
resolved:

**Updated on 2020-06-04**

1.  **Miscounted Provisional items.** The Dashboard is omitting many provisional
    items on the units pages.
    [CLDR-13833](https://unicode-org.atlassian.net/browse/CLDR-13833)
    *   **Workaround:** Review each of the Unit pages, looking for the items
        without ✔ marks, that is: ✘, ✘, or ✘ signs.

**Older resolved issues**

1.  *<none so far>*
