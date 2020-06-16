# Survey Tool: Vetting stage

## Dashboard

Once you have finished entering data, you will need to review the items for
accuracy. To assist with this, use the Survey Tool's Dashboard, accessible
through the link in the sidebar.

The Dashboard will show you a list of data items with warnings of different
kinds. Some will require action and some may be false positives. The idea here
is that you should work the Dashboard down to show zero items.

### Dashboard Sections

The Dashboard is divided in these sections. If a section is not visible for you,
that means you have no items in that section:

*   **Error**: The currently winning value has caused an error in validation
    that will have to be resolved before release. (High priority.)
    *   Fix the error. In some cases there is a conflict among items, and you'll
        need to fix the conflicting item, not the one showing the error.
*   **Losing**: Your vote is losing against the other vetters’ vote.
    *   Can you live with the winning value? If so, change your vote.
    *   Otherwise, use the forum to alert the other vetters and reach consensus.
*   **Disputed**: Your vote is winning, but other vetters voted differently.
    *   Use the forum to help reach consensus if possible.
*   **Warning**: The winning value has something unexpected in it, perhaps a
    character that’s not normally used in your language.
    *   Please review. If it’s an unwarranted warning, you can hide it.
*   **English Changed**: The English value changed from last version, but the
    winning translation in your language remained the same.
    *   Does the translation need to be updated? If not, you can hide the
        warning.
*   **New**: The winning localized value is different from last year.
    (Informational.)
*   **Missing**: We have no localized value for these values.
    *   Please provide them. (High priority.)
*   **Provisional**: We have a value, but not enough votes to support it and
    include them in the release.
    *   Add your vote if you haven’t already and alert other vetters through the
        forum to support if you have already voted.

### Fixing Entries

Each entry has the following:

*   A blue field which links to the relevant value in the Survey Tool. The link
    will open in a new window.
*   English value
*   previous CLDR version’s value
*   currently winning value

To the right of this information, there are 3-4 action buttons:

*   **Fix** (the pen): This will bring up window where you can change or edit
    your vote. You can fix an entry right here, or click the blue field to the
    left to fix it in its ordinary place in the Survey Tool.
*   **Hide** (crossed over eye): If the warning is a false positive, you can
    hide it from view. Note that this will not make it disappear, just hide it
    from view. Click on the other eye button on top of the section to unhide
    hidden lines. The count on each section will show how many items are showing
    versus the total.
*   **Forum** (the talk bubble): Enter a forum post to be seen by other
    linguists regarding this specific item. This is useful if your item is
    losing and you want to try to convince the other vetters to change their
    vote.
*   **Info** (i-symbol): Warnings and errors will have additional info here as
    to why something was flagged with a warning, this will help you resolve the
    warning.

### Clearing Items

There are two ways to clear items from the list:

1.  The preferred way is to fix them (such as adding a translation for a missing
    item)
2.  The other is to hide them (such as when the English has changed but the
    translation doesn’t need to change). Only hide an item if it really is a
    false positive, not because you gave up on fixing it.

The following are legacy tools to review votes, but the Priority Items tool is
deprecated in favor of the Dashboard. This information is presented here for
reference.

**Review:** [Priority
Items](http://st.unicode.org/cldr-apps/survey?_=cy&x=r_vetting)
|[Date/Time](http://st.unicode.org/cldr-apps/survey?_=cy&x=r_datetime&calendar=gregorian)
| [Zones](http://st.unicode.org/cldr-apps/survey?_=cy&x=r_zones) |
[Numbers](http://st.unicode.org/cldr-apps/survey?_=cy&x=r_compact)

You can also see a video walkthrough of the review sections on
[Walkthrough](../../../index/survey-tool/walkthrough/index.md).

---

The rest of this page discusses how to do the Priority Items. Once you have done
the Priority Items, [Review reports](../review-formats/index.md).

Remember to periodically look at the Forum for your locale.

1.  On any page in your locale, near the top there is a link
    "![image](http://unicode.org/cldr/apps/chat.png)==[Forum](http://unicode.org/cldr/apps/survey?forum=de)==".
2.  Click on it and go through the comments.
3.  If there is a request to change values or votes, either respond on the Forum
    with why you disagree, or change your vote.
4.  Some issues may be general, such as the capitalization of language names.
    *In the vetting period, please try to resolve these in accordance with the
    other items in the locale for consistency; leave anything else for the next
    release.*

If you have time after doing the above, it is useful to review items for
consistency.

1.  Go to each Section in the survey tool
2.  Check that related items (like singular/plural) don't have spurious
    differences
3.  Check that closely related items have consistent translations.

## Priority Items

Open your locale, such as <http://unicode.org/cldr/apps/survey?_=de>, and log
in.

Click on Priority Items. After it loads you’ll see a view over all the possible
issues for your locale. Once it loads you can leave it open while you work
through the items, so you won’t have to reload very often.

**Warning:**

*   *Make sure your coverage level is set correctly: typically **modern\***.
    Otherwise you won't see all the issues for your language.*
*   *After you change your coverage, or to see the new status of changed items,
    you must click the Refresh Values button.*

In the Priority view, you can see the important issues for your language. At the
top is a summary for each kind of issue, looking something like the following:

Summary

**For instructions, see [Priority
Items](http://cldr.unicode.org/translation/vetting-view).**

**Count Abbr. Description 0 ☐ Error\* The Survey Tool detected an error in the
winning value. 411 ☐ Losing\* The value that your organization chose (overall)
is either not the winning value, or doesn't have enough votes to be approved. 4
☐ Disputed\* There is a dispute between other organizations that needs your help
in resolving to the best value. 0 ☐ Warning\* The Survey Tool detected a warning
about the winning value. 265 ☐ Unsync’d\* The English value changed at some
point in CLDR, but the corresponding value for your language didn’t. 130 ☐ New\*
The winning value was altered from the last-released CLDR value. 36 ☐ Missing\*
Your current coverage level requires the item to be present, but it is
missing.**

It is followed by a list of issues, categorized by type.

## How to Proceed

You will click on each of the check-boxes above that that don't have a count of
zero, and follow the instructions below.

If you have any questions, please contact your organization's CLDR Technical
Committee member, or email
[surveytool@unicode.org](mailto:surveytool@unicode.org).

### Goals

#### Data Submission Phase

1.  Concentrate on fixing the Missing items first, since you can't fix them in
    the Vetting phase.
2.  You can then work on Error, Warning and Unsync'ed items.

#### Vetting Phase

1.  Review the New items and Unsync'ed items to make sure that they make sense.
2.  Work on getting of the Error, Losing, Disputed counts down to zero.
    1.  The Warning and Unsync'd counts might not be zero after you are done.
    2.  The count for New items is informative, it just represents the changes
        in this release. You do *not* have to try to reduce it.

*Go through the summary list, clicking the checkbox (☑) to show the issues of
type you're working on.* You can click several at once if you find that easier.
That will then expose the issues of that type below the summary.

### How to Handle

Handle each of the types of issues as follows:

### Missing\* (only applicable during Data Submission Phase)

1.  Add the missing value, or vote for an "inherited" value (in a special color)
2.  Unless there is some other error, you can't change these during the vetting
    phase, so make sure to get them done early!

### Error\*, Warning\*

1.  Go to the item (by clicking the **Fix?** link).
2.  Error items will be removed from the release, so they are a priority in the
    vetting phase.
3.  Review the warning items; most of them need fixing but not all. See [Fixing
    Errors and
    Warnings](http://cldr.unicode.org/translation/getting-started/errors-and-warnings)

### Losing\*, Disputed\*

1.  See if the winning value is ok. If so, change your vote to it, and go to the
    next item.
2.  Otherwise, post a message to the
    [Forum](http://st.unicode.org/smoketest/survey?forum=af).
    1.  State why you think the item should be changed.
    2.  If there are a number of items that have the same characteristic (such
        as the wrong capitalization), you can make that case in a single posting
        rather than multiple ones.

### New\*

1.  Quickly scan over these values.
2.  If the values are ok, then you don't need to do anything. If not, follow the
    instructions above.

### Unsync’d\*

For the Unsync'd issues, the older English value is listed below the new one,
and in Red. (See below). These often indicate that a change needs to be made in
your language. For example, in the tables below

1.  The English value was changed so that the locale "zh-Hans" shows up as
    "Chinese (Simplified)" rather than the somewhat redundant "Chinese
    (Simplified Han)". The corresponding change should be made to French.
2.  Similarly, the English was simplified for "Unknown Script"; that change
    should also be made to French.
3.  On the other hand, the change for that particular currency name in English
    is specific to English, and doesn't need to be reflected in French.

**Section: names — *Page: script***

No. Code English CLDR 1.9.1 Winning 2.0 Fix? 358 Hans Simplified
Simplified Han idéogrammes han simplifiés =
[Unsync’d\*](http://unicode.org/cldr/apps/survey?_=fr&xpath=%2F%2Fldml%2FlocaleDisplayNames%2Fscripts%2Fscript%5B%40type%3D%22Hans%22%5D)
359 Hant Traditional
Traditional Han idéogrammes han traditionnels =
[Unsync’d\*](http://unicode.org/cldr/apps/survey?_=fr&xpath=%2F%2Fldml%2FlocaleDisplayNames%2Fscripts%2Fscript%5B%40type%3D%22Hant%22%5D)
360 Zzzz Unknown Script
Unknown or Invalid Script écriture inconnue ou non valide =
[Unsync’d\*](http://unicode.org/cldr/apps/survey?_=fr&xpath=%2F%2Fldml%2FlocaleDisplayNames%2Fscripts%2Fscript%5B%40type%3D%22Zzzz%22%5D)

**Section: names — *Subsection: currency***

No. Code English CLDR 1.9.1 Winning 2.0 Fix? ... ... ... ... ... ... 29 BIF:name
Burundian Franc
Burundi Franc franc burundais =
[Unsync’d\*](http://unicode.org/cldr/apps/survey?_=fr&xpath=%2F%2Fldml%2Fnumbers%2Fcurrencies%2Fcurrency%5B%40type%3D%22BIF%22%5D%2FdisplayName)

### ### Review

### Once you have completed your items, review the Priority Items again to see
that all the changes are as expected.
