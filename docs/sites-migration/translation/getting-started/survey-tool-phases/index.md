# Survey Tool stages

Data collection in the Survey tool has 4 stages:

[TOC]

1.  Shakedown
2.  General submission
3.  Vetting
4.  Resolution

### Full vs. Limited Submission

There are two types of releases: full, and limited-submission.

*   Full-submission:
    *   Typically with the even versions (e.g. Version 36).
    *   All languages and data areas are open for contributions.
*   Limited-submission
    *   Typically, with odd versions (e.g. version 37).
    *   Selected data points are open for all languages; the voting options will
        be grayed out for those data points that are not in scope.
    *   Selected languages are open for all data points.
    *   In the Survey Tool, you will see the rows where you can add your vote
    *   What you can do depends on your locale:
        *   Newly targeted locales: proceed with Submission (General).
        *   Other targeted locales: proceed with Submission (General), but start
            with the
            [Dashboard](http://cldr.unicode.org/translation/getting-started/guide#TOC-Dashboard)
            step and focus on Errors\*, Missing†, and English Changed.
        *   Other locales: go to the
            [Dashboard](http://cldr.unicode.org/translation/getting-started/guide#TOC-Dashboard)
            and deal with any Errors\*.

## Survey Tool phase: Shakedown

*Make sure your coverage level is set correctly at the top of the page.*
Shakedown is on an invitation basis. If you have not received an invitation to
participate in shakedown, your participation is discouraged.
You should know in this stage:

*   The survey tool is **live and all data that you enter will be saved and
    used**.
*   You can start work
*   Expect a churn: there may be additional Tooling fixes and Data additions
    during this period.
*   Tool may be taken down for updates more frequently during general submission
*   You are expected to look for issues with the Survey tool and any other
    problems you encounter as a vetter. Please [file a
    ticket](http://unicode.org/cldr/trac/newticket).

## Survey Tool phase: General Submission

*Make sure your coverage level is set correctly at the top of the page.*

For new locales or ones where the goal is to increase the level, it is best to
proceed page-by-page starting with the **Core Data** section. At the top of each
page you can see the number of items open on the page. Then scan down the page
to see all the places where you need to vote (including adding items). Some

Then please focus on the
[Dashboard](http://cldr.unicode.org/translation/getting-started/guide#TOC-Dashboard)
view, first getting all **Missing**† items entered, and then addressing any
remaining **Errors**\* and reviewing the **English Changed** (fixing your
language if necessary).

> \* Note that if the committee finds systematic errors in data, new tests can
> be added during the submission period, resulting in new **Errors.**

> † Among the ***Missing*** are are new items for translation. (On the
> [Dashboard](http://cldr.unicode.org/translation/getting-started/guide#TOC-Dashboard),
> **New** means winning values that have changed since the last release.)

If you are working in a sub-locales (such as fr_CA), coordinate with others on
the Forum to work on each section after it is are done in the main locale (fr).
That way you avoid additional work and gratuitous differences. See voting for
inheritance vs. hard votes in [Survey Tool
guide](http://cldr.unicode.org/index/survey-tool/guide#TOC-Inheritance).

## Survey Tool phase: Vetting

All contributors are encourage to move their focus to the
[Dashboard](http://cldr.unicode.org/translation/getting-started/guide#TOC-Dashboard)
view, and:

1.  Resolve all of the Errors.
2.  Review all items in the
    [Forums](http://cldr.unicode.org/translation/getting-started/guide#TOC-Forum)
    that don't show consensus yet, and try to resolve them by posting relevant
    information.
3.  Consider other's opinions, by reviewing the **Disputed** and the **Losing**.
    See guidelines for handling
    [Disputed](http://cldr.unicode.org/translation/getting-started/guide#TOC-Disputed)
    and
    [Losing](http://cldr.unicode.org/translation/getting-started/guide#TOC-Losing).
4.  Review the items that are Flagged for TC and provide comments if you have
    information that should be considered.

> To see the Flagged items, go to the **Gear** dropdown, under **Forum** see
> **Flagged items**:

![image](gear.PNG)

## Resolution (Closed to vetters)

The vetting is done, and further work is being done by the CLDR committee to
resolve problems. You should periodically take a couple of minutes to check your
[Forums](http://cldr.unicode.org/index/survey-tool/guide#TOC-Forum) to see if
there are any questions about language-specific items that came up.
