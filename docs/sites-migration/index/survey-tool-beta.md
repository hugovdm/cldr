# Survey Tool Beta

April 15, 2013 — The [Unicode CLDR](http://cldr.unicode.org/) Survey Tool is
open for beta testing today. CLDR provides key building blocks for software to
support the world's languages, with the largest and most extensive standard
repository of locale data available. The survey tool is an online tool used by
organizations and individuals to contribute data to this repository, and to vote
on alternative contributions.

The survey tool has again undergone substantial revision, with dramatic
improvements in usability. We would appreciate people trying out the tool so
that we can identify any remaining problems before we start data submission for
CLDR 24 on April 24th.

For more information, including how to login, try it out, and supply feedback,
see [Survey Tool Beta](survey-tool-beta.md).

---

**## Access**

    ***[Production Survey Tool](http://st.unicode.org/cldr-apps/survey). If you
    have an existing survey tool account, you can go to the production tool at
    [Production Survey Tool](http://st.unicode.org/cldr-apps/survey).***

    ***[Smoke-Test Survey
    Tool](http://st.unicode.org/smoketest/createAndLogin.jsp?vap=isdithOif5). If
    you don’t have an account, you can still try out the survey tool using the
    Smoke Test version. It will create a test account automatically.***

**So that you can try out the tool as you wish, none of the data you enter during beta is saved.**

**The Smoke Test tool may be restarted at any time, because it used for development. If you get disconnected when this happens, then refresh your browser: all of your changes should be saved.**

**# Feedback**

**You can either file a ticket describing the problem you found ([newticket](http://unicode.org/cldr/trac/newticket)), or join the cldr users group for general discussion of the survey tool ([cldr-users](http://www.unicode.org/consortium/distlist-cldr-users.html)).**

**Please include the URL to the page where you found the error. For issues with the UI, it often helps to provide one or more screen shots providing context. For a ticket, these can be included by clicking "I have files to attach to this ticket".**

# ****Guide****

If you haven’t used the survey tool before, you may want to take a quick look
at:

    *<http://cldr.unicode.org/index/survey-tool/guide>*

    *<http://cldr.unicode.org/index/survey-tool/walkthrough>*

This documentation should be updated in the next few days for some of the
changes in UI.

# How you can help

Visit and randomly vote and enter changes.

    *Pick your favorite locale*

    *Click on the “General Info” button to choose a different subpage*

    *Visit different Sections of the locale (Code Lists, etc), and different
    pages in the Section.*

        *Vote for different choices (including Proposed, Others, Abstain)**

        *Change a value (by clicking on the value and editing it in place)**

        *Try zooming on different columns (clicking on the following cells)**

            **St (status, eg error/alert)***

            **Draft (the approval status)***

            **Voted (the voting status)***

            **Proposed / Others (particular values)***

            **(Clicking on Code shows some internals, not really user-focused
            item)***

        *Reset your Coverage Level (at the top). (This changes how many items
        show).**

    Verify that data was accepted, or is rejected (appropriately) because of an
    error.*

    Report any new issues at <http://unicode.org/cldr/trac/newticket>. (Skip
    those below).*

# Known issues

Please read these over so you know what to skip. Visit this page again often to
see any updated known issues.

1.  Use Firefox/Safari/Chrome/Internet Explorer 8+
2.  Some locales, such as English (en), are read-only.
3.  Other items may be added to this list during the beta period
4.  Other people’s votes may not show up immediately.
5.  Keyboard navigation is not working properly.
6.  **Do not click** on the navigation menus while a page is still loading. This
    is a known issue that will cause a hang.

### What changed?

1.  Navigate between sections in a locale without reloading
2.  Editing (or re-editing) items by clicking on text in-place.
3.  Scrolling should be faster
4.  Less cluttered page layout.
5.  After initial page load, changing sections and voting should be faster.
