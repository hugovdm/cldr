# Names and Patterns

## Display Names

These are intended for stand-alone use such as the label of a field where values
may be entered, for example Minutes and Seconds in the example below.

Enter desired time to liftoff:

Minutes: Seconds:

The expectation is that the display names would be in nominative form for
languages in which it makes a difference. There may be cases in which a display
name could be used in contexts for which nominative would be inappropriate, but
the hope is that CLDR clients would arrange the use of display names in user
interfaces so that nominative form is not inappropriate.

The unit data is provided in three widths:

*   long: typically a fully spelled-out name
*   short: a distinctive abbreviated form, not easily confused with another unit
*   narrow: as short as possible for situations with limited display space.
    Typically this form eliminates spaces and punctuation to the extent
    possible, and uses abbreviations that might only be clear in context.

Note that if in your locale certain abbreviations are always understood to mean
particular units, then different abbreviations should generally be used even in
the narrow form for other units. For example, if “m” is always understood to
mean “meters”, then even in the narrow form a different abbreviation should be
used for “minutes”—perhaps “min”, “mn”, or even “m.”.

## Simple Units

Simple units are cases like "{0} mile" or "{0} miles". These have from 1 to 6
[plural forms](../getting-started/plurals/index.md), depending on the language.
Units also have a display name, such as "miles", used as labels in interfaces.

## Compound Units

Some units are compound units, like "miles per hour". When formatting, software
will first look for a specialized pattern (with the right plural form), then if
that is not available, look for a compound unit and compose a fallback format.
Hover over the English column and the Winning column to see examples. The
following patterns are available:

**Examples** **Description** per cm/s, centimeters per second Used to compose
units consisting of a division of two source units when there is no specialized
pattern available. See
[perUnitPatterns](http://www.unicode.org/reports/tr35/tr35-general.html#perUnitPatterns).
times kW⋅h,
kilowatt-hour Used to compose units consisting of a multiplication of two source
units when there is no specialized pattern available. See [kilowatt
hour](https://en.wikipedia.org/wiki/Kilowatt_hour). square, cubic square meters
• Used to compose area or volume measures when there is no specialized pattern
available. The width should correspond to the base unit's width, as in [{0}
square
meter](https://cldr-smoke.unicode.org/smoketest/v#/USER/Area/5888c3421f06626c)
or [{0}
m²](https://cldr-smoke.unicode.org/smoketest/v#/USER/Area/6b88ccc5db865200).
• The short form will typically be superscripts {0}² or {0}³; the long form may
be the same or may be spelled out (as in English). Inflected languages may need
to use the superscripts instead of spelled-out forms where the units may have
different genders that would force adjective agreements.
• Note that the base unit will be lowercased when there is no spacing around the
{0}. Thus {0} Meter will be lowercased when composed with Quadrat{0}. milli-,
kilo-,… millimeter • Used to compose **metric** units when there is no
specialized pattern available.
• The width should correspond to the base unit's width, as in [{0}
decimeter](https://cldr-smoke.unicode.org/smoketest/v#/USER/Length/ce4591152ece6f2)
or [{0}
dm](https://cldr-smoke.unicode.org/smoketest/v#/fr/Length/1f1b7ef47cfaee78).
• Note that the base unit will be lowercased when there is no spacing around the
{0}. Thus {0} Meter will be lowercased when composed with Milli{0}.

The specialized patterns are needed where there is a special abbreviation, like
"mph" instead of "m/hr".

### Specialized Pattern

In addition, there are some very common combinations that are translated as a
whole, such as "{0} kilometro par hora". In that case, the number is substituted
directly for the {0} placeholder.

### Per Unit Pattern

In many languages, the "per Y" part is inflected, and the dividing unit can't be
simply substituted for {1}. Because of that, there are "per unit" patterns that
are of the form "{0} per hour". For that case, the process is simpler. The first
two steps are the same, but then the result is substituted into the "{0} per
hour" pattern directly.

### Fallback Format: two units

Some units are formed by combining other units. The most common of this is X per
Y, such as "miles per hour". There is a "per" pattern that is used for this. For
example, "{0} per {1}" might get replaced by "*10 meters* **per** *second*".

Given an amount, and two units, the process uses the available patterns to put
together a result, as described on
[perUnitPatterns](http://www.unicode.org/reports/tr35/tr35-general.html#perUnitPatterns).
(e.g. "3 kilograms" + "{0} per second" → "3 kilograms per second")
