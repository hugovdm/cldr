# Language/Locale Names

Some language names are simple, like "English". However, it is often important
to distinguish a variant of the language, even when it is only written. For
example, British English and American English are often written differently. In
some cases, the difference can be quite substantial, such as when the same
language is written with different [scripts](script-names.md) (aka writing
systems, like Latin letters vs Greek letters).

Thus more complex language names may be composed from simple languages plus
variants. A pattern is used to control how the translations for language,
script, and region codes are composed into a name when the compound code doesn't
have a specific translation. An example is "αγγλικά (Αυστραλία)", which has the
native name for "English", followed by the native word for "Australia" in
parentheses. See [Patterns for Locale/Language Names](localepattern.md).

For the simple language names, please follow these guidelines:

*   Each of the simple language names **must** be unique.
*   Don't use commas and don't invert the name (eg use "French Creole", not
    "French, Creole").
*   Don't use the characters "(" and ")", since they will be confusing in
    combination with countries or scripts in more complex language names. If you
    have to use brackets, use square ones: \[ and \].
*   The most neutral grammatical form for the language name should be chosen.
*   Use the capitalization that would be appropriate for a language name in the
    middle of a sentence; the <contextTransforms> data can specify the
    capitalization for other contexts. For more information, see
    [Capitalization](../translation-guide-general/capitalization.md).

## Unique Names

There are a few special cases:

*   Local variants of a language sometimes need to be translated, such as
    *Australian English* (internal code: en_AU) or Simplified Chinese (zh_Hans).
*   "Iberian Portuguese" or "European Portuguese" is the style of Portuguese
    used in Portugal (as opposed to Brazil)
*   Similarly "Iberian Spanish" or "European Spanish" is the style of Spanish
    specifically used in Spain (as opposed to Latin America).
*   "Swiss High German" (*Schweizer Hochdeutsch*), also called "Swiss Standard
    German", has the code `de_CH`.
*   "Swiss German" (*Schwyzerdütsch*) has the code `gsw`.
