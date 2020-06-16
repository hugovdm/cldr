# Unicode Locales and CLDR

#### Q. What are Unicode Locales?

A. The Unicode Locale project provides an XML data format (LDML) for
representing locale data, plus a repository of data in that format (CLDR). For
more             information, see <http://unicode.org/cldr/>.

#### Q. What products use Unicode Locales?

A. We don't track the users, but we know that the data and format are used
directly by IBM's AIX, Google, ICU, Java, and OpenOffice, while Microsoft uses
the format.              There are many indirect users as well. For example,
through using ICU many other companies              and organizations are using
Unicode Locales, including: Adobe, Apple (Mac OS X), Apache,                BEA,
Boost, Business Objects, CERN, Debian Linux, Eclipse, eBay, Free BSD, Gentoo
Linux,                Google, HP, Hyperion, Inktomi, Intel, Mozilla, Mandrake
Linux, Progress Software, Python,               SAP, Software AG, Sun
Microsystems (Solaris, Java), SuSE, Sybase, Symantec, Teradata (NCR), Ubuntu
Linux,               Virage, Wine, Yahoo! (see <http://icu-project.org/>)

Wikimedia is also using the data in its Translate extension
<http://www.mediawiki.org/wiki/Extension:Translate> and Translate Wiki project
<http://translatewiki.net/>.

*If you know of other direct or indirect users that would be useful to add to
this list, let us know by [filing a
report](http://www.unicode.org/cldr/bugs/locale-bugs).*

#### Q. What is the difference between a locale 		and a language?

A. The distinction in practice is very fuzzy. A locale is best thought of as
being a language plus some additional information. For more information, see
[What is a Locale?](http://www.unicode.org/reports/tr35/#Locale) and
[Language and Locale
IDs](http://www.unicode.org/reports/tr35/#Language_and_Locale_IDs).

#### Q. Does Unicode CLDR define special 		values used to indicate an Unknown value for language, script, region (country/territory), 		timezone, and currency?

A. Yes, see the table at                [
Unknown_or_Invalid_Identifiers](http://www.unicode.org/reports/tr35/#Unknown_or_Invalid_Identifiers)
in UTR#35.

#### Q. Are these in the source standards used by 		CLDR?

A. Some of them are, and some use private use codes defined by          CLDR.
For more information, see                 [
Identifiers](http://www.unicode.org/reports/tr35/#Identifiers) in UTR#35.

#### Q. Why is the Unknown value for script "Zzzz" and not "Zyyy"?

A. The [IANA            registry for BCP
47](http://www.iana.org/assignments/language-subtag-registry) includes these
special values for scripts:

Type: script
Subtag: Zyyy
Description: Code for undetermined script
Added: 2005-10-16
%%
Type: script
Subtag: Zzzz
Description: Code for uncoded script
Added: 2005-10-16

However, in the Unicode Standard, Zyyy marks characters that are common across
a number of scripts (like 1,2,3, . ; ? and so on). Because of that, in a Unicode
context it             is viewed as being more like "in multiple scripts", and
not really appropriate for locales.
Zzzz marks reserved characters which may end up becoming any script once encoded
(see           [Values](http://www.unicode.org/reports/tr24/#Values) in UTR#24).
It is also the                value used for Unknown script in CLDR. In
practice, it is rare to know the language without             the script
(en-Zzzz would be an odd case, for example), so this is used mostly for API
return values.

#### Q. But what would I use for an audio tape in English?

A. The code Zxxx is for unwritten (eg, spoken) material. Thus en-Zxxx could be
used for an audio tape, if you wanted to make clear that there was no written
English           content.

#### Q. What capitalization rule 		 would I use when translating display names?

A. Many LDML elements are display names. Display names describe languages,
scripts, countries, variants, units, and many other items. It is a translated
name for use in user-interfaces for displaying lists. The translator should
adopt the capitalization rules for menu lists, appropriate for the target
language.

Currencies may also have a display name. With the introduction of pluralized
units, it is recognized that currencies may also be used in user-interfaces with
flowing text.          For currency names, the translator may adopt a
capitalization rule suitable for use in both menu                lists and
flowing text, although we recognize, there may be limitations with this
strategy,             at this time.

---

![Access to Copyright and terms of use
](http://www.unicode.org/copyright.html){width="216" height="50"}
