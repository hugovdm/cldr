# Statement of Work for CLDR Contract Engineers

[TOC]

This document provides some background for the [CLDR Software
Engineer](index.md) tasks. The focus is on performance and UI improvements to
the CLDR Survey Tool (ST).

The work can be split among more than one person. For example, an engineer with
JS skills could work on the front-end, coordinating with an engineer with Java
skills working on the backend. Relatively independently from that area, a
different person with expertise in performance, Java, and SQL works on the
performance. It is expected that people would work remotely, with their own
equipment; they should however be located in an accessible timezone (between
California Time and Central European Time).

The goals for this work are listed below under Performance Improvement Goals and
UI Improvement Goals. Payment will be based on completion of milestones.

# Overview

So that there is a basic understanding of what is being worked on, the following
provides an overview of the CLDR Survey Tool. Its basic purpose is to provide a
UI for people to add and fix translations of locale data. This data is stored in
a database, and is converted to XML format for release.

People representing many different organizations may be working on the same
locale at the same time, and the results are resolved on the basis of votes
apportioned to the translators (called “vetters” in CLDR). The translations may
be simple names, or they may be more complicated patterns (such as a pattern
specifying a date format).

As each item is typed it, a series of tests are run. The status of an updated
value (whether it has an error, warning, or neither) is asynchronous — the user
doesn’t have to wait on the status before going to the next item on that page.

The ST doesn’t always present the same view to different users; users can pick a
“coverage level” that they want to work on. (The core locales are done at at
least a “modern” level; organizations can choose default levels on a per-locale
basis.) Users may also have differing numbers of votes.

To try out the Survey Tool and look at the user guide, see
[survey-tool](../survey-tool/index.md). Note that unless we are in a data
submission phase, the ST is in Read-only mode, and some of the functionality is
suppressed.

The help text for a given field typically points to a page that explains more
about a particular field or a particular type of error, such as
[timezones](http://cldr.unicode.org/translation/timezones), or other pages on
<http://cldr.unicode.org/translation>. The Survey tool also has a forum for
translators. The forum is used to leave comments / suggestions for other
translators, so that disputes on particular items can be resolved.

# Internals

The workhorse of the CLDR tooling is a Java class called
[CLDRFile](https://unicode.org/~srloomis/cldr-doc-snapshot/doc/org/unicode/cldr/util/CLDRFile.html).
Logically, it is a set of <key, value> pairs, where the key is an XML path
containing a code (like "DE" for Germany), and the value is a translation of
that code (like "Allemagne"). (For end-users, the path is sometimes called a
“field”.)

The ST architecture uses a frontend written in Javascript and a backend written
in Java. Data is stored in a MySQL database.

Every time someone adds or updates a translation in the ST, a series of data
tests are run. These check for the consistency of the data; otherwise it is too
easy for translators to make mistakes. We add to those tests over time, as we
discover common problems that translators have. Some of these tests are
relatively independent, such as the CheckForExemplars, which makes sure that a
translation doesn't contain unexpected characters (such as a Latin character O
instead of a Greek Omicron in the name of a country in the Greek locale). Some
are dependent on other items, such as checking that no distinct countries have
the same name. The tests can signal an error to users, or just a warning.

Take an XML path, such as the following

//ldml/numbers/decimalFormats\[@numberSystem="latn"\]/decimalFormatLength/decimalFormat\[@type="standard"\]/pattern\[@type="standard"\])

From it, we look up:

    a [PathHeader](../../development/updating-dtds/index.md), such as [<Numbers,
    Number Formatting Patterns, Standard Patterns,
    standard-decimal>](http://st.unicode.org/cldr-apps/v#/de/Number_Formatting_Patterns/24a93b3d14ba17b2).
    This is used to decide the section and page where the field appears in the
    ST, the subheader and “code” on that page. It also determines the ordering
    of all of those.

    an
    [XPathParts](https://unicode.org/~srloomis/cldr-doc-snapshot/doc/org/unicode/cldr/util/XPathParts.html),
    which has the parsed out the elements and attributes. This can be frozen
    (immutable) or regular (mutable).

    a [PathDescription](../../development/updating-dtds/index.md), with a
    user-visible description and pointer to a translation guide

    a [Coverage](../../development/updating-dtds/index.md) level (this is the
    only one that depends on the locale).

    a [Placeholders](../../development/updating-dtds/index.md) description, with
    a short description of each placeholder and an example.

The above are all driven by data files. In addition, the tests also have to map
from paths to different conditions to test for, and to groups of related paths
(for testing collisions, logical groups, etc). The examples shown to users in
hover tips — important especially for complex cases such as showing how pieces
are substituted into patterns — also have to branch depending on the paths. See
[an example](http://st.unicode.org/cldr-apps/v#/de/Gregorian/562f98c4c6b2e321)
of these hover tips, hovering over the English and native patterns.

We make heavy use of regex, including a lot of code that tries multiple regex
patterns against a path, and takes the first match. We have a mechanism called
[RegexLookup](https://unicode.org/~srloomis/cldr-doc-snapshot/doc/org/unicode/cldr/util/RegexLookup.html)
that is used to handle much of this, typically driven data files. Much of the
code in tests and for examples predates this, and has simpler tests for
different types of paths based on containment or
[XPathParts](https://unicode.org/~srloomis/cldr-doc-snapshot/doc/org/unicode/cldr/util/XPathParts.html)
checking.

Here are some possible areas for investigation to meet the performance goals
listed below.

    Thread-contention. While the goal is to be thread-safe, of course, there are
    probably areas where the threading is not optimal; where we block on items
    at too high a level, thus slowing down performance. An analysis is needed to
    determine whether that is happening and straighten it out if so.

    Test performance. The tests are a fertile field for [improving
    performance](https://unicode.org/cldr/trac/ticket/6911). For example, the
    tests build up caches as they work. Many different fields go into displaying
    a date, so when a date is checked, we end up building up ICU objects out of
    all the components needed for number and date formats. We don't currently
    keep track of which items affect the validity of which caches, so when a
    translation changes, all of these caches effectively get flushed, and then
    rebuilt. We suspect this is a prime target for improvement.

    Regex performance.
    [RegexLookup](https://unicode.org/~srloomis/cldr-doc-snapshot/doc/org/unicode/cldr/util/RegexLookup.html)
    is (a) not always used, and (b) may need some performance work.

    Path parsing. Revamp the code that calls the
    [XPathParts](https://unicode.org/~srloomis/cldr-doc-snapshot/doc/org/unicode/cldr/util/XPathParts.html)
    constructor and replace the factory methods for frozen or unfrozen copies.
    We can probably do a got part of this with refactoring via IDE.

    Database. The ST stores the CLDR files in a MySQL database. We should
    examine this to make sure that the saving is fully asynchronous, and that
    data storage is optimized.

The code is available as described on [CLDR
Releases/Downloads](../downloads/index.md), under
"[Advanced-SVN-Access](http://cldr.unicode.org/index/downloads#TOC-Advanced-SVN-Access)".

# Performance Improvement Goals

The goals are to improve the performance and reliability so that with up to 40
vetters working concurrently, people see the expected results:

Performance is dependent on many factors such as number of users on the system,
specific field and validations behind, server environment, etc.

About the performance areas and expectations below:

    The areas are identified either as most frequently encountering performance
    issues OR actions that are most frequently performed by Survey Tool users.

    The test locale (Czech = cs) is used as an example for a locale because of
    number of fields that get exposed is more comprehensive than others. That
    can be changed to a similar locale if a different one is easier to work
    with.

    User settings for the following performance areas are for Vetter, with
    Modern coverage.

Test fields are the following:

    [Formats - Standard - Date
    Formats](http://st.unicode.org/cldr-apps/v#/cs/Gregorian/562f98c4c6b2e321)

    <http://st.unicode.org/cldr-apps/v#/cs/MassWeight/3f252d4fc81cc4c7>

    <http://st.unicode.org/cldr-apps/v#/cs/Languages_E_J/225e1eb2402007a>

    <http://st.unicode.org/cldr-apps/v#/cs/C_MAfrica/>

    <http://st.unicode.org/cldr-apps/v#/cs/People/>

    <http://st.unicode.org/cldr-apps/v#prevforum/cs//>

The chief problem is that the performance degrades under higher load.

Performance area

Expected

#1

Vote Submit action on single item as vetter (After Click + to Add), the action:
Check green check mark (or return)

0.5 sec

#2

Voting on multiple items on a page in rapid succession (after ~5 clicks).
\[Current tool loses track and doesn’t respond.\]

0.5 sec / item

#3

Single item load on page. Click on Winning field and the item is fully populated
in the right pane

0.2 sec

#4

Page load using test locale for each of the test fields

1 sec

#5

Page load Dashboard

3 sec

#6

Page load of Forum (old)

1 sec

## Performance Milestones

    Milestone #1: Create scaffolding so that simultaneous input from multiple
    vetters can be simulated by a tool that interacts with the survey tool,
    using the common actions specified in the goals.

    Milestone #2: Complete an analysis of the hotspots in loaded operation, and
    create a document of recommend tasks to address them (in priority order,
    based on the best ROI).

        The CLDR committee will then settle on a set of tasks to address the
        performance issues based on the recommendations

    Milestones #3… Each of the tasks in 2a will be a separate milestone

        There also may be iterations: after fixing performance problem #1,
        re-run the tests to identify the hotspots to make sure that the tasks
        are still relevant. New tasks may need to be added, or they may need
        prioritization.

# UI Improvement Goals

The goals are to improve user experience of CLDR data contributors, and help
administer/monitor contribution activities. Following is a list of known issues
that will be prioritized. Some implementation will require investigation on the
current issue, and spec on the desired behavior.

TRAC Query:
[Front/Backend](https://unicode.org/cldr/trac/query?owner=backend&owner=frontend&status=accepted&status=design&status=new&status=reviewfeedback&group=owner&col=id&col=summary&col=status&col=owner&col=type&col=priority&col=milestone&col=component&col=reporter&report=89&order=priority)

## Description of Services

    During a production phase when contributors are actively working in the
    survey tool, investigate and fix incoming tickets in order of priority
    determined by the CLDR TC triage.

    Address existing bugs in order of priority determined by the CLDR TCs. The
    existing tickets are organized into areas of priority in the Areas and
    Priorities section.

    When working through the Survey Tool code, review for improvements to the
    current design and bring recommendation to the CLDR TC.

    Bring design solutions to CLDR TC member and find best possible solutions.

    Attend CLDR TC meetings (as invited) to participate in triages or discuss
    designs.

    Create documentation as needed (or requested by the CLDR TCs) that would
    explain either the existing design or new design solutions.

    Resolve any blocking issues in the production environment not limited to the
    survey tool code.

## Areas and Priorities

Following are list of areas in order of priority with some examples of existing
bugs and current pain points. Listed in each area are examples of known tickets,
for the most current set, use TRAC and the keywords provided for each area.

    Browser compatibility. TRAC keyword “BrowserCompat”
    The following 4 browsers need to be supported: Chrome, Firefox, Safari, Edge

        Updated browsers (no older than 6 months)

Example tickets: [#10396](http://unicode.org/cldr/trac/ticket/10396) ST: on Edge
or IE copy "English" or "Winning" doesn't work

    High priority bugs. TRAC keyword “STP1”
    Example tickets:

        [#10323](http://unicode.org/cldr/trac/ticket/10323): Filipino forum does
        not load

        [#10521](http://unicode.org/cldr/trac/ticket/10521): voting page issues
        found in pt_PT

        [#9675](https://unicode.org/cldr/trac/ticket/9675): "voting
        participation" hard to get to, and crashes

    Dashboard UI. TRAC keyword “Dashboard”
    The Dashboard is used throughout contribution phases, but most importantly
    during vetting phase, and users need to be able work quickly to prioritize
    and work through the items.
    Example tickets:

        [#10528](https://unicode.org/cldr/trac/ticket/10528): Assamese Error
        shown in Dashboard does not show in the data point

        [#10866](https://unicode.org/cldr/trac/ticket/10866): Dashboard
        suggestion for New

        [#10692](https://unicode.org/cldr/trac/ticket/10692): Dashboard losing
        count message does not match code

    Voting experience. TRAC keyword “Voting”
    Voting is one of the fundamental actions that vetters perform. UI design is
    a big factor to vetters submitting correct data.
    Example tickets:

        #[10324](https://unicode.org/cldr/trac/ticket/10324): some sub-locales
        cannot add suggestion when there is approved data

        [#10485](https://unicode.org/cldr/trac/ticket/10485) Import:
        Automatically Import Vote information from previous cycle

        Make Tips and Examples shown to the vetters follow intended spec and
        easy to use

    Inheritance. TRAC keyword: “Inheritance”
    Inheritance is a hierarchy vertically and horizontally that determines the
    base data set when there is no specific data available for the locale.
    Inheritance impacts sub locales, but main locales also are impacted
    vertically up to Root and horizontally as well. Inheritance is important to
    vetters, because they should be using the inherited value to reduce data
    repetition as well as consistency when it’s deemed correct for the locale.
    Example tickets:

        [#10466](https://unicode.org/cldr/trac/ticket/10466): Inheritance value
        is not available

        [#10574](https://unicode.org/cldr/trac/ticket/10574): always be able to
        explicitly select the “inherited” value

        [#8722](https://unicode.org/cldr/trac/ticket/8722): consistent colors
        for aliases

        [#9554](https://unicode.org/cldr/trac/ticket/9554): inherited nits

    Architectural Cleanup: : TRAC keyword: “STARCH”

        Front/Back end has developed without a [clean API
        separation](https://unicode.org/cldr/trac/ticket/7339).(#7339)

        Change the back-end to present a clean and documented API to the
        front-end (REST best practices and separating authentication endpoints
        from other data endpoints) which will enable performance, security, and
        feature development on the [front and back
        end](https://unicode.org/cldr/trac/ticket/5992).(#5992)

    Reporting. TRAC keyword: “Reporting”
    Reporting impacts various UI area where calculations are utilized. For
    examples, the Priority Items, Count of Votes in User views, Calculated error
    counts in Dashboard, etc. Reporting is important for vetters as well as
    administrators to monitor progress and to get the accurate statistics.
    Example tickets:

        [#9584](https://unicode.org/cldr/trac/ticket/9584): "Manager" can't see
        "Priority Items Summary"

        [#10773](https://unicode.org/cldr/trac/ticket/10773): For Errors on the
        Priority items, show comprehensive

    Admin UI: TRAC keyword: “AdminUI”
    Admin UI serves roles such as TC and Manager to manage users and their
    access control in the Survey tool.
    Example tickets:

        UI improvements may be needed (low priority)

    Forum: TRAC keyword: “Forum”
    The Forum is where vetters discuss different aspects about the data itself,
    and come to consensus on controversial items.
    Example tickets:

        #[10935](https://unicode.org/cldr/trac/ticket/10935): Show all old forum
        posts

    ST General: TRAC keyword: “STGEN”
    The survey tool has different areas that are not specific to vetters actions
    for contributing, but that supports communication and navigation within the
    system.
    Example tickets:

        [#7306](https://unicode.org/cldr/trac/ticket/7306): clipping problems in
        tool

        [#9326](https://unicode.org/cldr/trac/ticket/9326): Survey tool left
        nave BCP47 and Supplemental shouldn’t be there

        [10289](http://unicode.org/cldr/trac/ticket/10289): The default coverage
        isn't set right for locales.

# Milestones

Dates can be adjusted to fit invoicing requirements.

Description

Date

#1

Fix browser compbility and blockiating issues that are identified by the CLDR
TC.

March 31, 2018

#2

Finish priority V34 Dsub tickets

April 30, 2018

#3

On-going production support and and working with the CLDR TCs against Priorities
and Areas

May 31, 2018

#4

On-going production support and and working with the CLDR TCs against Priorities
and Areas

June 30, 2018

#5

On-going production support and and working with the CLDR TCs against Priorities
and Areas

July 31, 2018

#6

On-going production support and and working with the CLDR TCs against Priorities
and Areas

August 31, 2018

#7

On-going production support and and working with the CLDR TCs against Priorities
and Areas

Sept 30, 2018

#8

On-going production support and and working with the CLDR TCs against Priorities
and Areas

Oct 31, 2018

#9

On-going production support and and working with the CLDR TCs against Priorities
and Areas

Nov 30, 2018

#10

On-going production support and and working with the CLDR TCs against Priorities
and Areas

Dec 31, 2018
