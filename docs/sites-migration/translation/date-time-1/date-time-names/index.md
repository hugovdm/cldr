# Date/Time Names

## Textual Fields

Certain calendar fields can have both numeric and textual forms. The textual
forms can vary in length, from narrow to full. Some languages also need two
different forms of these textual forms according to whether they used for
formatting, or stand-alone. For more information, see [Date/Time
Patterns](../date-time-patterns/index.md).

For names of eras, months, weekdays, and day periods, use the capitalization
that would be appropriate in the middle of a sentence; the <contextTransforms>
data can specify the capitalization for other contexts. For more information,
see [Capitalization](../../translation-guide-general/capitalization.md).

Many of the sets of names form [Logical
Groups](http://cldr.unicode.org/translation/logical-groups), and you need to
make sure they have the same status or you will get error messages. See [Logical
Groups](http://cldr.unicode.org/translation/logical-groups) for more
information.

### Eras

There are only two values for an era in a Gregorian calendar. The common
presentation of these era names in English are the more religious forms "BC"
(Before Christ) and "AD (Anno Domini)" - from the Latin for "The year of our
Lord". The secular equivalents of these two era names are "BCE" (Before Common
Era) and "CE" (Common Era).

As of CLDR 24 it is now possible for a locale to supply both forms, if both are
used in the locale. You will need to consider whether the religious (BC/AD) form
or the secular (BCE/CE) form is more commonly used in your language, and make
the most common form the default form (code 0, 1). The alternate form, if used,
can be provide under the entries for codes 0-variant, 1-variant. If your locale
does not commonly use an alternate form, do not provide any entries for these.

Other calendars have a different numbers of eras. The names for eras are often
specific to the given calendar, such as the Japanese era names. You only
typically need to translate these if the calendar in question is in common use
in one of the countries that uses your language.

### Months of the Year

This field is one of the months of the year, such as January or February. Note
that the format styles (e.g. MMMM) are intended to be used in patterns *with* a
day-of-month number, while the stand-alone styles (e.g. LLLL) are intended to be
used by themselves or in patterns *without* a day-of-month number. These may
result in different forms in some languages, for example:

*   The stand-alone forms may be in nominative case, while the format forms may
    be in genitive case (as in Finnish, Slavic languages, and some other
    languages); or...
*   The format forms may include a preposition in appropriate form, while the
    stand-alone forms would not (as in Catalan).

The specific values that are used in the format and stand-alone names need to be
closely co-ordinated with the date patterns that will use them. For more
information, see [Synchronizing Date/Time Names and
Patterns](../date-time-patterns/index.md).

In many languages, it is not common to use abbreviated months. The preferred way
to address this is using date/time patterns that never use abbreviated months
MMM or LLL, as shown in [Patterns without abbreviated
months](../date-time-patterns/index.md), whils still supplying abbreviated
months names if possible. If there is no way to supply abbreviated month names,
the full month names may be used for abbreviated months too.

### Days of the Week

This field is one of the days of the week, such as Sunday or Monday. Note that
separate forms can be provided for format style (e.g. EEEE) and stand-alone
style (e.g. cccc); the usage of these two styles must be closely coordinated
with the date patterns that use them. For more information, see [Synchronizing
Date/Time Names and Patterns](../date-time-patterns/index.md).

### Day Periods (AM, PM, etc.)

1.  AM/PM (special handling for locales using 24 hrs)

    *   For locales using the 24 hr as the standard formats, AM/PM data fields
        are difficult to handle. Translations of AM/PM may be more confusing
        than the English strings.
    *   If the English AM/PM strings are more commonly understood, vote for
        inheritance English strings AM/PM. (See related tickets: Hindi
        #[11417](https://unicode-org.atlassian.net/browse/CLDR-11417), German
        #[10789](https://unicode-org.atlassian.net/browse/CLDR-10789))
    *   If translations of AM/PM are commonly understood in your locale, use the
        translations.

**WARNING:**

1.  You will be translating codes that may have no English equivalent.
    *   *For example, Malayalam has the code
        [**morning2**](http://st.unicode.org/cldr-apps/v#/ml/Gregorian/2bcc83b0ea697571),
        which doesn’t exist in English.*
2.  The goal is to make sure that the **wide** format and **wide** stand-alone
    forms are correct.
    *   *The short and narrow forms do not need to be supplied.*
3.  The time span associated with each code is different for different
    languages!
    *   To see what the time-spans are for your language, hover over the value.
    *   You should see something like the following:

    *   It shows the time span (with a 24 hour clock) for the code, and then an
        example (for the format codes).
        *   You can also go to the web page [Day
            Periods](http://www.unicode.org/cldr/charts/latest/supplemental/day_periods.html),
            and look for your language.
        *   For example, for Malayalam, you would go to
            ...[day_periods.html#ml](http://www.unicode.org/cldr/charts/latest/supplemental/day_periods.html#ml)
            , and see that **morning2** is the period that extends from
            **06:00** to **12:00**.
4.  The **format** version will be substituted into a time format, and should
    contain whatever inflections/prepositions are necessary for that.
    *   For example: **Code** **English** **German** **Russian** **Standalone**
        `morning1` morning Morgen утра **Formatting** `morning1` in the morning
        morgens утро ***formatting example*** morning1 10:00 in the morning
        10.00 morgens 10:00 утра
5.  For more about how this works, be sure to read the following section.

---

DayPeriods are spans of time during the day. There are two forms for each
possible period:

*   **stand-alone:** used to label a particular period, such as *"morning".*
*   **format:** used in combination with a specific time, such as *"12 noon"* or
    *"7 in the morning"*.

The codes may also be used—like plural categories—to select messages based on
the day period. For example, an email program might use them to select among
messages like: *"arrived last night"* or *"arrived this morning"*.

In all of the **Span** examples below, the times are 24 hour starting at 00:00
(midnight). The span does not actually include the second number of the range.
For example, 05:00-08:00 is really 05:00-07:59:59.999...

There are two types of day periods, **fixed** and **locale-specific**.

#### Fixed Periods

The fixed periods have the same definition in each language. The codes am and pm
must always exist, even if your language always uses 24 hour time and doesn't
use am/pm in any patterns (they are required for testing). So use the best term
you can. As long as the 24 hour symbol (H) is used in the patterns, they won't
actually show up in formatted times and dates.

Noon or midnight don't have to be present if the precise terms don't exist in
your language. For example, many languages don't have a special term for
precisely 12:00 noon. They may have a term for "midday" that spans from (say)
11:00-13:00, but not have unique term for exactly 12:00 noon. Such a language
should not have a code for noon show up in the Survey Tool.

In formatting, where your language has a term for *midnight*, it is used instead
of the term for *am* for the point in time 00:00 (= 24:00). Similarly, where
your language has a term for *noon*, it is used instead of *pm* for the point in
time 12:00.

Code English Examples Span *am* am 00:00–12:00 (noon) *pm* pm 12:00–24:00
*midnight* midnight The point in time at precisely 00:00 midnight *noon* noon
The point in time at precisely 12:00 noon

#### Locale-Specific Periods

These mark approximate periods in the day, *and those periods differ between
languages*. The codes are arbitrary, and don't have to match the English meaning
for your language: the important feature is the time span. The spans are
approximate; in reality they may vary with the time of year (they might be
dependent on sunrise), or context (someone might say they went to bed at 2 at
night, and later one say that they woke up at 2 in the morning).

**For a list of the day period IDs defined in CLDR for your language, see [Day
Periods](http://www.unicode.org/cldr/charts/latest/supplemental/day_periods.html).**
If you think the rules are wrong (or missing) for your language, please [file a
ticket](http://unicode.org/cldr/trac/newticket) and supply the missing
information. Here are examples for English and Chinese.

Code English **Span** **Chinese** **Span** *morning1* morning 06:00–12:00 早上
05:00-08:00 *morning2* *unused*
上午 08:00-12:00 *afternoon1* afternoon 12:00–18:00 中午 12:00-13:00 *afternoon2*
*unused*
下午 13:00-19:00 *evening1* evening1 18:00-21:00 晚上 19:00-00:00 *evening2*
*unused*
*unused*
*night1* night 21:00–06:00 凌晨 00:00-05:00 *night2* *unused*
*unused*

### Narrow Date Fields

The narrow date fields are the shortest possible names (in terms of width in
common fonts), and are not guaranteed to be unique. Think of what you might find
on a credit-card-sized wallet or checkbook calendar, such as in English for days
of the week:

S M T W T F S

### Cyclic Name Sets

Cyclic name sets are used in calendars where naming cycles are used for naming
years, months, days, times of day or zodiacs. For example, the Chinese and Hindu
calendars each use a 60-name cycle for naming years. Each cyclic name set has
stand-alone and format textual forms of varying lengths, similar to months or
days.

### Month Patterns

For lunar calendars that can have months added or removed from the usual set of
months in a year, month patterns are used to rename the affected months or the
months around them.

## **Date Field Names**

The date field *name* are used in user interfaces, such as labels in a table
used for inputting values.

*Year* 1942 *Month* ... *Day* ...

The grammatical form should be whatever is typical for such isolated or
stand-alone cases: generally it will be nominative singular. The lettercasing
should be appropriate for middle-of-sentence use, since there is now separate
capitalization context data that can specify how these should be capitalized for
use in a label. Also see the translation guide on
[Capitalization](http://cldr.unicode.org/translation/capitalization).

The fields can be provided for three widths: full, short, and narrow. They are
listed below along with English examples and explanations (a few of the fields
are not straightforward).

F**ield name** **English examples for different name widths** **Explanation of
the field being named, example as a label** **(full)** **-short** **-narrow**
**era** era era era Name of the field that distinguishes different calendar
epochs in a calendar, such as CE / BCE for the Gregorian calendar, or 平成 / 昭和 /
大正 for the Japanese calendar. Can be used as a popup menu label, e.g. “Era: CE ▾
” to select CE for Gregorian calendar. **year** year yr. yr. Name of the field
that designates years. **quarter** quarter qtr. qtr. Name of the field for
quarter of the year. Can be used as a popup menu label, e.g. “Quarter: 2 ▾ ” to
select the second quarter of the year. **week** week wk. wk. Name of the field
for week number of the year. Can be used as a popup menu label, e.g. “Week: 20 ▾
” to select the 20th week of the year for an event. **weekOfMonth** week of
month wk. of mo. wk. of mo. Name of the field for the week number in the month.
Can be used as a popup menu label, e.g. “Week of month: 3 ▾ ” to select the 3rd
week of the month for an event. **day** day day day Name of the field for the
day number in the month. Can be used as a popup menu label, e.g. “Day: 19 ▾ ” to
select the 19th day of the month for an event. **dayOfYear** day of year day of
yr. day of yr. Name of the field for the day number in the year. Can be used as
a popup menu label, e.g. “Day of year: 139 ▾ ” to select the 139th day of the
year for an event. **weekday** day of the week day of wk. day of wk. Name of the
field for the day of the week. Can be used as a popup menu label, e.g. “Day of
the Week: Friday ▾ ” to select Friday for an event. **weekdayOfMonth** weekday
of the month wkday. of mo. wkday. of mo. Name of the field specifying the number
of the occurrence of a particular weekday within the month. Can be used as a
popup menu label, e.g. “Weekday of the month: 3 ▾ ” to select the 3rd Friday of
the month for an event, assuming that Friday is specified with a different
popup. **dayperiod** AM/PM AM/PM AM/PM Name of the field that designates range
of time within a day. Can be used as a popup menu label, e.g. “AM/PM: morning ▾
” to select the desired time for a flight departure; different values could be
used to select other ranges such as "evening", "AM" or "PM", or particular
points such as “noon” or “midnight” (The current English name is not necessarily
the best example for this). **hour** hour hr. hr. Name of the field that
designates hours. **minute** minute min. min. Name of the field that designates
minutes. **second** second sec. sec. Name of the field that designates seconds.
**zone** time zone zone zone Name of the field that designates the time zone.
Can be used as a popup menu label, e.g. “Time zone: Pacific Time ▾ ” to select
Pacific Time; different values could be used to select other time zones, such as
“GMT” or “Beijing Time”.

## Relative Date Names

Some dates can be specified by giving relative names, such as "this month",
"last month" or "next month". For example, if today is Jan 10, then *this month*
is January, *last month* was December, and *next month* is February. Thus:

Category English Examples Meaning *next X* next month The event occurs in the
next calendar month (day, etc). *this X* this month,
today The event occurs in the current calendar month (day, etc). *last X* last
month,
yesterday The event occurs in the immediately last month (day, etc).

**Notes:**

*   There is a difference between unit patterns *(see
    [Plurals](../../getting-started/plurals/index.md))* such as "1 year ago" and
    relative names such as "Last Year". The phrase "1 year ago" has more of
    sense of a duration. For example, on January 2nd, you could refer to an
    event on December 30th as "Last Year". You couldn't refer to it as "1 year
    ago".
*   Some languages have a special word for "The day before yesterday", which may
    also be displayed for translation.

When listing calendar events, or when emails arrived, an interface may
abbreviate dates using relative names. In the following list, the events up to 2
months ago are listed with explicit dates, while the closer ones use relative
dates. These names might be used in various contexts and the new guidance is
that they should be capitalized as appropriate for the middle of a sentence.
They can be programmatically capitalized (using the contextTransform data) for
different contexts, such as for listing in a menu of column of an interface.
Here is how these might be used in a listing of emails:

From Subject Date Rick Re: Meeting in February 12:15 Tom, Sarah,… Avoiding taxes
Yesterday Nicole Investment opportunities in Germany? 4 days ago Rick Meeting in
February Last Month Jane New Year's Eve Party! Dec 12, 2009

## Relative Day-of-the-Week Names

Some dates can be specified by giving relative names, such as "last Saturday",
"this Saturday", or "next Saturday". ***The distinction between 'this' and
'next' may not be present in your language, thus they may have the same
translation.***

Category English Examples Meaning *next X* next Saturday The first Saturday
after today, if it is in the following week. *this X* this Saturday The first
Saturday after today, if it is in the current week. *last X* last Saturday The
first Saturday before today.

For example, if today is Wednesday, then last Saturday was 4 days ago. This
Saturday is in 3 days, and next Monday is in 5 days.

## Week of

There are a number of patterns like “the week of {0}” used for constructions
such as “the week of April 11, 2016” or “the week of April 11–15”. The
placeholder can be a full or partial date. There are related week-of date
pattern that it should be as consistent with as possible, described
[here](../date-time-patterns/index.md).

<dateFormatItem id="MMMMW" count="one">'week' W 'of' MMM</dateFormatItem>
