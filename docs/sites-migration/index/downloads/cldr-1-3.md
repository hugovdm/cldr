# CLDR 1.3 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases
(Downloads)](http://unicode.org/cldr/data/docs/web/repository_access.html). *In
terms of license, the Unicode                   [Terms of
Use](http://unicode.org/copyright.html) apply; in particular,
[Exhibit 1](http://unicode.org/copyright.html#Exhibit1).*

No. Date Rel. Note Data Spec Delta CVS Tag **1.3**
**[2005-06-02](http://unicode.org/Public/cldr/1.3.0/)**
**[Version1.3](http://unicode.org/cldr/data/docs/web/version/1.3.html)**
**[CLDR1.3](http://unicode.org/Public/cldr/1.3.0/)**
**[LDML1.3](http://www.unicode.org/reports/tr35/tr35-5.html)** **[
Changes1.3](http://www.unicode.org/cldr/bugs/locale-bugs/closed?expression=target.*1.3)**
**`release-1-3`**

CLDR Version 1.3 contains contains data for 296 locales: 96 languages and 130
territories. In this release, the major additions to CLDR are:

*   A complete set of POSIX-format data generated from the XML format, plus a
    tool to generate versions for different platforms.
*   The addition of new data to support localization of timezones
*   The addition of data for UN M.49 regions, including continents and region.
*   The canonicalization of the data files, including the consolidation of
    inherited data
*   The restriction of currency codes to ISO 4217 codes (past and present)
*   The addition of number and data tests, for verifying that implementations
    correctly implement the LDML specification using CLDR data.
*   The addition of metadata for LDML
*   The addition of mappings from language to script and territory
*   Various other fixes and additions of data, and extensions to the
    specification.

## Corrigendum 1: Time zone and Date Format Pattern Correction

In CLDR version 1.3, the policy was that for a given (resolved) locale,
uniqueness is required for time zone display names. That is, two different time
zone IDs could not have the same display name. This policy turns out to be
overly strict, and did not allow for customary names in cases where it does not
cause a problem. The committee has relaxed this policy so that where the parsing
results would give the same GMT offset, the standard and daylight display names
can be the same across different time zone IDs.

The short and long time zone names for Europe/London and Europe/Dublin in the
**`en.xml`** locale data file had been changed because of the old policy. In
accordance with this new policy, they are corrected by this corrigendum as
follows:

`<zone type="Europe/London">` CLDR 1.3 Corrected
` <long>`
` <generic>British Time</generic> `
` <standard>British Standard Time</standard> `
` <daylight>British Daylight Time</daylight> `
` </long>`
` <short>`
` <generic>BT</generic> `
` <standard>BST</standard> `
` <daylight>BDT</daylight> `
` </short>`
`<zone type="Europe/London">`` </zone>`
` <long>`
` <standard>Greenwich Mean Time</standard> `
` <daylight>British Summer Time</daylight> `
` </long>`
` <short>`
` <standard>GMT</standard> `
` <daylight>BST</daylight> `
` </short>`
` </zone>`

*{omitted}*

`<zone type="Europe/Dublin">`
` <long>`
` <standard>Greenwich Mean Time</standard> `
` <daylight>Irish Summer Time</daylight> `
` </long>`
` <short>`
` <standard>GMT</standard> `
` <daylight>IST</daylight> `
` </short>`
` </zone> `

The data reflecting the above correction is checked into CVS under the tag
**`release-1-3-C1`**. For information on the usage of this, see [CLDR Releases
(Downloads)](http://unicode.org/cldr/repository_access.html).

The following are corrections to the date format pattern in [UTS #35: Locale
Data Markup Language (LDML)](http://www.unicode.org/reports/tr35/). The
Stand-Alone months and days, and the long era names, although approved by the
technical committee, had been omitted from the specification. The use of
specific sequences of 'z', 'Z', and 'E' is changed to preserve backwards
compatibility with Java.

CLDR 1.3 Corrected era G 1..3 AD Era - Replaced with the Era string for the
current date. era G 1..3 AD Era - Replaced with the Era string for the current
date. One to three letters for the abbreviated form, four letters for the long
form. 4 Anno Domini month M 1..2 09 Month - Use one or two for the numerical
month, three for the abbreviation, or four for the full name, or 5 for the
narrow name. 3 Sept 4 September 5 S month M 1..2 09 Month - Use one or two for
the numerical month, three for the abbreviation, or four for the full name, or
five for the narrow name. 3 Sept 4 September 5 S L 1..2 09 **Stand-Alone** Month
- Use one or two for the numerical month, three for the abbreviation, or four
for the full name, or 5 for the narrow name. 3 Sept 4 September 5 S week
day E 1..2 3 Day of week - Use three for the short day, or four for the full
name, or 5 for the narrow name. Sunday is always day 1 3 Tues 4 Tuesday 5 T e
1..2 2 Local day of week. Same as E except numeric value will depend on the
local starting day of the week. For this example, Monday is the first day of the
week. 3 Tues 4 Tuesday 5 T week
day E 1..3 Tues Day of week - Use one through three letters for the short day,
or four for the full name, or five for the narrow name. 4 Tuesday 5 T e 1..2 2
Local day of week. Same as E exceptadds a numeric value that will depend on the
local starting day of the week, using one or two letters. For this example,
Monday is the first day of the week. 3 Tues 4 Tuesday 5 T c 1 2 **Stand-Alone**
local day of week - Use one letter for the local numeric value (same as 'e'),
three for the short day, or four for the full name, or five for the narrow name.
3 Tues 4 Tuesday 5 T zone z 1 PT Time zone. Use 1 for short wall (generic) time,
2 for long wall time, 3 for the short time zone (i.e. PST) or 4 for the full
name (Pacific Standard Time). If there's no name for the zone, fallbacks may be
used, depending on available data. 2 Pacific Time 3 PDT 4 Pacific Daylight Time
Z 1 GMT-08:00 Use 1 for GMT format, 2 for RFC 822 2 -0800 zone z 1..3 PDT Time
zone - Use one to three letters for the short time zone or four for the full
name. For more information, see Appendix J: [Time Zone
Fallback](http://unicode.org/cldr/corrigenda.html#Time_Zone_Fallback) 4 Pacific
Daylight Time Z 1..3 -0800 Use one to three letters for RFC 822, four letters
for GMT format. 4 GMT-08:00 v 1 PT Use one letter for short wall (generic) time,
four for long wall time. For more information, see Appendix J: [Time Zone
Fallback](http://unicode.org/cldr/corrigenda.html#Time_Zone_Fallback) 4 Pacific
Time

### List of Languages and Territories in this Release

**Languages (96):** Afar \[Qafar\]; Afrikaans; Albanian \[shqipe\]; Amharic
\[አማርኛ\]; Arabic \[‎العربية‎\]; Armenian \[Հայերէն\]; Assamese \[অসমীয়া\];
Azerbaijani - Cyrillic \[Азәрбајҹан - Cyrl\]; Azerbaijani - Latin \[azərbaycanca
- Latn\]; Basque \[euskara\]; Belarusian \[Беларускі\]; Bengali \[বাংলা\]; Blin
\[ብሊን\]; Bosnian \[Bosanski\]; Bulgarian \[Български\]; Catalan \[català\];
Chinese - Simplified Han \[中文 - 简体汉语\]; Chinese - Traditional Han \[中文 - 繁體漢語\];
Cornish \[kernewek\]; Croatian \[hrvatski\]; Czech \[Čeština\]; Danish
\[Dansk\]; Divehi \[‎ދިވެހިބަސް‎\]; Dutch \[Nederlands\]; Dzongkha \[རྫོང་ཁ\];
English; Esperanto; Estonian \[Eesti\]; Faroese \[føroyskt\]; Finnish \[suomi\];
French \[français\]; Gallegan \[galego\]; Geez \[ግዕዝኛ\]; Georgian \[ქართული\];
German \[Deutsch\]; Greek \[Ελληνικά\]; Gujarati \[ગુજરાતી\]; Hawaiian \[ʻōlelo
Hawaiʻi\]; Hebrew \[‎עברית‎\]; Hindi \[हिंदी\]; Hungarian \[magyar\]; Icelandic
\[Íslenska\]; Indonesian \[Bahasa Indonesia\]; Inuktitut \[ᐃᓄᒃᑎᑐᑦ ᑎᑎᕋᐅᓯᖅ\];
Irish \[Gaeilge\]; Italian \[italiano\]; Japanese \[日本語\]; Kalaallisut; Kannada
\[ಕನ್ನಡ\]; Kazakh \[Қазақ\]; Khmer \[ភាសាខ្មែរ\]; Kirghiz \[Кыргыз\]; Konkani
\[कोंकणी\]; Korean \[한국어\]; Lao \[ລາວ\]; Latvian \[latviešu\]; Lithuanian
\[Lietuvių\]; Macedonian \[македонски\]; Malay \[Bahasa Melayu\]; Malayalam
\[മലയാളം\]; Maltese \[Malti\]; Manx \[Gaelg\]; Marathi \[मराठी\]; Mongolian
\[Монгол хэл\]; Norwegian Bokmål \[norsk bokmål\]; Norwegian Nynorsk \[norsk
nynorsk\]; Oriya \[ଓଡ଼ିଆ\]; Oromo \[Oromoo\]; Pashto (Pushto) \[‎پښتو‎\]; Persian
\[‎فارسی‎\]; Polish \[polski\]; Portuguese \[português\]; Punjabi \[ਪੰਜਾਬੀ\];
Romanian \[Română\]; Russian \[русский\]; Sanskrit \[संस्कृत\]; Serbian -
Cyrillic \[Српски - Ћирилица\]; Serbian - Latin \[Srpski - Latinica\]; Sidamo
\[Sidaamu Afo\]; Slovak \[slovenský\]; Slovenian \[Slovenščina\]; Somali
\[Soomaali\]; Spanish \[español\]; Swahili \[Kiswahili\]; Swedish \[svenska\];
Syriac \[‎ܣܘܪܝܝܐ‎\]; Tamil \[தமிழ்\]; Tatar \[Татар\]; Telugu \[తెలుగు\]; Thai
\[ไทย\]; Tigre \[ትግረ\]; Tigrinya \[ትግርኛ\]; Turkish \[Türkçe\]; Ukrainian
\[Українська\]; Urdu \[‎اردو‎\]; Uzbek - Arabic \[‎اۉزبېک - Араб‎\]; Uzbek -
Cyrillic \[Ўзбек - Кирил\]; Uzbek - Latin \[oʿzbek - Lotin\]; Vietnamese \[Tiếng
Việt\]; Walamo \[ወላይታቱ\]; Welsh \[Cymraeg\]

**Territories (130):** Afghanistan \[‎افغانستان‎\]; Albania \[Shqipëria\];
Algeria \[‎الجزائر‎\]; American Samoa; Argentina; Armenia \[Հայաստանի
Հանրապետութիւն\]; Australia; Austria \[Österreich\]; Azerbaijan \[Azərbaycan,
Азәрбајҹан\]; Bahrain \[‎البحرين‎\]; Belarus \[Беларусь\]; Belgium \[België,
Belgien, Belgique\]; Belize; Bhutan \[འབྲུག\]; Bolivia; Bosnia and Herzegovina
\[Bosna i Hercegovina, Босна и Херцеговина\]; Botswana; Brazil \[Brasil\];
Brunei; Bulgaria \[България\]; Cambodia \[កម្ពុជា\]; Canada; Chile; China
\[中国\]; Colombia; Costa Rica; Croatia \[Hrvatska\]; Cyprus \[Κύπρος\]; Czech
Republic \[Česká republika\]; Denmark \[Danmark\]; Djibouti \[Jabuuti,
Yabuuti\]; Dominican Republic \[República Dominicana\]; Ecuador; Egypt
\[‎مصر‎\]; El Salvador; Eritrea \[Eretria, ኤርትራ\]; Estonia \[Eesti\]; Ethiopia
\[Itiyoophiya, Itoobiya, Itoophiyaa, Otobbia, ኢትዮጵያ\]; Faroe Islands
\[Føroyar\]; Finland \[Suomi\]; France; Georgia \[საქართველო\]; Germany
\[Deutschland\]; Greece \[Ελλάδα\]; Greenland \[Kalaallit Nunaat\]; Guam;
Guatemala; Honduras; Hong Kong S.A.R. China \[中華人民共和國香港特別行政區\]; Hungary
\[Magyarország\]; Iceland \[Ísland\]; India \[‎الهند‎, भारत, भारतम्, ভারত, ভাৰত,
ਭਾਰਤ, ભારત, ଭାରତ, இந்தியா, భారత దేళ౦, ಭಾರತ, ഇന്ത്യ\]; Indonesia; Iran
\[‎ایران‎\]; Iraq \[‎العراق‎\]; Ireland \[Éire\]; Israel \[‎ישראל‎\]; Italy
\[Italia\]; Jamaica; Japan \[日本\]; Jordan \[‎الاردن‎\]; Kazakhstan
\[Қазақстан\]; Kenya \[Keeniyaa, Kiiniya\]; Kuwait \[‎الكويت‎\]; Kyrgyzstan
\[Кыргызстан\]; Laos \[ລາວ\]; Latvia \[Latvija\]; Lebanon \[‎لبنان‎\]; Libya
\[‎ليبيا‎\]; Liechtenstein; Lithuania \[Lietuva\]; Luxembourg \[Luxemburg\];
Macao S.A.R. China \[澳門特別行政區\]; Macedonia \[Македонија\]; Malaysia; Maldives
\[‎ދިވެހި ރާއްޖެ‎\]; Malta; Marshall Islands; Mexico \[México\]; Monaco;
Mongolia \[Монгол улс\]; Morocco \[‎المغرب‎\]; Netherlands \[Nederland\]; New
Zealand; Nicaragua; Northern Mariana Islands; Norway \[Noreg, Norge\]; Oman
\[‎عمان‎\]; Pakistan \[‎پاکستان‎\]; Panama \[Panamá\]; Paraguay; Peru \[Perú\];
Philippines; Poland \[Polska\]; Portugal; Puerto Rico; Qatar \[‎قطر‎\]; Romania
\[România\]; Russia \[Россия\]; Saudi Arabia \[‎العربية السعودية‎\]; Serbia And
Montenegro \[Srbija i Crna Gora, Србија и Црна Гора\]; Singapore \[新加坡\];
Slovakia \[Slovenská republika\]; Slovenia \[Slovenija\]; Somalia
\[Soomaaliya\]; South Africa \[Suid-Afrika\]; South Korea \[대한민국\]; Spain
\[Espainia, España, Espanya\]; Sudan \[‎السودان‎\]; Sweden \[Sverige\];
Switzerland \[Schweiz, Suisse, Svizzera\]; Syria \[‎سورية‎, ‎ܣܘܪܝܝܐ‎\]; Taiwan
\[臺灣\]; Tanzania; Thailand \[ประเทศไทย\]; Trinidad and Tobago; Tunisia
\[‎تونس‎\]; Turkey \[Türkiye\]; U.S. Virgin Islands; Ukraine \[Украина,
Україна\]; United Arab Emirates \[‎الامارات العربية المتحدة‎\]; United Kingdom
\[Prydain Fawr, Rywvaneth Unys\]; United States \[Estados Unidos, ʻAmelika Hui
Pū ʻIa\]; United States Minor Outlying Islands; Uruguay; Uzbekistan
\[Oʿzbekiston, Ўзбекистон\]; Venezuela; Vietnam \[Việt Nam\]; Yemen \[‎اليمن‎\];
Zimbabwe

**Notes:**

*   The amount of data per locale and the status (draft or vetted) varies.
*   Tooltips will show the ISO code and Latin transliteration if available.
    (To set your tooltip font in IE, right click on the desktop, pick
    Properties>Appearance>Advanced>Item: ToolTip, then set the font to Arial
    Unicode MS or other large font.)
*   If the above doesn't display in your browser, see [Display
    Problems?](http://www.unicode.org/help/display_problems.html)
