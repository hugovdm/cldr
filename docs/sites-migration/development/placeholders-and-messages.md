# Placeholders and Messages

There are certain files that describe CLDR formats for translation. These files
are also used for internal testing, and should be updated when new structure is
added.

**xmbPlaceholders.txt**

A RegexLookup file that maps from a path to information about placeholders. For
example:

^//ldml/dates/timeZoneNames/fallbackRegionFormat ; {1}=COUNTRY Argentina;
{0}=CITY Buenos Aires

The values are separated by semicolons, and are one per possible placeholder.
Each value is of the form

placeholder**=**entity**\[space\]**example

So for the case of {1}=COUNTRY Argentina

placeholder - {1} - the CLDR placeholder

entity - COUNTRY - a variable name that represents the kind of entity that will
be substituted

example - Argentina - an example entity.

**xmbHandling.txt**

A RegexLookup file that maps from a path to a message about the path, for use in
examples in ST and otherwise. For example:

^//ldml/localeDisplayNames/localeDisplayPattern/localeSeparator ; The separator
used to compose modifiers in locale (language) names. Note: before translating,
be sure to read http://cldr.org/translation/localepattern.

The value is a message which may contain placeholders, and should always have a
pointer to the documentation for the type of path, in
http://cldr.org/translation/XXX. The placeholders are extracted from the path.
For example:

^//ldml/localeDisplayNames/types/type\\\[@type="(\[^"\]\*)"\]\\\[@key="collation"\]
; The name of "{1} collation" (sorting order). For more information, please see
http://cldr.org/translation/key-names.

In this case, the {1} will be the type attribute value.

For some paths, there is a special initial parameter, such as ROOT metazone;
\[Description TBD\].
