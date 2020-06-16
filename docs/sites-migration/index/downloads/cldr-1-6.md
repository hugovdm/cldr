# CLDR 1.6 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases
(Downloads)](http://unicode.org/cldr/data/docs/web/repository_access.html). *In
terms of license, the Unicode [Terms of Use](http://unicode.org/copyright.html)
apply; in particular, [Exhibit 1](http://unicode.org/copyright.html#Exhibit1).*

No. Date Rel. Note Data Spec Delta CVS Tag **1.6** **2008-07-02**
**[Version1.6](http://unicode.org/cldr/data/docs/web/version/1.6.html)**
**[CLDR1.6](http://unicode.org/Public/cldr/1.6.0/)**
**[LDML1.6](http://www.unicode.org/reports/tr35/tr35-10.html)**
**[Changes1.6](http://www.unicode.org/cldr/bugs/locale-bugs/closed?expression=target.*1.6)**
**`release-1-6`**

***Note:** See also
[Errata](http://unicode.org/cldr/data/docs/web/errata.html).*

CLDR 1.6 contains data for 137 languages and 140 territories: 374 locales in
all. Version 1.6 of the repository contains over 32% more locale data than the
previous release, with nearly 24,000 new or modified data items entered by over
220 different contributors.

Major contributors to CLDR 1.6 include Adobe, Apple, Google, IBM, and Sun, plus
official representatives from a number of countries. Many other organizations
and volunteers around the globe, including Gnome, Kotoistus, LISA, OpenOffice,
and Utilika, have also made important contributions. The data for CLDR is
gathered through the CLDR *survey tool*, which allows organizations and
volunteers to contribute, compare, and vet locale data. For web pages with
different views of CLDR data, see <http://unicode.org/cldr/charts.html>.

Unicode CLDR 1.6 is part of the Unicode locale data project, together with the
Unicode Locale Data Markup Language (LDML: <http://unicode.org/reports/tr35/>).
LDML is an XML format used for general interchange of locale data, such as in
Microsoft's .NET. Major new features of Unicode LDML 1.6 include:

*   Plural rules (such as the 4 forms for Russian).
*   Plural forms of currencies and date/time durations ("1 hour" vs "2 hours")
*   Interval formats for a concise representation of a range of two dates or
    times ("Jan 10-12, 2008").
*   Telephone codes for different countries.
*   Clarified fallback process for resource bundle lookup and resource item
    lookup.
*   Explicit definition of Unicode locale and language identifiers.
*   Many other clarifications and corrections.

### List of Languages and Territories in this Release

**Languages (137):** Afar \[Qafar\]; Afrikaans; Akan \[ak\]; Albanian
\[shqipe\]; Amharic \[አማርኛ\]; Arabic \[‎العربية‎\]; Armenian \[Հայերէն\];
Assamese \[অসমীয়া\]; Atsam \[cch\]; Azerbaijani (Cyrillic) \[Азәрбајҹан
(kiril)\]; Azerbaijani (Latin) \[azərbaycanca (latın)\]; Basque \[euskara\];
Belarusian \[беларуская\]; Bengali \[বাংলা\]; Blin \[ብሊን\]; Bosnian
\[Bosanski\]; Bulgarian \[български\]; Burmese \[ဗမာ\]; Catalan \[català\];
Coptic \[cop\]; Cornish \[kernewek\]; Croatian \[hrvatski\]; Czech \[čeština\];
Danish \[dansk\]; Divehi \[‎ދިވެހިބަސް‎\]; Dutch \[Nederlands\]; Dzongkha
\[རྫོང་ཁ\]; English (Deseret) \[𐐀𐑍𐑊𐐮𐑇 (𐐔𐐯𐑆𐐲𐑉𐐯𐐻)\]; English (Shavian); Esperanto;
Estonian \[eesti\]; Ewe \[ee\]; Faroese \[føroyskt\]; Filipino; Finnish
\[suomi\]; French \[français\]; Friulian \[furlan\]; Ga \[gaa\]; Galician
\[galego\]; Geez \[ግዕዝኛ\]; Georgian \[ქართული\]; German \[Deutsch\]; Greek
\[Ελληνικά\]; Gujarati \[ગુજરાતી\]; Hausa (Arabic) \[Haoussa (Arab)\]; Hausa
(Latin) \[Haoussa (Latn)\]; Hawaiian \[ʻōlelo Hawaiʻi\]; Hebrew \[‎עברית‎\];
Hindi \[हिन्दी\]; Hungarian \[magyar\]; Icelandic \[íslenska\]; Igbo \[ig\];
Indonesian \[Bahasa Indonesia\]; Interlingua; Inuktitut \[ᐃᓄᒃᑎᑐᑦ ᑎᑎᕋᐅᓯᖅ\]; Irish
\[Gaeilge\]; Italian \[italiano\]; Japanese \[日本語\]; Jju \[kaj\]; Kalaallisut;
Kamba \[kam\]; Kannada \[ಕನ್ನಡ\]; Kazakh (Cyrillic) \[Қазақ (Cyrl)\]; Khmer
\[ភាសាខ្មែរ\]; Kinyarwanda \[rw\]; Kirghiz \[Кыргыз\]; Konkani \[कोंकणी\];
Korean \[한국어\]; Koro \[kfo\]; Kpelle \[kpe\]; Kurdish (Arabic) \[‎كوردی
(Arab)‎\]; Kurdish (Latin) \[kurdî (Latn)\]; Lao \[ລາວ\]; Latvian \[latviešu\];
Lingala \[lingála\]; Lithuanian \[lietuvių\]; Macedonian \[македонски\]; Malay
\[Bahasa Melayu\]; Malayalam \[മലയാളം\]; Maltese \[Malti\]; Manx \[Gaelg\];
Marathi \[मराठी\]; Moldavian \[moldovenească\]; Mongolian (Cyrillic) \[монгол
(Cyrl)\]; Mongolian (Mongolian) \[монгол (Mong)\]; Nepali \[नेपाली\]; Northern
Sami \[davvisámegiella\]; Northern Sotho \[Sesotho sa Leboa\]; Norwegian
\[norsk\]; Norwegian Bokmål \[norsk bokmål\]; Norwegian Nynorsk \[nynorsk\];
Nyanja \[ny\]; Oriya \[ଓଡ଼ିଆ\]; Oromo \[Oromoo\]; Pashto \[‎پښتو‎\]; Persian
\[‎فارسی‎\]; Polish \[polski\]; Portuguese \[português\]; Punjabi (Arabic)
\[‎پنجاب (العربية)‎\]; Punjabi (Gurmukhi) \[ਪੰਜਾਬੀ (ਗੁਰਮੁਖੀ)\]; Romanian
\[română\]; Russian \[русский\]; Sanskrit \[संस्कृत भाषा\]; Serbian (Cyrillic)
\[Српски (Ћирилица)\]; Serbian (Latin) \[Srpski (Latinica)\]; Sichuan Yi
\[ꆈꌠꉙ\]; Sidamo \[Sidaamu Afo\]; Simplified Chinese \[中文（简体）\]; Sinhala
\[සිංහල\]; Slovak \[slovenský\]; Slovenian \[slovenščina\]; Somali \[Soomaali\];
South Ndebele \[isiNdebele\]; Southern Sotho \[Sesotho\]; Spanish \[español\];
Swahili \[Kiswahili\]; Swati \[Siswati\]; Swedish \[svenska\]; Syriac
\[‎ܣܘܪܝܝܐ‎\]; Tagalog; Tajik (Cyrillic) \[tg (Cyrl)\]; Tamil \[தமிழ்\]; Tatar
\[Татар\]; Telugu \[తెలుగు\]; Thai \[ไทย\]; Tigre \[ትግረ\]; Tigrinya \[ትግርኛ\];
Tonga \[lea fakatonga\]; Traditional Chinese \[繁體中文\]; Tsonga \[Xitsonga\];
Tswana \[Setswana\]; Turkish \[Türkçe\]; Tyap \[kcg\]; Uighur (Arabic) \[ug
(Arab)\]; Ukrainian \[українська\]; Urdu \[‎اردو‎\]; Uzbek (Arabic) \[‎اۉزبېک
(Араб)‎\]; Uzbek (Cyrillic) \[Ўзбек (Кирил)\]; Uzbek (Latin) \[o'zbekcha
(Lotin)\]; Venda \[Tshivenḓa\]; Vietnamese \[Tiếng Việt\]; Walamo \[ወላይታቱ\];
Welsh \[Cymraeg\]; Wolof (Latin) \[wo (Latn)\]; Xhosa \[isiXhosa\]; Yoruba
\[Yorùbá\]; Zulu \[isiZulu\]

**Territories (140):** Afghanistan \[‎افغانستان‎\]; Albania \[Shqipëria\];
Algeria \[‎الجزائر‎\]; Argentina; Armenia \[Հայաստանի Հանրապետութիւն\]; Austria
\[Österreich\]; Azerbaijan \[Azərbaycan, Азәрбајҹан\]; Bahrain \[‎البحرين‎\];
Bangladesh \[বাংলাদেশ\]; Belarus \[Беларусь\]; Belgium \[België, Belgien,
Belgique\]; Bhutan \[འབྲུག\]; Bolivia; Bosnia and Herzegovina \[Bosna i
Hercegovina, Босна и Херцеговина\]; Brazil \[Brasil\]; Brunei; Bulgaria
\[България\]; Cambodia \[កម្ពុជា\]; Canada; Chile; China \[CN, ꍏꇩ, 中国\];
Colombia; Congo - Brazzaville \[Kongó-Brazzaville\]; Congo - Kinshasa
\[Kongó-Kinsásá\]; Costa Rica; Croatia \[Hrvatska\]; Cyprus \[Κύπρος\]; Czech
Republic \[Česká republika\]; Denmark \[Danmark\]; Djibouti \[Jabuuti,
Yabuuti\]; Dominican Republic \[República Dominicana\]; Ecuador; Egypt
\[‎مصر‎\]; El Salvador; Eritrea \[Eretria, ኤርትራ\]; Estonia \[Eesti\]; Ethiopia
\[Itiyoophiya, Itoobiya, Itoophiyaa, Otobbia, ኢትዮጵያ\]; Faroe Islands
\[Føroyar\]; Finland \[FI, Suomi\]; France; Georgia \[საქართველო\]; Germany
\[Deutschland\]; Ghana \[GH\]; Greece \[Ελλάδα\]; Greenland \[Kalaallit
Nunaat\]; Guatemala; Guinea \[GN\]; Honduras; Hong Kong SAR China \[中国香港特别行政区,
中華人民共和國香港特別行政區\]; Hungary \[Magyarország\]; Iceland \[Ísland\]; India \[‎بھارت‎,
भारत, भारतम्, ভারত, ভাৰত, ਭਾਰਤ, ભારત, ଭାରତ, இந்தியா, భారత దేళం, ಭಾರತ, ഇന്ത്യ\];
Indonesia; Iran \[‎ایران‎\]; Iraq \[‎العراق‎\]; Ireland \[Éire\]; Israel
\[‎ישראל‎\]; Italy \[Italia, Italie\]; Ivory Coast \[CI\]; Japan \[日本\]; Jordan
\[‎الأردن‎\]; Kazakhstan \[Қазақстан\]; Kenya \[KE, Keeniyaa, Kiiniya\]; Kuwait
\[‎الكويت‎\]; Kyrgyzstan \[Кыргызстан\]; Laos \[ລາວ\]; Latvia \[Latvija\];
Lebanon \[‎لبنان‎\]; Lesotho \[LS\]; Liberia \[LR\]; Libya \[‎ليبيا‎\];
Liechtenstein; Lithuania \[Lietuva\]; Luxembourg \[Luxemburg\]; Macau SAR China
\[中国澳门特别行政区, 中華人民共和國澳門特別行政區\]; Macedonia \[Македонија\]; Malawi \[MW\];
Malaysia; Maldives \[‎ދިވެހި ރާއްޖެ‎\]; Malta; Mexico \[México\]; Moldova
\[Moldova, Republica\]; Monaco; Mongolia \[Монгол улс\]; Montenegro \[Crna Gora,
Црна Гора\]; Morocco \[‎المغرب‎\]; Myanmar \[မြန်မာ\]; Namibia \[Namibië\];
Nepal \[नेपाल\]; Netherlands \[Nederland\]; Nicaragua; Niger \[NE\]; Nigeria
\[NG, Nijeriya\]; Norway \[Noreg, Norga, Norge\]; Oman \[‎عمان‎\]; Pakistan
\[‎پاکستان‎, ‎پکستان‎\]; Panama \[Panamá\]; Paraguay; Peru \[Perú\]; Philippines
\[Pilipinas\]; Poland \[Polska\]; Portugal; Puerto Rico; Qatar \[‎قطر‎\];
Romania \[România\]; Russia \[Россия\]; Rwanda \[RW\]; Saudi Arabia \[‎المملكة
العربية السعودية‎\]; Senegal \[Sénégal, SN\]; Serbia \[Srbija, Србија\];
Singapore \[新加坡\]; Slovakia \[Slovenská republika\]; Slovenia \[Slovenija\];
Somalia \[Soomaaliya\]; South Africa \[Suid-Afrika, ZA\]; South Korea \[대한민국\];
Spain \[Espainia, España, Espanya\]; Sri Lanka \[ශ්‍රී ලංකාව\]; Sudan \[SD,
‎السودان‎\]; Swaziland \[SZ\]; Sweden \[Sverige\]; Switzerland \[Schweiz,
Suisse, Svizzera\]; Syria \[‎سوريا‎, ‎ܣܘܪܝܝܐ‎\]; Taiwan \[臺灣\]; Tajikistan
\[TJ\]; Tanzania; Thailand \[ไทย\]; Togo \[TG\]; Tonga; Tunisia \[‎تونس‎\];
Turkey \[Tirkiye, Türkiye\]; Ukraine \[Украина, Україна\]; United Arab Emirates
\[‎الامارات العربية المتحدة‎\]; United Kingdom \[Prydain Fawr, Rywvaneth Unys\];
United States \[Estados Unidos, ʻAmelika Hui Pū ʻIa, 𐐏𐐭𐑌𐐴𐐻𐐲𐐼 𐐝𐐻𐐩𐐻𐑅\]; Uruguay;
Uzbekistan \[Oʿzbekiston, Ўзбекистон\]; Venezuela; Vietnam \[Việt Nam\]; Yemen
\[‎اليمن‎\]

**Notes:**

*   The amount of data per locale and the status (*unconfirmed*, *provisional*,
    *contributed*, or *approved*) varies.
*   Tooltips will show the ISO code and Latin transliteration if available.
    (To set your tooltip font in IE, right click on the desktop, pick Properties
    > Appearance > Advanced > Item: ToolTip, then set the font to Arial Unicode
    MS or other large font.)
*   If the above doesn't display in your browser, see [Display
    Problems?](http://www.unicode.org/help/display_problems.html)
