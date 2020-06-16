# Grammatical Inflection

[TOC]

For a limited number of locales and units of measurement, we are adding support
for inflections for noun case and gender. The following is the limited set of
locales in v38:

Grammatical Feature

Locales

Case

pl, ru, de, hi

Gender

pl, ru, de, nb, da, sv, hi, es, fr, it, nl, pt

Not all units will have the extra information: they are limited to a subset of
about 75. For these units, many but not all forms have “seed” data, marked as
provisional.

**Important:** Many of the new data items have "seed" data supplied for them.
These are marked as provisional (✘), and need to be reviewed. If you use the
Dashboard, don't just use the pencil icon ✏️ to change items. If you do that,
you can't ensure that the seed data and original data is consistent. Instead,
right click on the Code value, such as:

long-one-accusative

## Miscellaneous > Minimal Pairs

<https://st.unicode.org/cldr-apps/v#/de/MinimalPairs/>

Here you need to add patterns that distinguish different cases or genders.

    Case. Provide a phrase that requires the noun or noun/adjective placeholder
    to be in that case.

        For example, for German, “... mit {0} ...” requires the {0} to be in the
        dative case (for a noun phrase).

        There should be some noun-phrase placeholder that would change form for
        each member of the set.

        Not all possible placeholder values will exhibit differences. For
        example, in German only masculine noun phrases are different in the
        accusative case (den Mann vs der Mann). Sometimes you may need a
        combination of words, as is done for Welsh plurals.

    Gender. Provide a phrase that requires a noun or noun/adjective placeholder
    to have that gender.

        For example, the phrase “Die {0} ist…” requires the noun to be feminine
        (singular) .

        The placeholder for gender will be different words.

        Make sure that the phrase limits unwanted forms. For example, “Die {0}”
        would be insufficient for German feminine, because the placeholder could
        be masculine plural.

## Units > Compound Units

<https://st.unicode.org/cldr-apps/v#/fr/CompoundUnits/>

There are two Codes that need your attention: Power2 and Power3. These are
typically adjectives, and would need to agree with unit of measurement.

The Code is now longer, allowing for case and gender. If the language doesn’t
have case, the gender will be “nominative”. If the language doesn’t have gender,
it will be “dgender”. That is also used for a selected instance for gendered
languages: either neuter or masculine (if the language has no neuter). Example:

*   long-one-nominative-dgender requests the masculine case in French
*   long-one-nominative-feminine requests the feminine case in French

(Note: the dgender is a workaround: we plan to show the correct value in the
future)

## Units> Other > Liter > gender

<https://st.unicode.org/cldr-apps/v#/de/Volume/1027df24bd31941e>

If your language supports gender for units of measure, you’ll see a new element
for the gender of each relevant unit. For example, a Liter in German is
masculine. If you try to put in an illegal value, you’ll get a message that
lists the valid values for your locale, such as The gender value for this locale
must be one of: \[feminine, masculine, neuter\]

Many of the units have “seed” values for the gender variants. These are marked
as provisional, and you’ll have to verify whether they are correct or need
changes.

## Units> Other > Liter > long-one-accusative

<https://st.unicode.org/cldr-apps/v#/de/Volume/529c3100fd1c0226>

If your language support case inflections for units of measure, you’ll see new
rows for the relevant units. You should pick the form appropriate for the case
and plural category. Often it is the same as for some other category.

Many of the units have “seed” values for the case variants. These are marked as
provisional, and you’ll have to verify whether they are correct or need changes.

English (inch-pound) units. Many of the units are just used in a few
English-speaking countries. While it may seem pointless to translate these
obscure units, there are circumstances that require them.

Some inch-pound units are of different sizes in the US and the UK. To
distinguish them, the Header will use the term Imperial for the British version.
For example, Gallon is always the US version, and Gallon-Imperial is always the
UK version.

    Typically locales will just qualify the UK version, such as “{0} Imp.
    Gallone” or “{0} britische Gallone”. The seed data may differ between these
    conventions; if so you’ll have to change either the seed data or the data
    from the last release.

    In some cases, the US version has a qualification, such as “{0}
    amerikanische Flüssiggallone”. Again, you’ll want to check that the
    last-release and seed data are consistent, and fix if not.

    In some cases, the seed data will be completely wrong, and have a name for
    the UK version being used for the US unit, or vice versa. These you’ll need
    to fix.

    You also want to review the other units to make sure that they have
    consistent phrasing. For example, you don’t want “Flüssiggallone” for one
    unit, and simply “Gallone” for another.

    In general, shorter is better, as long as it is clear.
