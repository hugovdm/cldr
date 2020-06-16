# CLDR 1.7 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases (Downloads)](index.md).

No. Date Rel. Note Data Spec Delta CVS Tag **1.7** **2009-05-08**
**[Version1.7](cldr-1-7.md)**
**[CLDR1.7](http://unicode.org/Public/cldr/1.7.0/)**
**[LDML1.7](http://www.unicode.org/reports/tr35/tr35-12.html)**
**[Changes1.7](http://www.unicode.org/cldr/bugs/locale-bugs/closed?expression=target.*1.7)**
**`release-1-7`**

***Note:** See also [Errata](http://cldr.unicode.org/errata).*

CLDR 1.7 contains data for 146 languages and 159 territories: 468 locales in
all. Version 1.7 of the repository contains over 21% more locale data than the
previous release, with over 40,000 new or modified data items from over 140
different contributors. Major contributors to CLDR 1.7 include Adobe, Apple,
Google, IBM, and Sun, plus official representatives from a number of countries.
Many other organizations and volunteers around the globe, including Gnome,
Kotoistus, LISA, OpenOffice, and Utilika, have also made important
contributions. The data for CLDR is gathered through the [CLDR Survey
Tool](http://cldr.unicode.org/index/survey-tool), which allows organizations and
volunteers to contribute, compare, and vet locale data. In the development of
this release, the process of gathering data was sped up, and the voting process
was simplified.

The new features of Unicode CLDR 1.7 include:

*   New and improved data, including Indic data.
*   Enhanced number system support, including many non-decimal formats as well
    as spelled-out forms ("twenty-three")
*   Postal code format validity
*   New IETF BCP 47 (RFC 4646) support
*   Calendar preference data
*   Improved language population data, and language-script mapping data
*   Local DTD access
*   Improved currency symbols
*   Clarified specification of timezone parsing

Unicode CLDR 1.7 is part of the Unicode locale data project, together with the
Unicode Locale Data Markup Language (LDML: <http://unicode.org/reports/tr35/>).
LDML is an XML format used for general interchange of locale data, such as in
Microsoft's .NET. For web pages with different views of CLDR data, see
<http://cldr.unicode.org/index/charts>.

### List of Languages and Territories in this Release

**Languages:** Afar \[Qafar\]; Afrikaans; Akan \[ak\]; Albanian \[shqipe\];
Amharic \[አማርኛ\]; Arabic \[‎العربية‎\]; Armenian \[Հայերէն\]; Assamese
\[অসমীয়া\]; Atsam \[cch\]; Azerbaijani (Cyrillic) \[Азәрбајҹан (kiril)\];
Azerbaijani (Latin) \[azərbaycanca (latın)\]; Basque \[euskara\]; Belarusian
\[беларуская\]; Bengali \[বাংলা\]; Blin \[ብሊን\]; Bosnian \[Bosanski\]; Bulgarian
\[български\]; Burmese \[ဗမာ\]; Catalan \[català\]; Coptic \[cop\]; Cornish
\[kernewek\]; Croatian \[hrvatski\]; Czech \[čeština\]; Danish \[dansk\]; Divehi
\[‎ދިވެހިބަސް‎\]; Dutch \[Nederlands\]; Dzongkha \[རྫོང་ཁ\]; English (Deseret)
\[𐐀𐑍𐑊𐐮𐑇 (𐐔𐐯𐑆𐐲𐑉𐐯𐐻)\]; English (Shavian); Esperanto; Estonian \[eesti\]; Ewe
\[ee\]; Faroese \[føroyskt\]; Filipino; Finnish \[suomi\]; French \[français\];
Friulian \[furlan\]; Ga \[gaa\]; Galician \[galego\]; Geez \[ግዕዝኛ\]; Georgian
\[ქართული\]; German \[Deutsch\]; Greek \[Ελληνικά\]; Gujarati \[ગુજરાતી\]; Hausa
(Arabic) \[Haoussa (Arab)\]; Hausa (Latin) \[Haoussa (Latn)\]; Hawaiian \[ʻōlelo
Hawaiʻi\]; Hebrew \[‎עברית‎\]; Hindi \[हिन्दी\]; Hungarian \[magyar\]; Icelandic
\[íslenska\]; Igbo \[ig\]; Indonesian \[Bahasa Indonesia\]; Interlingua;
Inuktitut \[ᐃᓄᒃᑎᑐᑦ ᑎᑎᕋᐅᓯᖅ\]; Irish \[Gaeilge\]; Italian \[italiano\]; Japanese
\[日本語\]; Jju \[kaj\]; Kalaallisut; Kamba \[kam\]; Kannada \[ಕನ್ನಡ\]; Kazakh
(Cyrillic) \[Қазақ (Cyrl)\]; Khmer \[ភាសាខ្មែរ\]; Kinyarwanda \[rw\]; Kirghiz
\[Кыргыз\]; Konkani \[कोंकणी\]; Korean \[한국어\]; Koro \[kfo\]; Kpelle \[kpe\];
Kurdish (Arabic) \[‎كوردی (Arab)‎\]; Kurdish (Latin) \[kurdî (Latn)\]; Lao
\[ລາວ\]; Latvian \[latviešu\]; Lingala \[lingála\]; Lithuanian \[lietuvių\]; Low
German \[Plattdüütsch\]; Macedonian \[македонски\]; Malay \[Bahasa Melayu\];
Malayalam \[മലയാളം\]; Maltese \[Malti\]; Manx \[Gaelg\]; Marathi \[मराठी\];
Mongolian (Cyrillic) \[монгол (Cyrl)\]; Mongolian (Mongolian) \[монгол (Mong)\];
Nepali \[नेपाली\]; Northern Sami \[davvisámegiella\]; Northern Sotho \[Sesotho
sa Leboa\]; Norwegian \[norsk\]; Norwegian Bokmål \[norsk bokmål\]; Norwegian
Nynorsk \[nynorsk\]; Nyanja \[ny\]; Occitan; Oriya \[ଓଡ଼ିଆ\]; Oromo \[Oromoo\];
Pashto \[‎پښتو‎\]; Persian \[‎فارسی‎\]; Polish \[polski\]; Portuguese
\[português\]; Punjabi (Arabic) \[‎پنجاب (العربية)‎\]; Punjabi (Gurmukhi)
\[ਪੰਜਾਬੀ (ਗੁਰਮੁਖੀ)\]; Romanian \[română\]; Russian \[русский\]; Sanskrit
\[संस्कृत भाषा\]; Serbian (Cyrillic) \[Српски (Ћирилица)\]; Serbian (Latin)
\[Srpski (Latinica)\]; Sichuan Yi \[ꆈꌠꉙ\]; Sidamo \[Sidaamu Afo\]; Simplified
Chinese \[中文（简体）\]; Sinhala \[සිංහල\]; Slovak \[slovenčina\]; Slovenian
\[slovenščina\]; Somali \[Soomaali\]; South Ndebele \[isiNdebele\]; Southern
Sotho \[Sesotho\]; Spanish \[español\]; Swahili \[Kiswahili\]; Swati
\[Siswati\]; Swedish \[svenska\]; Swiss German \[Schwiizertüütsch\]; Syriac
\[‎ܣܘܪܝܝܐ‎\]; Tagalog; Tajik (Cyrillic) \[tg (Cyrl)\]; Tamil \[தமிழ்\]; Tatar
\[Татар\]; Telugu \[తెలుగు\]; Thai \[ไทย\]; Tibetan \[པོད་སྐད་\]; Tigre \[ትግረ\];
Tigrinya \[ትግርኛ\]; Tonga \[lea fakatonga\]; Traditional Chinese \[繁體中文\]; Tsonga
\[Xitsonga\]; Tswana \[Setswana\]; Turkish \[Türkçe\]; Tyap \[kcg\]; Uighur
(Arabic) \[ug (Arab)\]; Ukrainian \[українська\]; Urdu \[‎اردو‎\]; Uzbek
(Arabic) \[‎اۉزبېک (Араб)‎\]; Uzbek (Cyrillic) \[Ўзбек (Кирил)\]; Uzbek (Latin)
\[o'zbekcha (Lotin)\]; Venda \[Tshivenḓa\]; Vietnamese \[Tiếng Việt\]; Walamo
\[ወላይታቱ\]; Welsh \[Cymraeg\]; Wolof (Latin) \[wo (Latn)\]; Xhosa \[isiXhosa\];
Yoruba \[Yorùbá\]; Zulu \[isiZulu\]

**Territories:** Afghanistan \[‎افغانستان‎\]; Albania \[Shqipëria\]; Algeria
\[‎الجزائر‎\]; Argentina; Armenia \[Հայաստանի Հանրապետութիւն\]; Austria
\[Österreich\]; Azerbaijan \[Azərbaycan, Азәрбајҹан\]; Bahrain \[‎البحرين‎\];
Bangladesh \[বাংলাদেশ\]; Belarus \[Беларусь\]; Belgium \[België, Belgien,
Belgique\]; Bhutan \[འབྲུག\]; Bolivia; Bosnia and Herzegovina \[Bosna i
Hercegovina, Босна и Херцеговина\]; Brazil \[Brasil\]; Brunei; Bulgaria
\[България\]; Cambodia \[កម្ពុជា\]; Canada; Chile; China \[CN, རྒྱ་ནག, ꍏꇩ, 中国\];
Colombia; Congo - Brazzaville \[Kongó-Brazzaville\]; Congo - Kinshasa
\[Kongó-Kinsásá\]; Costa Rica; Côte d’Ivoire \[CI\]; Croatia \[Hrvatska\];
Cyprus \[Κύπρος\]; Czech Republic \[Česká republika\]; Denmark \[Danmark\];
Djibouti \[Jabuuti, Yabuuti\]; Dominican Republic \[República Dominicana\];
Ecuador; Egypt \[‎مصر‎\]; El Salvador; Eritrea \[Eretria, ኤርትራ\]; Estonia
\[Eesti\]; Ethiopia \[Itiyoophiya, Itoobiya, Itoophiyaa, Otobbia, ኢትዮጵያ\]; Faroe
Islands \[Føroyar\]; Finland \[FI, Suomi\]; France \[França\]; Georgia
\[საქართველო\]; Germany \[Deutschland, Düütschland\]; Ghana \[Gaana, GH\];
Greece \[Ελλάδα\]; Greenland \[Kalaallit Nunaat\]; Guatemala; Guinea \[GN\];
Honduras; Hong Kong SAR China \[中国香港特别行政区, 中華人民共和國香港特別行政區\]; Hungary
\[Magyarország\]; Iceland \[Ísland\]; India \[‎بھارت‎, भारत, भारतम्, ভারত, ভাৰত,
ਭਾਰਤ, ભારત, ଭାରତ, இந்தியா, భారత దేశం, ಭಾರತ, ഇന്ത്യ, རྒྱ་གར་\]; Indonesia; Iran
\[IR, ‎ایران‎\]; Iraq \[IQ, ‎العراق‎\]; Ireland \[Éire\]; Israel \[‎ישראל‎\];
Italy \[Italia, Italie\]; Japan \[日本\]; Jordan \[‎الأردن‎\]; Kazakhstan
\[Қазақстан\]; Kenya \[KE, Keeniyaa, Kiiniya\]; Kuwait \[‎الكويت‎\]; Kyrgyzstan
\[Кыргызстан\]; Laos \[ລາວ\]; Latvia \[Latvija\]; Lebanon \[‎لبنان‎\]; Lesotho
\[LS\]; Liberia \[LR\]; Libya \[‎ليبيا‎\]; Liechtenstein; Lithuania \[Lietuva\];
Luxembourg \[Luxemburg\]; Macau SAR China \[中国澳门特别行政区, 中華人民共和國澳門特別行政區\];
Macedonia \[Македонија\]; Malawi \[MW\]; Malaysia; Maldives \[‎ދިވެހި ރާއްޖެ‎\];
Malta; Mexico \[México\]; Moldova \[Republica Moldova\]; Monaco; Mongolia
\[Монгол улс\]; Montenegro \[Crna Gora, Црна Гора\]; Morocco \[‎المغرب‎\];
Myanmar \[Burma\] \[မြန်မာ\]; Namibia \[Namibië\]; Nepal \[नेपाल\]; Netherlands
\[Nederland\]; Nicaragua; Niger \[Nijer\]; Nigeria \[NG, Nijeriya\]; Norway
\[Noreg, Norga, Norge\]; Oman \[‎عمان‎\]; Pakistan \[‎پاکستان‎, ‎پکستان‎\];
Panama \[Panamá\]; Paraguay; Peru \[Perú\]; Philippines \[Pilipinas\]; Poland
\[Polska\]; Portugal; Puerto Rico; Qatar \[‎قطر‎\]; Romania \[România\]; Russia
\[Россия\]; Rwanda \[RW\]; Saudi Arabia \[‎المملكة العربية السعودية‎\]; Senegal
\[Sénégal, SN\]; Serbia \[Srbija, Србија\]; Singapore \[新加坡\]; Slovakia
\[Slovenská republika\]; Slovenia \[Slovenija\]; Somalia \[Soomaaliya\]; South
Africa \[iNingizimu Afrika, Suid-Afrika, ZA\]; South Korea \[대한민국\]; Spain
\[Espainia, España, Espanya\]; Sri Lanka \[ශ්‍රී ලංකාව\]; Sudan \[SD,
‎السودان‎\]; Swaziland \[SZ\]; Sweden \[Sverige\]; Switzerland \[Schweiz,
Schwiiz, Suisse, Svizzera\]; Syria \[SY, ‎سوريا‎, ‎ܣܘܪܝܝܐ‎\]; Taiwan \[台灣\];
Tajikistan \[TJ\]; Tanzania; Thailand \[ไทย\]; Togo \[TG\]; Tonga; Tunisia
\[‎تونس‎\]; Turkey \[Tirkiye, Türkiye\]; Ukraine \[Украина, Україна\]; United
Arab Emirates \[‎الامارات العربية المتحدة‎\]; United Kingdom \[Prydain Fawr,
Rywvaneth Unys\]; United States \[Estados Unidos, ʻAmelika Hui Pū ʻIa, 𐐏𐐭𐑌𐐴𐐻𐐲𐐼
𐐝𐐻𐐩𐐻𐑅\]; Uruguay; Uzbekistan \[Oʿzbekiston, Ўзбекистон\]; Venezuela; Vietnam
\[Việt Nam\]; Yemen \[‎اليمن‎\]

**Notes:**

*   The amount of data per locale and the status (*unconfirmed*, *provisional*,
    *contributed*, or *approved*) varies.
*   Tooltips will show the ISO code and Latin transliteration if available.
    (To set your tooltip font in IE, right click on the desktop, pick Properties
    > Appearance > Advanced > Item: ToolTip, then set the font to Arial Unicode
    MS or other large font.)
*   If the above doesn't display in your browser, see [Display
    Problems?](http://www.unicode.org/help/display_problems.html)

The Unicode [Terms of Use](http://unicode.org/copyright.html) apply to this
data; in particular, see [Exhibit
1](http://unicode.org/copyright.html#Exhibit1).
