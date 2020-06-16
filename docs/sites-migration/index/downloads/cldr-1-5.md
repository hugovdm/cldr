# CLDR 1.5 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases
(Downloads)](http://unicode.org/cldr/data/docs/web/repository_access.html). *In
terms of license, the Unicode                   [Terms of
Use](http://unicode.org/copyright.html) apply; in particular,
[Exhibit 1](http://unicode.org/copyright.html#Exhibit1).*

No. Date Rel. Note Data Spec Delta CVS Tag **1.5** **2007-07-31**
**[Version1.5](http://unicode.org/cldr/data/docs/web/version/1.5.html)**
**[CLDR1.5](http://unicode.org/Public/cldr/1.5.0/)**
**[LDML1.5](http://www.unicode.org/reports/tr35/tr35-8.html)**
**[Changes1.5](http://www.unicode.org/cldr/bugs/locale-bugs/closed?expression=target.*1.5)**
**`release-1-5`**

***Note:** the test and tools directories, and some of the charts,
will be updated in stages. See also
[Errata](http://unicode.org/cldr/data/docs/web/errata.html).*

CLDR 1.5 contains data for                      135 languages and 149
territories: 394 locales in all. Version 1.5                      of the
repository contains over 42% more locale data than the
previous release, with over 27,000 new or modified data items
entered by over 160 different contributors. New to this release are also
BGN transliterations. Major contributors to                     CLDR 1.5 include
Adobe, Apple, Google, IBM, and Sun, plus official
representatives from a number of countries. Many other organizations
and volunteers around the globe have also made important
contributions.

Unicode CLDR 1.5 is part of the Unicode locale data project,
together with Unicode Locale Data                       Markup Language
**(Unicode LDML 1.5)**. LDML is an XML format used for general interchange of
locale data, such as                      in Microsoft's .NET. Major features of
Unicode LDML 1.5 include                         new conformance clauses,
commonly used time zone translations, revisions                        for
handling bidirectional text (Arabic and Hebrew), language fallbacks, revisions
for character fallbacks (used for legacy                     character
encodings),                   mappings to related language and country codes,
and substantial data on language and                    script usage in
different countries.

The data for CLDR is gathered through the *CLDR survey tool*, which allows
organizations and volunteers to                      contribute locale data.
Major improvements to the tool include: enhancements of the
appearance, layout, and operation, substantial new
documentation, improved testing, new levels of approval and corresponding
changes to the                        voting process for lesser-known languages,
and translator forums (and rss).

### List of Languages and Territories in this Release

**Languages (135):** Afar \[Qafar\];                    Afrikaans; Akan \[ak\];
Albanian \[shqipe\];                    Amharic \[አማርኛ\]; Arabic \[‎العربية‎\];
Armenian \[Հայերէն\];                   Assamese \[অসমীয়া\]; Atsam \[cch\];
Azerbaijani (Cyrillic) \[Азәрбајҹан (Cyrl)\]; Azerbaijani
(Latin) \[azərbaycanca (Latn)\]; Basque \[euskara\];
Belarusian \[беларуская\];                      Bengali \[বাংলা\]; Blin \[ብሊን\];
Bosnian \[Bosanski\];                  Bulgarian \[български\]; Burmese
\[my\]; Catalan \[català\]; Coptic                      (Arabic) \[cop (Arab)\];
Cornish \[kernewek\];                  Croatian \[hrvatski\]; Czech \[čeština\];
Danish \[dansk\]; Divehi \[‎ދިވެހިބަސް‎\];                      Dutch
\[Nederlands\]; Dzongkha \[རྫོང་ཁ\];                      English; Esperanto;
Estonian \[eesti\]; Ewe \[ee\]; Faroese \[føroyskt\];
Filipino; Finnish \[suomi\];                    French \[français\]; Friulian
\[furlan\];                       Ga \[gaa\]; Galician \[galego\];
Geez \[ግዕዝኛ\]; Georgian \[ქართული\];                    German \[Deutsch\];
Greek \[Ελληνικά\];                         Gujarati \[ગુજરાતી\]; Hausa
(Arabic) \[ha (Arab)\]; Hausa (Latin) \[ha (Latn)\];                    Hawaiian
\[ʻōlelo Hawaiʻi\]; Hebrew                     \[‎עברית‎\]; Hindi \[हिंदी\];
Hungarian \[magyar\]; Icelandic \[íslenska\];                   Igbo \[ig\];
Indonesian \[Bahasa Indonesia\];                   Interlingua; Inuktitut
\[ᐃᓄᒃᑎᑐᑦ ᑎᑎᕋᐅᓯᖅ\];                       Irish \[Gaeilge\]; Italian
\[italiano\];                        Japanese \[日本語\]; Jju \[kaj\];
Kalaallisut; Kamba \[kam\];                     Kannada \[ಕನ್ನಡ\]; Kazakh
\[Қазақ\];                    Khmer \[ភាសាខ្មែរ\]; Kinyarwanda \[rw\];
Kirghiz \[Кыргыз\]; Konkani                     \[कोंकणी\]; Korean \[한국어\];
Koro \[kfo\]; Kpelle \[kpe\];                   Kurdish (Arabic) \[‎كوردی
(erebî)‎\];                   Kurdish (Latin) \[kurdî (Latn)\]; Lao \[ລາວ\];
Latvian \[latviešu\]; Lingala \[lingála\];                      Lithuanian
\[lietuvių\]; Macedonian                     \[македонски\]; Malay \[Bahasa
Melayu\];                        Malayalam \[മലയാളം\]; Maltese \[Malti\];
Manx \[Gaelg\]; Marathi \[मराठी\];                      Mongolian \[монгол\];
Nepali                    \[नेपाली\]; Northern Sami \[dávvisámegiella\];
Northern Sotho \[Sesotho sa Leboa\]; Norwegian                  Bokmål \[norsk
bokmål\]; Norwegian Nynorsk \[nynorsk\];                         Nyanja \[ny\];
Oriya \[ଓଡ଼ିଆ\];                         Oromo \[Oromoo\]; Pashto \[‎پښتو‎\];
Persian \[‎فارسی‎\]; Polish \[polski\];                         Portuguese
\[português\];                       Punjabi (Arabic) \[‎پنجاب (Arab)‎\];
Punjabi (Gurmukhi) \[ਪੰਜਾਬੀ (ਗੁਰਮੁਖੀ)\]; Romanian \[română\];
Russian \[русский\];                    Sanskrit \[संस्कृत भाषा\];
Serbian (Cyrillic) \[Српски (Ћирилица)\];                       Serbian (Latin)
\[Srpski (Latinica)\];                  Sichuan Yi \[ꆈꌠꉙ\]; Sidamo \[Sidaamu
Afo\];                     Simplified Chinese \[中文（简体）\];
Slovak \[slovenský\]; Slovenian \[slovenščina\];                        Somali
\[Soomaali\]; South Ndebele \[isiNdebele\];                      Southern Sotho
\[Sesotho\]; Spanish \[español\];                        Swahili \[Kiswahili\];
Swati \[Siswati\];                       Swedish \[svenska\]; Syriac
\[‎ܣܘܪܝܝܐ‎\]; Tajik \[tg\]; Tamil \[தமிழ்\];                    Tatar \[Татар\];
Telugu \[తెలుగు\];                     Thai \[ไทย\]; Tibetan \[པོད་སྐད་\];
Tigre \[ትግረ\]; Tigrinya \[ትግርኛ\];                       Tonga \[lea fakatonga\];
Traditional Chinese \[繁體中文\]; Tsonga \[Xitsonga\];                      Tswana
\[Setswana\]; Turkish \[Türkçe\];                        Tyap \[kcg\]; Uighur
\[ug\];                    Ukrainian \[українська\];                       Urdu
\[‎اردو‎\];                        Uzbek (Arabic) \[‎اۉزبېک (Араб)‎\];
Uzbek (Cyrillic) \[Ўзбек (Кирил)\];                     Uzbek (Latin)
\[o'zbekcha (Lotin)\]; Venda \[Tshivenḓa\];                       Vietnamese
\[Tiếng Việt\]; Walamo \[ወላይታቱ\];                    Welsh \[Cymraeg\]; Wolof
(Arabic) \[wo                  (Arab)\]; Wolof (Latin) \[wo (Latn)\];
Xhosa \[isiXhosa\]; Yoruba \[yo\]; Zulu \[isiZulu\]

**Territories (149):** Afghanistan \[‎افغانستان‎\];                     Albania
\[Shqipëria\]; Algeria \[‎الجزائر‎\];                   American Samoa;
Argentina;                      Armenia \[Հայաստանի Հանրապետութիւն\];
Australia; Austria \[Österreich\];                      Azerbaijan \[Azərbaycan,
Азәрбајҹан\];                  Bahrain \[‎البحرين‎\];
Bangladesh \[বাংলাদেশ\]; Belarus \[Беларусь\];                  Belgium
\[België, Belgien, Belgique\]; Belize;                  Bhutan \[འབྲུག\];
Bolivia;                      Bosnia and Herzegovina \[Bosna i Hercegovina,
Босна и Херцеговина\]; Botswana; Brazil \[Brasil\];                     Brunei;
Bulgaria \[България\];                  Cambodia \[កម្ពុជា\]; Canada;
Chile; China \[རྒྱ་ནག, ꍏꇩ, 中国\];                        Colombia; Congo -
Brazzaville \[Kongó-Brazzaville\];                    Congo - Kinshasa
\[Kongó-Kinsásá\]; Costa Rica;                         Croatia \[Hrvatska\];
Cyprus \[Κύπρος\];                        Czech Republic \[Česká republika\];
Denmark \[Danmark\];                        Djibouti \[Jabuuti, Yabuuti\];
Dominican Republic                       \[República Dominicana\]; Ecuador;
Egypt \[EG, ‎مصر‎\]; El Salvador;                       Eritrea \[Eretria,
ኤርትራ\]; Estonia \[Eesti\];                   Ethiopia \[Itiyoophiya, Itoobiya,
Itoophiyaa, Otobbia, ኢትዮጵያ\];                         Faroe Islands \[Føroyar\];
Finland \[FI, Suomi\];                       France; Georgia \[საქართველო\];
Germany \[Deutschland\]; Ghana \[GH\];                  Greece \[Ελλάδα\];
Greenland \[Kalaallit                        Nunaat\]; Guam; Guatemala;
Guinea \[GN\]; Honduras;                        Hong                    Kong SAR
China \[中華人民共和國香港特別行政區\]; Hungary \[Magyarország\];                    Iceland
\[Ísland\];                     India \[‎بھارت‎, भारत,                  भारतम्,
ভারত, ভাৰত, ਭਾਰਤ, ભારત, ଭାରତ, இந்தியா, భారత దేళం, ಭಾರತ, ഇന്ത്യ, རྒྱ་གར་\];
Indonesia; Iran \[IR, ‎ایران‎\];                        Iraq \[IQ, ‎العراق‎\];
Ireland \[Éire\];                        Israel \[‎ישראל‎\]; Italy \[Italia,
Italie\]; Jamaica; Japan \[日本\];                        Jordan \[‎الأردن‎\];
Kazakhstan \[Қазақстан\]; Kenya \[KE, Keeniyaa, Kiiniya\];
Kuwait \[‎الكويت‎\];                    Kyrgyzstan \[Кыргызстан\]; Laos \[ລາວ\];
Latvia \[Latvija\]; Lebanon \[‎لبنان‎\];                        Liberia \[LR\];
Libya \[‎ليبيا‎\];                      Liechtenstein; Lithuania \[Lietuva\];
Luxembourg \[Luxemburg\];                       Macao SAR
China \[中華人民共和國澳門特別行政區\]; Macedonia \[Македонија\];                     Malawi
\[MW\]; Malaysia;                        Maldives \[‎ދިވެހި ރާއްޖެ‎\]; Malta;
Marshall Islands; Mexico \[México\];                    Monaco; Mongolia
\[Монгол улс\];                        Montenegro \[Crna Gora, Црна Гора\];
Morocco \[‎المغرب‎\]; Myanmar \[MM\];                   Namibia \[Namibië\];
Nepal \[NP\];                      Netherlands \[Nederland\]; New Zealand;
Nicaragua; Niger \[NE\];                        Nigeria \[NG\]; Northern Mariana
Islands;                       Norway \[Noreg, Norge, Norgga\]; Oman \[‎عمان‎\];
Pakistan \[PK, ‎پاکستان‎\]; Panama \[Panamá\];                  Paraguay; Peru
\[Perú\];                        Philippines; Poland \[Polska\]; Portugal;
Puerto Rico; Qatar \[‎قطر‎\];                   Romania \[România\]; Russia
\[Россия\];                         Rwanda \[RW\];                  Saudi Arabia
\[‎المملكة العربية السعودية‎\]; Senegal \[SN\];                    Serbia
\[Srbija, Србија\];                      Singapore \[新加坡\]; Slovakia \[Slovenská
republika\]; Slovenia \[Slovenija\];                    Somalia \[Soomaaliya\];
South Africa \[Suid-Afrika, ZA\];                       South Korea \[대한민국\];
Spain \[Espainia,                         España, Espanya\]; Sudan
\[‎السودان‎\];                         Sweden \[Sverige\]; Switzerland
\[Schweiz, Suisse,                      Svizzera\]; Syria \[SY, ‎سوريا‎,
‎ܣܘܪܝܝܐ‎\];                    Taiwan \[臺灣\]; Tajikistan \[TJ\];
Tanzania; Thailand \[ประเทศไทย\];                       Togo \[TG\]; Tonga;
Trinidad and Tobago; Tunisia \[‎تونس‎\];                        Turkey
\[Tirkiye, Türkiye\]; U.S. Virgin Islands;                       Ukraine
\[Украина, Україна\];                   United Arab Emirates \[‎الامارات العربية
المتحدة‎\]; United Kingdom \[Prydain Fawr, Rywvaneth Unys\];
United States \[Estados Unidos, ʻAmelika Hui Pū ʻIa, US\];
United States Minor Outlying Islands; Uruguay;                  Uzbekistan
\[Oʿzbekiston, Ўзбекистон\];                         Venezuela; Vietnam \[Việt
Nam\];                        Yemen \[‎اليمن‎\]; Zimbabwe

**Notes:**

*   The amount of data per locale and the status (*unconfirmed*,
    *provisional*, *contributed*, or *approved*) varies.
*   Tooltips will show the ISO code and Latin transliteration if available.
    (To set your tooltip font in IE, right click on the desktop, pick Properties
    > Appearance > Advanced > Item: ToolTip, then set the font to Arial Unicode
    MS or other large font.)
*   If the above doesn't display in your browser, see [Display
    Problems?](http://www.unicode.org/help/display_problems.html)
