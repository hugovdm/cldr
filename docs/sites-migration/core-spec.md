# Core Specification

*(This is a draft of converting the LDML spec to a different format. It is not
updated.)*

## 1. Introduction

Not long ago, computer systems were like separate worlds, isolated from one
another. The internet and related events have changed all that. A single system
can be built of many different components, hardware and software, all needing to
work together. Many different technologies have been important in bridging the
gaps; in the internationalization arena, Unicode has provided a lingua franca
for communicating textual data. However, there remain differences in the locale
data used by different systems.

The best practice for internationalization is to store and communicate
language-neutral data, and format that data for the client. This formatting can
take place on any of a number of the components in a system; a server might
format data based on the user's locale, or it could be that a client machine
does the formatting. The same goes for parsing data, and locale-sensitive
analysis of data.

But there remain significant differences across systems and applications in the
locale-sensitive data used for such formatting, parsing, and analysis. Many of
those differences are simply gratuitous; all within acceptable limits for human
beings, but yielding different results. In many other cases there are outright
errors. Whatever the cause, the differences can cause discrepancies to creep
into a heterogeneous system. This is especially serious in the case of collation
(sort-order), where different collation caused not only ordering differences,
but also different results of queries! That is, with a query of customers with
names between "Abbot, Cosmo" and "Arnold, James", if different systems have
different sort orders, different lists will be returned. (For comparisons across
systems formatted as HTML tables, see \[[Comparisons](#Comparisons)\].)

**Note:** There are many different equally valid ways in which data can be
judged to be "correct" for a particular locale. The goal for the common locale
data is to make it as consistent as possible with existing locale data, and
acceptable to users in that locale.

This document specifies an XML format for the communication of locale data: the
Unicode Locale Data Markup Language (LDML). This provides a common format for
systems to interchange locale data so that they can get the same results in the
services provided by internationalization libraries. It also provides a standard
format that can allow users to customize the behavior of a system. With it, for
example, collation (sorting) rules can be exchanged, allowing two
implementations to exchange a specification of tailored collation rules. Using
the same specification, the two implementations will achieve the same results in
comparing strings (see \[[UCA](#UCA)\]). Unicode LDML can also be used to let a
user encapsulate specialized sorting behavior for a specific domain, or create a
customized locale for a minority language. Unicode LDML is also used in the
Unicode Common Locale Data Repository (CLDR). CLDR uses an open process for
reconciling differences between the locale data used on different systems and
validating the data, to produce with a useful, common, consistent base of locale
data.

For more information, see the Common Locale Data Repository project page
\[[LocaleProject](#localeProject)\].

As LDML is an interchange format, it was designed for ease of maintenance and
simplicity of transformation into other formats, above efficiency of run-time
lookup and use. Implementations should consider converting LDML data into a more
compact format prior to use.

### 1.1 Conformance

There are many ways to use the Unicode LDML format and the data in CLDR, and the
Unicode Consortium does not restrict the ways in which the format or data are
used. However, an implementation may also claim conformance to LDML or to CLDR,
as follows:

***UAX35-C1.*** An implementation that claims conformance to this specification
shall:

1.  Identify the sections of the specification that it conforms to.
    *   For example, an implementation might claim conformance to all LDML
        features except for *transforms* and*segments*.
2.  Interpret the relevant elements and attributes of LDML documents in
    accordance with the descriptions in those sections.
    *   For example, an implementation that claims conformance to the date
        format patterns must interpret the characters in such patterns according
        to [Date Field Symbol Table](#Date_Field_Symbol_Table).
3.  Declare which types of CLDR data that it uses.
    *   For example, an implementation might declare that it only uses language
        names, and those with a *draft* status of*contributed* or *approved*.

***UAX35-C2.*** An implementation that claims conformance to Unicode locale or
language identifiers shall:

1.  Specify whether Unicode locale extensions are allowed
2.  Specify the canonical form used for identifiers in terms of casing and field
    separator characters.

External specifications may also reference particular components of Unicode
locale or language identifiers, such as:

*Field X can contain any Unicode region subtag values as given in Unicode
Technical Standard #35: Unicode Locale Data Markup Language (LDML), excluding
grouping codes.*

## 2. What is a Locale?

Before diving into the XML structure, it is helpful to describe the model behind
the structure. People do not have to subscribe to this model to use data in
LDML, but they do need to understand it so that the data can be correctly
translated into whatever model their implementation uses.

The first issue is basic: *what is a locale?* In this model, a locale is an
identifier (id) that refers to a set of user preferences that tend to be shared
across significant swaths of the world. Traditionally, the data associated with
this id provides support for formatting and parsing of dates, times, numbers,
and currencies; for measurement units, for sort-order (collation), plus
translated names for time zones, languages, countries, and scripts. The data can
also include support for text boundaries (character, word, line, and sentence),
text transformations (including transliterations), and other services.

Locale data is not cast in stone: the data used on someone's machine generally
may reflect the US format, for example, but preferences can typically set to
override particular items, such as setting the date format for 2002.03.15, or
using metric or Imperial measurement units. In the abstract, locales are simply
one of many sets of preferences that, say, a website may want to remember for a
particular user. Depending on the application, it may want to also remember the
user's time zone, preferred currency, preferred character set, smoker/non-smoker
preference, meal preference (vegetarian, kosher, and so on), music preference,
religion, party affiliation, favorite charity, and so on.

Locale data in a system may also change over time: country boundaries change;
governments (and currencies) come and go: committees impose new standards; bugs
are found and fixed in the source data; and so on. Thus the data needs to be
versioned for stability over time.

In general terms, the locale id is a parameter that is supplied to a particular
service (date formatting, sorting, spell-checking, and so on). The format in
this document does not attempt to represent all the data that could conceivably
be used by all possible services. Instead, it collects together data that is in
common use in systems and internationalization libraries for basic services. The
main difference among locales is in terms of language; there may also be some
differences according to different countries or regions. However, the line
between *locales* and *languages*, as commonly used in the industry, are rather
fuzzy. Note also that the vast majority of the locale data in CLDR is in fact
language data; all non-linguistic data is separated out into a separate tree.
For more information, see *[Appendix D: Language and Locale
IDs](#Language_and_Locale_IDs)*.

We will speak of data as being "in locale X". That does not imply that a locale
*is* a collection of data; it is simply shorthand for "the set of data
associated with the locale id X". Each individual piece of data is called a
*resource* or *field*, and a tag indicating the key of the resource is called a
*resource tag.*

## 3. Unicode Language and Locale Identifiers

Unicode LDML uses stable identifiers based on \[[BCP47](#BCP47)\] for
distinguishing among languages, locales, regions, currencies, time zones,
transforms, and so on. There are many systems for identifiers for these
entities. The Unicode LDML identifiers may not match the identifiers used on a
particular target system. If so, some process of identifier translation may be
required when using LDML data.

A *Unicode language identifier* has the following structure (provided in either
EBNF (Perl-based) or ABNF \[[RFC5234](#RFC5234)\]):

EBNF

ABNF

unicode_language_id="root" | unicode_language_subtag (sep
unicode_script_subtag)? (sep unicode_region_subtag)? (sep
unicode_variant_subtag)\*="root" / unicode_language_subtag \[sep
unicode_script_subtag\] \[sep unicode_region_subtag\] \*(sep
unicode_variant_subtag) sep= "-" | "_"= "-" / "_"

For example, "en-US" (American English), "en_GB" (British English), "es-419"
(Latin American Spanish), and "uz-Cyrl" (Uzbek in Cyrillic) are all Unicode
language identifiers.

A *Unicode locale identifier* is composed of a Unicode language identifier plus
(optional) locale extensions. It has the following structure:

EBNF

ABNF

unicode_locale_id= unicode_language_id unicode_locale_extensions?=
unicode_language_id \[unicode_locale_extensions\]unicode_locale_extensions= sep
"u" ((sep keyword)+ |(sep attribute)+ (sep keyword)\*)= sep "u" (1\*(sep
keyword) / 1\*(sep attribute) \*(sep keyword))keyword= key (sep type)?= key
\[sep type\]key= alphanum{2}= 2alphanumtype= alphanum{3,8} (sep
alphanum{3,8})\*= 3\*8alphanum \*(sep 3\*8alphanum)attribute= alphanum{3,8}=
3\*8alphanumalphanum= \[0-9 A-Z a-z\]= ALPHA / DIGIT

For historical reasons, this is called a Unicode locale identifier. However, it
really functions (with few exceptions) as alanguage identifier, and accesses
language-based data. Except where it would be unclear, this document uses the
term "locale" data loosely to encompass both types of data: for more
information, see *[Appendix D: Language and Locale
IDs](#Language_and_Locale_IDs)*.

Although not shown in the syntax above, Unicode locale identifiers may also have
\[[BCP47](#BCP47)\] extensions (other than "u") and private use subtags; these
are not, however, relevant to their use in Unicode.

As for terminology, the term *code* may also be used instead of "subtag", and
"territory" instead of "region". The primary language subtag is also called the
*base language code*. For example, the base language code for "en-US" (American
English) is "en" (English). The *type* may also be referred to as a *value* or
*key-value*.

The Unicode locale identifier is based on \[[BCP47](#BCP47)\]. However, it
differs in the following ways:

*   It does not allow for the full syntax of \[[BCP47](#BCP47)\]:
    *   No irregular or BCP47 grandfathered tags are allowed
    *   No extlang subtags are allowed
*   It allows for certain additions:
    *   For field separator characters, the "_" character can be used as well as
        the "-" used in \[[BCP47](#BCP47)\].
    *   "root" to indicate the generic locale used as the parent of all
        languages in the CLDR data model.
    *   Defined semantics of certain private use codes, and some "macrolanguage"
        codes.

The identifiers can vary in case and in the separator characters. The "-" and
"_" separators are treated as equivalent. All identifier field values are
case-insensitive. Although case distinctions do not carry any special meaning,
an implementation of LDML should use the casing recommendataions in
\[[BCP47](#BCP47)\], especially when a Unicode locale identifier is used for
locale data exchange in software protocols. The recommendation is that: the
region subtag is in uppercase, the script subtag is in title case, and all other
subtags are in lowercase.

**Note:** The current version of CLDR uses upper case letters for variant
subtags in its file names for backward compatibility reasons. This might be
changed in future CLDR releases.

The Unicode language and locale identifier field values are given in the
following table. Note that some private-use field values may be given specific
values.

Language/Locale Field DefinitionsFieldAllowable CharactersAllowable
valuesunicode_language_subtag

(also known as a *Unicode base language code)*

ASCII letters\[[BCP47](#BCP47)\] subtag values marked as **Type: language**

ISO 639-3 introduces the notion of "macrolanguages", where certain ISO 639-1 or
ISO 639-2 codes are given broad semantics, and additional codes are given for
the narrower semantics. For backwards compatibility, Unicode language
identifiers retain use of the narrower semantics for these codes. For example:

ForUse*Not*Standard Chinese (Mandarin)`zhcmn`Standard Arabic`ararb`Standard
Malay`mszsm`Standard Swahili`swswh`Standard Uzbek`uzuzn`Standard Kokani`kokknn`

For a full list, see
[supplementalMetadata.xml](http://unicode.org/repos/cldr/trunk/common/supplemental/supplementalMetadata.xml).
If a language subtag matches the type attribute of a languageAlias element, then
the replacement value is used instead. For example, because "swh" occurs in
<languageAlias type="swh" replacement="sw"/>, "sw" must be used instead of
"swh". Thus Unicode language identifiers use "ar-EG" for Standard Arabic
(Egypt), not "arb-EG"; they use "zh-TW" for Mandarin Chinese (Taiwan), not
"cmn-TW".

The private use codes from `qfz..qtz` will never be given specific semantics in
Unicode identifiers, and are thus safe for use for other purposes by other
applications.

unicode_script_subtag

(also known as a *Unicode script code)*

ASCII letters\[[BCP47](#BCP47)\] subtag values marked as **Type: script**

In most cases the script is not necessary, since the language is only
customarily written in a single script. Examples of cases where it is used are:

`az_Arab`Azerbaijani in Arabic script`az_Cyrl`Azerbaijani in Cyrillic
script`az_Latn`Azerbaijani in Latin script`zh_Hans`Chinese, in simplified
script`zh_Hant`Chinese, in traditional script

Unicode identifiers give specific semantics to three Unicode Script values
\[[UAX24](#UAX24)\]:

`Zyyy`Common `Qaai`Inheritedthe preferred form is now Zinh`Zzzz`Unknown

The private use subtags from Qaaq..Qabx will never be given specific semantics
in Unicode identifiers, and are thus safe for use for other purposes by other
applications.

unicode_region_subtag

(also known as a *Unicode region code,* or *a Unicode territory code)*

ASCII letters and digits\[[BCP47](#BCP47)\] subtag values marked as **Type:
region**

Unicode identifiers give specific semantics to three private use subtags:

`QO`Outlying Oceania `QU`European Union*the preferred form is now EU*`ZZ`Unknown
or Invalid Territory

The private use subtags from XA..XZ will never be given specific semantics in
Unicode identifiers, and are thus safe for use for other purposes by other
applications.

unicode_variant_subtag

(also known as a *Unicode language variant code)*

ASCII letters\[[BCP47](#BCP47)\] subtag values marked as **Type:
variant***attribute*ASCII letters and digitsCurrently not used, reserved for
future use.*key*ASCII letters and digits*key*/*type* definitions are discussed
below. For information on the process for adding new *key*/*type*, see
\[[LocaleProject](#localeProject)\].*type*ASCII letters and digits

*Examples:*

en fr_BE de_DE_u_co_phonebk_cu_ddm

A locale that only has a language subtag (and optionally a script subtag) is
called a *language locale*; one with both language and territory subtag is
called a *territory locale* (or *country locale*).

The following chart contains a subset of key/type combinations currently
available. For the complete list of keys and types defined for Unicode locale
extensions, see Appendix Q: [Locale Extension Key and Type
Data](#Locale_Extension_Key_and_Type_Data).

Key/Type Definitionscategorykey
(old key name)key descriptiontype
(old type name)type descriptionCalendar"ca"
(calendar)Calendar algorithm
*(For information on the calendar algorithms associated with the data used with
these, see \[[Calendars](#Calendars)\].)*"buddhist"Thai Buddhist calendar (same
as Gregorian except for the year)"chinese"Traditional Chinese
calendar"coptic"Coptic calendar"ethioaa"
(ethiopic-amete-alem)Ethiopic calendar, Amete Alem (epoch approx. 5493
B.C.E.)"ethiopic"Ethiopic calendar, Amete Mihret (epoch approx. 8 C.E.)"gregory"
(gregorian)Gregorian calendar"hebrew"Traditional Hebrew calendar"indian"Indian
calendar"islamic"Astronomical Arabic calendar"islamicc"
(islamic-civil)Civil (algorithmic) Arabic calendar"japanese"Japanese Imperial
calendar (same as Gregorian except for the year, with one era for each
Emperor)"persian"Persian calendar"roc"Republic of China calendar>Collation"co"
(collation)Collation type"big5han"Pinyin ordering for Latin, big5 charset
ordering for CJK characters. (used in Chinese)"dict"
(dictionary)For a dictionary-style ordering (such as in Sinhala)"direct"Hindi
variant"gb2312"
(gb2312han)Pinyin ordering for Latin, gb2312han charset ordering for CJK
characters. (used in Chinese)"phonebk"
(phonebook)For a phonebook-style ordering (such as in German)"pinyin"Pinyin
ordering for Latin and for CJK characters; that is, an ordering for CJK
characters based on a character-by-character transliteration into a pinyin.
(used in Chinese)"reformed"Reformed collation (such as in Swedish)"standard"The
default ordering for each language. For root it is \[[UCA](#UCA)\] order; for
each other locale it is the same as UCA ordering except for appropriate
modifications to certain characters for that language. The following are
additional choices for certain locales; *they only have effect in certain
locales.*"stroke"Pinyin ordering for Latin, stroke order for CJK characters
(used in Chinese)"trad"
(traditional)For a traditional-style ordering (such as in Spanish)"unihan"Pinyin
ordering for Latin, Unihan radical-stroke ordering for CJK characters. (used in
Chinese)Collation parameters"ka"
(colAlternate)Alternate handling"noignore"
(non-ignorable)
"shifted"*For information on each collation setting parameter, see: 5.14.1
[<collation>](#Collation_Element)*"kb"
(colBackwards)Backward second level weight"true"
(yes)
"false"
(no)"kc"
(colCaseLevel)Case level"kn"
(colNumeric)Numeric"kh"
(colHiraganaQuaternary)Hiaragana quarternary"kk"
(colNormalization)Normalization"kf"
(colCaseFirst)Case first"upper"
"lower"
"false"
(no)"ks"
(colStrength)Collation strength"level1"
(primary)
"level2"
(secondary)
"level3"
(tertiary)
"level4"
(quarternary)
"identic"
(identical)"vt"
(variableTop)Variable top*Hexadecimal digits representing Unicode code point(s).
See Appendix Q: [Locale Extension Keys and
Types](#Locale_Extension_Key_and_Type_Data) for the details.*Currency"cu"
(currency)Currency type*ISO 4217 code,*

*plus others in common use*

Currency value identified by ISO 4217 code, plus others in common use. Also uses
XXX as*Unknown or Invalid Currency*. A *Unicode currency code* is defined as
this set of values.

For more information, see C.1 [Supplemental Currency
Data](#Supplemental_Currency_Data).

Number"nu"
(numbers)Numbering system*Unicode script subtag*Four-letter types indicate the
decimal numbering system using digits \[:GeneralCategory=Nd:\] for the script
represented in Unicode.

For more information, see Section C.13[Numbering Systems](#Numbering_Systems).

"arabext"Extended Arabic-Indic digits ("arab" means the base Arabic-Indic
digits)"armnlow"Armenian lowercase numerals"fullwide"Full width
digits"greklow"Greek lowercase numerals"hansfin"Simplified Chinese financial
numerals"hantfin"Traditional Chinese financial numerals"jpanfin"Japanese
financial numerals"roman"Roman numerals"romanlow"Roman lowercase numeralsTime
zone"tz"
(timezone)Time zone*Unicode short time zone IDs*See Appendix Q: [Locale
Extension Keys and Types](#Locale_Extension_Key_and_Type_Data)for the complete
list.Locale variant"va"Common variant type"posix"POSIX style locale variant

For more information on the allowed keys and types, see the specific elements
below, and Appendix Q: [Locale Extension Key and Type
Data](#Locale_Extension_Key_and_Type_Data).

Additional keys or types might be added in future versions. Implementations of
LDML should be robust to handle any syntactically valid key or type values.

### 3.1 Unknown or Invalid Identifiers

The following identifiers are used to indicate an unknown or invalid code in
Unicode language and locale identifiers. For Unicode identifiers, the region
code uses a private use ISO 3166 code, and Time Zone code uses an additional
code; the others are defined by the relevant standards. When these codes are
used in APIs connected with Unicode identifiers, the meaning is that either
there was no identifier available, or that at some point an input identifier
value was determined to be invalid or ill-formed.

Code TypeValueDescription in Referenced StandardsLanguage`und`Undetermined
languageScript`Zzzz`Code for uncoded script, Unknown \[[UAX24](#UAX24)\]Region
`ZZ`Unknown or Invalid TerritoryCurrency`XXX`The codes assigned for transactions
where no currency is involvedTime Zone`unk`Unknown or Invalid Time Zone

When only the script or region are known, then a locale ID will use "und" as the
language subtag portion. Thus the locale tag "und_Grek" represents the Greek
script; "und_US" represents the US territory.

#### 3.1.1 Numeric Codes

For region codes, ISO and the UN establish a mapping to three-letter codes and
numeric codes. However, this does not extend to the private use codes, which are
the codes 900-999 (total: 100), and AAA, QMA-QZZ, XAA-XZZ, and ZZZ (total:
1092). Unicode identifiers supply a standard mapping to these: for the numeric
codes, it uses the top of the numeric private use range; for the 3-letter codes
it doubles the final letter. These are the resulting mappings for all of the
private use region codes:

RegionUN/ISO NumericISO
3-Letter`AA958AAAQM..QZ959..972QMM..QZZXA..XZ973..998XAA..XZZZZ999ZZZ`

For script codes, ISO 15924 supplies a mapping (however, the numeric codes are
not in common use):

ScriptNumeric`Qaaa..Qabx900..949`

### 3.2 BCP 47 Conformance

Unicode language and locale identifiers inherit the design and the repertoire of
subtags from \[[BCP47](#BCP47)\] Language Tags. There are some extensions and
restrictions made for the use of identifiers in CLDR.

#### 3.2.1 -u- Extension

\[[BCP47](#BCP47)\] Language Tags provides a mechanism for extending language
tags for use in various applications by extension subtags. Each extension subtag
is identified by a single alphanumeric character subtag assigned by IANA.
Unicode is in the process of registring a character 'u' for Unicode locale
extensions.

The syntax of 'u' extension subtags is defined by the rule
`unicode_locale_extensions` in [Unicode locale
identifier](#Unicode_locale_identifier), except the separator of subtags `sep`
must be always hyphen '-' when the extension is used as a part of BCP 47
language tag. All subtags within the Unicode locale extension are alphanumeric
characters in length of two to eight that meet the rule `extension` in the
\[[BCP47](#BCP47)\] specification.

The complete list of Unicode locale extension subtags are defined by Appendix Q:
[Locale Extension Key and Type Data](#Locale_Extension_Key_and_Type_Data). These
subtags are all in lowercase (that is the canonnical casing for these subtags),
however, subtags are case-insensitive and casing does not carry any specific
meaning.

A 'u' extension may contain multiple `attribute`s or `keyword`s as defined in
[Unicode locale identifier](#Unicode_locale_identifier). Although the order
of`attribute`s or `keyword`s does not matter, this specification defines the
canonical form as below:

*   All attributes are sorted in alphabetical order.
*   All keywords are sorted by alphabetical order of keys.

For example, the canonical form of 'u' extension "u-foo-bar-nu-thai-ca-buddhist"
is "u-bar-foo-ca-buddhist-nu-thai". The attributes "foo" and "bar" in this
example are provided only for illustration; no attribute subtags are defined by
the current CLDR specification.

#### 3.2.2 BCP 47 Language Tag Conversion

A Unicode language/locale identifier can be converted to a valid \[[BCP
47](#BCP47)\] language tag by performing the following transformation.

1.  Replace the "_" separators with "-"
2.  Replace the special language identifier "root" with the BCP 47 primary
    language tag "und"

For example,`en_US` → `en-US`
`de_DE_u_co_phonebk` → `de-DE-u-co-phonebk`
`root` → `und`
`root_u_cu_usd` → `und-u-cu-usd`

A valid \[[BCP 47](#BCP47)\] language tag can be converted to a valid Unicode
language/locale identifier by performing the following transformation.

1.  Canonicalize the language tag (afterwards, there will be no extlang subtag)
2.  Replace the BCP 47 primary language subtag "und" with "root" if no script,
    region, or variant subtags are present
3.  If the BCP 47 primary language subtag matches the *type* attribute of a
    *languageAlias* element
    in[supplementalMetadata.xml](http://unicode.org/repos/cldr/trunk/common/supplemental/supplementalMetadata.xml),
    replace the language subtag with the *replacement* value.
4.  If the BCP 47 region subtag matches the *type* attribute of a
    *territoryAlias* element in
    [supplementalMetadata.xml](http://unicode.org/repos/cldr/trunk/common/supplemental/supplementalMetadata.xml),
    replace the language subtag with the *replacement* value. (When multiple
    *replacement* values are available, use the first one)

For example,`en-US` → `en-US` (no changes)
`und` → `root`
`und-US` → `und-US` (no changes, because region subtag is present)
`und-u-cu-USD` → `root-u-cu-usd`
`cmn-TW` → `zh-TW` (language alias)
`sr-CS` → `sr-RS` (territory alias)

**Note:** In some rare cases, BCP 47 language tags cannot be converted to valid
Unicode language/locale identifiers, such as certain \[[BCP 47](#BCP47)\]
grandfathered tags.

### 3.3 Relation to OpenI18n

The locale id format generally follows the description in the *OpenI18N Locale
Naming Guideline* \[[NamingGuideline](#NamingGuideline)\], with some
enhancements. The main differences from the those guidelines are that the locale
id:

1.  does not include a charset (since the data in LDML format always provides a
    representation of all Unicode characters. The repository is stored in UTF-8,
    although that can be transcoded to other encodings as well.),
2.  adds the ability to have a variant, as in Java
3.  adds the ability to discriminate the written language by script (or script
    variant).
4.  is a superset of \[[BCP47](#BCP47)\] codes.

### 3.4 Compatibility with Older Identifiers

LDML version before 1.7.2 used slightly different syntax for variant subtags and
locale extensions. Implementations of LDML may provide backward compatible
identifier support as described in following sections.

#### 3.4.1 Legacy Variants

Old LDML specification allowed codes other than registered \[[BCP47](#BCP47)\]
variant subtags used in Unicode language and locale identifiers for representing
variations of locale data. Unicode locale identifiers including such variant
codes can be converted to the new \[[BCP47](#BCP47)\] compatible identifiers by
following the descriptions below:

Legacy Variant MappingsVariant CodeDescriptionAALANDÅland, variant of "sv"
Swedish used in Finland. Use "sv_AX" to indicate this.BOKMALBokmål, variant of
"no" Norwegian. Use primary language subtag "nb" to indicate
this.NYNORSKNynorsk, variant of "no" Norwegian. Use primary language subtag "nn"
to indicate this.POSIXPOSIX variation of locale data. Use Unicode locale
extension "-u-va-posix" to indicate this.POLYTONIPolitonic, variant of "el"
Greek. Use \[[BCP47](#BCP47)\] variant subtag "polyton" to indicate
this.SAAHOThe Saaho variant of Afar. Use primary language subtag "ssy" to
indicated this.

#### 3.4.2 Old Locale Extension Syntax

LDML 1.7 or older specification used different syntax for representing unicode
locale extensions. The previous definition of Unicode locale extensions had the
following structure:

EBNF

ABNF

old_unicode_locale_extensions= "@" old_key "=" old_type (";" old_key "="
old_type)\*= "@" old_key "=" old_type \*(";" old_key "=" old_type)

The new specification mandates keys to be two alphanumeric characters and types
to be three to eight alphanumeric characters. As the result, new codes were
assigned to all existing keys and some types. For example, a new key "co"
replaced the previous key "collation", a new type "phonebk" replaced the
previous type "phonebook". However, the existing collation type "big5han"
already satisfied the new requirement, so no new type code was assigned to the
type. The chart below shows some example mappings between the new syntax and the
old syntax.

Locale Extension MappingsOld (LDML 1.7 or
older)Newde_DE@collation=phonebookde_DE_u_co_phonebkzh_Hant_TW@collation=big5hanzh_Hant_TW_u_co_big5hanth_TH@calendar=gregorian;@numbers=thaith_TH_u_ca_gregory_nu_thaien_US_POSIX@timezone=America/Los_Angelesen_US_u_tz_uslax_va_posix

For more information about the key/type definitions and their old code mappings,
see Appendix Q: [Locale Extension Key and Type
Data](#Locale_Extension_Key_and_Type_Data).

## 4. Locale Inheritance

The XML format relies on an inheritance model, whereby the resources are
collected into *bundles*, and the bundles organized into a tree. Data for the
many Spanish locales does not need to be duplicated across all of the countries
having Spanish as a national language. Instead, common data is collected in the
Spanish language locale, and territory locales only need to supply differences.
The parent of all of the language locales is a generic locale known as *root*.
Wherever possible, the resources in the root are language & territory neutral.
For example, the collation (sorting) order in the root is the default Unicode
Collation Algorithm order (see \[[UCA](#UCA)\]). Since English language
collation has the same ordering, the 'en' locale data does not need to supply
any collation data, nor does either the 'en_US' or the 'en_IE' locale data.

Given a particular locale id "en_IE_someVariant", the search chain for a
particular resource is the following.

en_IE_someVariant en_IE en root

If a type and key are supplied in the locale id, then logically the chain from
that id to the root is searched for a resource tag with a given type, all the
way up to root. If no resource is found with that tag and type, then the chain
is searched again without the type.

Thus the data for any given locale will only contain resources that are
different from the parent locale. For example, most territory locales will
inherit the bulk of their data from the language locale: "en" will contain the
bulk of the data: "en_IE" will only contain a few items like currency. All data
that is inherited from a parent is presumed to be valid, just as valid as if it
were physically present in the file. This provides for much smaller resource
bundles, and much simpler (and less error-prone) maintenance. At the script or
region level, the "primary" child locale will be empty, since its parent will
contain all of the appropriate resources for it. For more information see
*Appendix P.3 [Default Content](#Default_Content).*

If a language has more than one script in customary modern use, then the CLDR
file structure in common/main follows the following model:

lang
lang_script
lang_script_region
lang_region *(aliases to lang_script_region)*

There are actually two different kinds of fallback: resource bundle lookup and
resource item lookup. For the former, a process is looking to find the first,
best resource bundle it can; for the later, it is fallback within bundles on
individual items, like a the translated name for the region "CN" in Breton.
These are closely related, but distinct, processes. Below "key" stands for zero
or more key/type pairs.

Lookup Differences

Lookup Type

Example

Comments

Resource **bundle** lookup

se-FI → se
→ default\*
→ root

\* default may have its own inheritance change; for example, it may be "en-GB →
en" In that case, the chain is expanded by inserting the chain, resulting in:
se-FI → se
→ fi → en-GB → en
→ root

Resource **item** lookup

se-FI+key → se+key
→ root_alias\*+key → root+key

\* if there is a root_alias to another key or locale, then insert that entire
chain. For example, suppose that months for another calendar system have a root
alias to Gregorian months. In that case, the root alias would change the key,
and retry from se-FI downward.
se-FI+key → se+key
→ root_alias\*+key
→ se-FI+key2 → se+key2
→ root_alias\*+key2 → root+key2

The fallback is a bit different for these two cases; internal aliases and keys
are are not involved in the bundle lookup, and the default locale is not
involved in the item lookup. Moreover, the resource item lookup must remain
stable, because the resources are built with a certain fallback in mind;
changing the core fallback order can render the bundle structure incoherent.
Resource bundle lookup, on the other hand, is more flexible; changes in the view
of the "best" match between the input request and the output bundle are more
tolerant, when represent overall improvements for users. For more information,
see *[Section 5.3.1 Fallback_Elements](#Fallback_Elements)*.

Where the LDML inheritance relationship does not match a target system, such as
POSIX, the data logically should be fully resolved in converting to a format for
use by that system, by adding *all* inherited data to each locale data set.

For a more complete description of how inheritance applies to data, and the use
of keywords, see *[Appendix I: Inheritance and
Validity](#Inheritance_and_Validity)*.

The locale data does not contain general character properties that are derived
from the *Unicode Character Database*
\[[UCD](http://unicode.org/reports/tr41/#UAX44)\]. That data being common across
locales, it is not duplicated in the bundles. Constructing a POSIX locale from
the CLDR data requires use of UCD data. In addition, POSIX locales may also
specify the character encoding, which requires the data to be transformed into
that target encoding.

**Warning:** If a locale has a different script than its parent (for example,
sr_Latn), then special attention must be paid to make sure that all inheritance
is covered. For example, auxiliary exemplar characters may need to be empty
("\[\]") to block inheritance.

### 4.1 Multiple Inheritance

In clearly specified instances, resources may inherit from within the same
locale. For example, currency format symbols inherit from the number format
symbols; the Buddhist calendar inherits from the Gregorian calendar. This *only*
happens where documented in this specification. In these special cases, the
inheritance functions as normal, up to the root. If the data is not found along
that path, then a second search is made, logically changing the
element/attribute to the alternate values.

For example, for the locale "en_US" the month data in <calendar
class="buddhist"> inherits first from <calendar class="buddhist"> in "en", then
in "root". If not found there, then it inherits from <calendar type="gregorian">
in "en_US", then "en", then in "root".
