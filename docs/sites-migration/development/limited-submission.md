# Limited Submission

In a limited submission cycle, vetters cannot modify data except for:

1.  Organization=CLDR Locales plus specific "high level locales", where the user
    community has kept the data up to date.
2.  Certain paths in those locales (and the set of paths may depend on the
    locale)
    1.  Any missing item at the Organization=CLDR default coverage level for
        that locale
    2.  Specific exceptions

To force a limited submission (typically for the Q4/1 locale),

1.  Set CheckCLDR.LIMITED_SUBMISSION = true;
2.  Modify SubmissionLocales as needed to reflect the exact paths being allowed.

Note: the tool <https://r12a.github.io/app-subtags/> is useful for looking up
language codes. However, be careful: look at XXX.
