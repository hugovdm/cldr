# Language Tag Equivalences

The Unicode Language and Locale Identifiers are defined in [Chapter
3](http://unicode.org/reports/tr35/#Unicode_Language_and_Locale_Identifiers) of
[UTS #35 Unicode Locale Data Markup Language
(LDML)](http://unicode.org/reports/tr35/). These are based on
[BCP47](http://www.rfc-editor.org/rfc/bcp/bcp47.txt).

These are defined as being case-insensitive, and can use either - or _ as a
separator (while - is preferred, for historical reasons LDML data in CLDR uses
_).

Identifiers like "en", "en-US", and "en-Latn-US" are all valid, and refer to the
same entity. The shorter form is generally preferred, but many implementations
use longer forms. For best interoperability, implementations should be prepared
to accept any of them as equivalent.

In addition, identifiers like "iw" and "he" (for Hebrew) are also both valid,
and refer to the same entity. These are cases where for historical reasons the
international standards that are the basis for these identifiers have multiple
possible aliases for the same thing. For best interoperability, implementations
should also be prepared to accept any of them as equivalent.

### Testing equivalence

To see if two language identifiers are equivalent, do the following. (An example
is shown in square brackets, starting from \[IW-HEBR\].)

1.  perform BCP47 canonicalization, but treating _ and - as equivalent \[ →
    iw-Hebr\]
2.  map any - character to _ for use with CLDR data \[ → iw_Hebr\]
3.  replace all alias type values by their replacement values (see below) \[ →
    he_Hebr\]
4.  maximize each identifier using the likely subtag data (see below) \[ →
    he_Hebr_IL\]

If the results are the same, the language identifiers are equivalent \[IW-HEBR ~
he\]. Of course, implementations can (and should) optimize this processing so
that the common cases are fast. They may only support the data for the locales
that they support to reduce footprint.

The data for determining these equivalences are in the supplemental data
directory of CLDR. The release versions of these can be found in the files
referenced on the [CLDR Releases/Downloads](../downloads/index.md) page. The
links in the discussion below go to the development (trunk) version. Often APIs
are available to support these operations directly, such as in ICU.

A useful API is a LocaleMatcher, which takes as input a list of desired locales
(from the user) and a list of supported locales (based on what the product
supports), and produces a best match. That can take desired={iw-IL, fr};
supported={he, de}, and produce 'he'. It can also use other 'closeness' measures
to get results such as desired={en-AU}; supported={en, en-GB} → en-GB.

### Aliases

The data is in
[supplementalMetadata.xml](http://unicode.org/repos/cldr/trunk/common/supplemental/supplementalMetadata.xml)
under the <alias> element. For example,

<languageAlias type="iw" replacement="he" reason="deprecated"/>

This means that iw ~ he, and that he is the preferred form. However, many
implementations use the other form.

### Likely subtags

The data is in
[likelySubtags.xml](http://unicode.org/repos/cldr/trunk/common/supplemental/likelySubtags.xml)
under the <likelySubtags> element. For example:

<likelySubtag from="en" to="en_Latn_US"/>

This means that en ~ en-US ~ en-Latn ~ en-Latn-US, and en is the shortest form.

<likelySubtag from="zh" to="zh_Hans_CN"/>

<likelySubtag from="zh_Hant" to="zh_Hant_TW"/>

This means that zh ~ zh-CN ~ zh-Hans ~ zh-Hans-CN, and that zh-Hant ~ zh-TW ~
zh-Hant-TW.

For more information, see [Likely
Subtags](http://unicode.org/reports/tr35/#Likely_Subtags).
