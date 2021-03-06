# Default Content

Locales are primarily identified by their ***base*** language. For example,
English \[en\], Arabic \[ar\] or German \[de\].

We also label scripts explicitly, where a language is typically written in
multiple scripts, such as Cyrillic or Latin. For example, Serbian (Cyrillic)
\[sr_Cyrl\] and Serbian (Latin) \[sr_Latn\].

Each language + script combination is treated as a unit. (i.e. People do not mix
different script in the same data set.)

If a language is ***not*** typically written in multiple scripts, then the
script sub-tag is omitted. For example, en_US or ko_KR.

Locales may also have regional variants. For example, English (US) \[en_US\] vs
English (UK) \[en_GB\], or Serbian (Cyrillic, Montenegro) \[sr_Cyrl_ME\] vs
Serbian (Cyrillic, Serbia) \[sr_Cyrl_RS\]. Regions may be countries such as
China \[CN\], parts of countries such as Hong Kong \[HK\] or multi-country
regions such as Latin America \[419\]. Also see [Regional
Variants](http://cldr.unicode.org/translation/getting-started/guide#TOC-Regional-Variants-also-known-as-Sub-locales-).

The contents for the base language should be as widely usable (neutral) as
possible, but **must be** usable without modification for its *default content
locale;* this is the locale for the language’s *default region,* which is
typically the region with the most speakers of the language. A default content
locale has no data other than identity information, it inherits all data from
its parent.

For example:

*   American English \[en_US\] is the default content locale for English \[en\]
*   German (Germany) \[de_DE\] is the default content locale for German \[de\].
*   Portuguese (Brazil) \[pt_BR\] is the default content locale for Portuguese
    \[pt\]
*   Serbian (Cyrillic) \[sr_Cyrl\] is the default content locale for Serbian
    \[sr\], which is the default for Serbian (Cyrillic, Seriba) \[sr_Cyrl_RS\] .
*   Arabic (World) \[ar_001\] is the default content locale for Arabic \[ar\],
    which is for Modern Standard Arabic.

**Tips for linguists:**

1.  Make sure the base language content is correct; as widely usable (neutral)
    as possible, but must be usable **without** modification in the default
    content locale.
    For example:
    *   English \[en\] locale content must be usable for English (US)
    *   Arabic \[ar\] content must be usable for Arabic (world/neutral).
2.  Make sure that where there is a difference in a sub-region, the differences
    are represented in the regional-variant locale.
    For example:
    *   Spanish (Mexico) \[es_MX\] differences from Spanish (Latin America)
        \[es_419\]
    *   Arabic (Egypt) \[ar_EG\] that are different from Arabic (World)
        \[ar_001\]
