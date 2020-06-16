# Fixing Errors

[TOC]

I distributed the errors according to what we discussed yesterday.

<https://docs.google.com/spreadsheet/ccc?key=0AqRLrRqNEKv-dGNSbnRLbmpKZHpRX2xhQkJxVXRla3c#gid=0>

## Basic Process

Please look over the locales with errors assigned to you. Easiest way to see the
errors is to go to the locale, then hit Review>Priority Items.

*   **Set your coverage to Comprehensive at the top!**
*   **Make sure Errors is checked and nothing else is.**

If it is not obvious how to deal with particular errors or you have questions,
then please raise it in a Reply-All to this message. If you have questions, you
can also make a vote/fix, then raise it here just in case. Also, you may not
have enough votes to get your answer selected; just ask here for someone from
another org to second you.
***Make sure to look over the forum.*** Many people had trouble understanding or
using the tool, and sometimes posted the 'correct' answer to the forum instead.
Note that there are two ways to get to the forum postings. From the Sections
menu (at the bottom) or an icon at the top right on the Review pages.
Unfortunately, even if someone had a post on a row, the "forum icon" often
doesn't appear in the detail panel for that row, so you have to use the
workaround below.
If you have questions, try always to list the URL that you get in the address
bar from clicking on the row, if possible.

### Example

There were two contending versions of the locale separator for Arabic, and I
chose the one with the Arabic-script comma:
<http://st.unicode.org/cldr-apps/v#/ar/Locale_Name_Patterns/1d142c4be7841aa7>

## Answers in Forum

If the translator has filed the correct answer in the forum instead of in the
main tool, here's what you do.

In Priority Items you'll see:

No.CodeEnglishCLDR 23Winning
24Fix?CommentLight-Year483narrow-one{0}ly*missing*{0} سنة
ضوئية[Error\*](http://st.unicode.org/cldr-apps/survey?_=ar&strid=9d601659b94d83e)<value
too wide> Too wide by about 60% (with common fonts).
Click on the Error\* item, and get to the row:
<http://st.unicode.org/cldr-apps/v#/ar/Length/2710bb6b1d691b1e>

The item is way too long. Open up the forum and search for
Light-Year-narrow-zero (get that from the header+code for the row). There you
find the value to use: {0}س ض. Copy it, then go back to
<http://st.unicode.org/cldr-apps/v#/ar/Length/2710bb6b1d691b1e> and paste the
value.

Keeping two windows open makes this easier.

## Country/Region Collisions

There is more information on how to fix these on [Country/Region
Names](../translation/displaynames/country-names.md), under "Unique Names". Try
to get a replacement either from the forum (see above) or from a native speaker.
If you can't get a fix that resolves the problem, put the ISO code in brackets
after a region, or in the worst case, remove the translation from the less
important one.

## Currency collisions

Often one of them is an old currency (not a legal tender anywhere anymore). The
mistake people make is to omit the date. To fix, just add the date, as in
<http://st.unicode.org/cldr-apps/v#/is/Currencies/401f2e2bc981cf85>.

Unfortunately, there is a but in the Survey Tool, so you won't see the error go
away in the one you *didn't* fix. That should go away the next time the ST is
rebooted.

If that doesn't work, and you can't get the right translation, then remove the
translation on the lesser-used currency (eg, vote for the ISO code).

## No Narrow Form

> users say sometimes there is no shorter form that satisfies "narrow" width
requirements for weather units \[punjabi\]

Try to get a replacement either from the forum (see above) or from a native
speaker. If you can't get a replacement that is short enough, use the English
version.

## Superfluous Plural Forms

>docs don't say what 'superfluous plural form' is or what to do about it

The superfluous plural forms are ones that cannot occur with the pattern given.
For example, "00 million" in English will never need a form for the "one" plural
category, since the values are limited to 10-99, 10.x-99.x etc. So "1" cannot
occur with that pattern.

Since they will never occur, we don't worry much about the value. If you are
getting a collision error, easiest is to just copy the "other" form with the
same digits.

## Compact Numbers

If you have collisions between, say, the 10 digit form and the 13 digit form,
look at the related forms to see if you use them. For example, if both have
"0B", and the 11 or 12 digit form follows a different pattern with just more
visible digits (eg "00k M" and "000k M"), and modify the 10 digit form to fit.

## Compound Language Names

If there is a collision between a compound language name (eg for es_419) and any
other, just remove it (vote for the code).

Example: <http://st.unicode.org/cldr-apps/v#/uz/Languages/335f9eebd92b43e3>
where Latin American Spanish had the same name as Spanish. Just vote for es_419,
which will cause the actual name to be composed (as you can see by the example
below it).
