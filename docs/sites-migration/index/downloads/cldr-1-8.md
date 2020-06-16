# CLDR 1.8 Release Note

The following are the files for this release. For a description of their purpose
and format, see [CLDR Releases (Downloads)](index.md).

No. Date Rel. Note Data Spec Delta CVS Tag **1.8** **2010-03-17**
**[Version1.8](cldr-1-8.md)**
**[CLDR1.8](http://unicode.org/Public/cldr/1.8.0/)**
**[LDML1.8](http://www.unicode.org/reports/tr35/tr35-15.html)**
**[Changes1.8](http://unicode.org/cldr/trac/query?status=closed&milestone=1.8p1&milestone=1.8p2&milestone=1.8&milestone=1.8o)**
**`release-1-8-0`**

***Note:** See also [Errata](http://cldr.unicode.org/errata/).*

Unicode CLDR 1.8 contains data for 186 languages and 159 territories: 501
locales in all. Version 1.8 of the repository contains over 22% more locale data
than the previous release, with over 42,000 new or modified data items from more
than 300 different contributors. Major contributors to CLDR 1.8 include Afrigen,
ANLoc, Apple, Google, and IBM, plus official representatives from a number of
countries such as Finland (Kotoistus), India (Department of Information
Technology), and France (Office de la Langue Bretonne). Many other organizations
and volunteers around the globe, including Adobe, Gnome, LISA, OpenOffice, and
Utilika, have also made important contributions.

The new features of Unicode CLDR 1.8 include:

*   Many new and enhanced locales for Africa, submitted by Afrigen (for more
    information, see the [press
    release](http://www.unicode.org/press/pr-cldr1.8.html))
*   Index exemplar characters, for first-letter indexes in phones and other
    environments
*   Day periods, for languages where am/pm are insufficient
*   List patterns, for composing a list such as "**A**, **B** et **C**"
*   Language matching data, for matching requested locales against supported
    locales.
*   Improved BCP47 support, for canonicalization of macrolanguages and 3
    letter/digit aliases
*   Modularized timezone information, for ease of updating to timezone database
    releases

Unicode CLDR 1.8 is part of the Unicode locale data project, together with the
Unicode Locale Data Markup Language (LDML: <http://unicode.org/reports/tr35/>).
LDML is an XML format used for general interchange of locale data, such as in
Microsoft's .NET. For web pages with different views of CLDR data,
see<http://cldr.unicode.org/index/charts>.

### List of Languages and Territories in this Release

**Languages:** Afar \[Qafar\]; Afrikaans; Akan; Albanian \[shqipe\]; Amharic
\[አማርኛ\]; Arabic \[‎العربية‎\]; Armenian \[Հայերէն\]; Assamese \[অসমীয়া\]; Asu
\[Kipare\]; Atsam \[cch\]; Azerbaijani (Arabic) \[azərbaycanca (ərəb)\];
Azerbaijani (Cyrillic) \[Азәрбајҹан (kiril)\]; Azerbaijani (Latin)
\[azərbaycanca (latın)\]; Bambara \[bamanakan\]; Basque \[euskara\]; Belarusian
\[беларуская\]; Bemba \[Ichibemba\]; Bena \[Hibena\]; Bengali \[বাংলা\]; Blin
\[ብሊን\]; Bosnian \[Bosanski\]; Breton \[br\]; Bulgarian \[български\]; Burmese
\[ဗမာ\]; Catalan \[català\]; Central Morocco Tamazight (Latin) \[Tamaziɣt
(Latn)\]; Cherokee \[ᏣᎳᎩ\]; Chiga \[Rukiga\]; Colognian \[ksh\]; Cornish
\[kernewek\]; Croatian \[hrvatski\]; Czech \[čeština\]; Danish \[dansk\]; Divehi
\[‎ދިވެހިބަސް‎\]; Dutch \[Nederlands\]; Dzongkha \[རྫོང་ཁ\]; Embu \[Kĩembu\];
English (Deseret) \[𐐀𐑍𐑊𐐮𐑇 (𐐔𐐯𐑆𐐲𐑉𐐯𐐻)\]; English (Shavian); Esperanto; Estonian
\[eesti\]; Ewe \[Eʋegbe\]; Faroese \[føroyskt\]; Filipino; Finnish \[suomi\];
French \[français\]; Friulian \[furlan\]; Fulah \[Pulaar\]; Ga \[gaa\]; Galician
\[galego\]; Ganda \[Luganda\]; Geez \[ግዕዝኛ\]; Georgian \[ქართული\]; German
\[Deutsch\]; Greek \[Ελληνικά\]; Gujarati \[ગુજરાતી\]; Gusii \[Ekegusii\]; Hausa
(Arabic) \[Hausa (Arab)\]; Hausa (Latin) \[Hausa (Latn)\]; Hawaiian \[ʻōlelo
Hawaiʻi\]; Hebrew \[‎עברית‎\]; Hindi \[हिन्दी\]; Hungarian \[magyar\]; Icelandic
\[íslenska\]; Igbo; Indonesian \[Bahasa Indonesia\]; Interlingua; Inuktitut
\[ᐃᓄᒃᑎᑐᑦ ᑎᑎᕋᐅᓯᖅ\]; Irish \[Gaeilge\]; Italian \[italiano\]; Japanese \[日本語\];
Jju \[kaj\]; Kabuverdianu; Kabyle \[Taqbaylit\]; Kalaallisut; Kalenjin; Kamba
\[Kikamba\]; Kannada \[ಕನ್ನಡ\]; Kazakh (Cyrillic) \[Қазақ (Cyrl)\]; Khmer
\[ភាសាខ្មែរ\]; Kikuyu \[Gikuyu\]; Kinyarwanda; Kirghiz \[Кыргыз\]; Konkani
\[कोंकणी\]; Korean \[한국어\]; Koro \[kfo\]; Koyra Chiini \[Koyra ciini\];
Koyraboro Senni; Kpelle \[kpe\]; Kurdish (Arabic) \[‎كوردی (عەرەبی)‎\]; Kurdish
(Latin) \[‎kurdî (لاتین)‎\]; Langi \[Kɨlaangi\]; Lao \[ລາວ\]; Latvian
\[latviešu\]; Lingala \[lingála\]; Lithuanian \[lietuvių\]; Low German
\[Plattdüütsch\]; Luo \[Dholuo\]; Luyia \[Luluhia\]; Macedonian \[македонски\];
Machame \[Kimachame\]; Makonde \[Chimakonde\]; Malagasy; Malay \[Bahasa
Melayu\]; Malayalam \[മലയാളം\]; Maltese \[Malti\]; Manx \[Gaelg\]; Maori \[mi\];
Marathi \[मराठी\]; Masai \[Maa\]; Meru \[Kĩmĩrũ\]; Mongolian (Cyrillic) \[монгол
(Cyrl)\]; Mongolian (Mongolian) \[монгол (Mong)\]; Morisyen \[kreol morisien\];
Nama \[Khoekhoegowab\]; Nepali \[नेपाली\]; North Ndebele \[isiNdebele\];
Northern Sami \[davvisámegiella\]; Northern Sotho \[Sesotho sa Leboa\];
Norwegian \[norsk\]; Norwegian Bokmål \[norsk bokmål\]; Norwegian Nynorsk
\[nynorsk\]; Nyanja \[ny\]; Nyankole \[Runyankore\]; Occitan; Oriya \[ଓଡ଼ିଆ\];
Oromo \[Oromoo\]; Pashto \[‎پښتو‎\]; Persian \[‎فارسی‎\]; Polish \[polski\];
Portuguese \[português\]; Punjabi (Arabic) \[‎پنجاب (العربية)‎\]; Punjabi
(Gurmukhi) \[ਪੰਜਾਬੀ (ਗੁਰਮੁਖੀ)\]; Romanian \[română\]; Romansh \[rumantsch\];
Rombo \[Kihorombo\]; Russian \[русский\]; Rwa \[Kiruwa\]; Saho \[ssy\]; Samburu
\[Kisampur\]; Sango \[Sängö\]; Sanskrit \[संस्कृत भाषा\]; Sena; Serbian
(Cyrillic) \[Српски (Ћирилица)\]; Serbian (Latin) \[Srpski (Latinica)\];
Shambala \[Kishambaa\]; Shona \[chiShona\]; Sichuan Yi \[ꆈꌠꉙ\]; Sidamo \[Sidaamu
Afo\]; Simplified Chinese \[中文（简体）\]; Sinhala \[සිංහල\]; Slovak \[slovenčina\];
Slovenian \[slovenščina\]; Soga \[Olusoga\]; Somali \[Soomaali\]; South Ndebele
\[isiNdebele\]; Southern Sotho \[Sesotho\]; Spanish \[español\]; Swahili
\[Kenya\]; Swati \[Siswati\]; Swedish \[svenska\]; Swiss German
\[Schwiizertüütsch\]; Syriac \[‎ܣܘܪܝܝܐ‎\]; Tachelhit (Latin) \[tamazight
(Latn)\]; Tachelhit (Tifinagh) \[ⵜⴰⵎⴰⵣⵉⵖⵜ (Tfng)\]; Tagalog; Taita \[Kitaita\];
Tajik (Cyrillic) \[tg (Cyrl)\]; Tamil \[தமிழ்\]; Taroko \[trv\]; Tatar
\[Татар\]; Telugu \[తెలుగు\]; Teso \[Kiteso\]; Thai \[ไทย\]; Tibetan
\[པོད་སྐད་\]; Tigre \[ትግረ\]; Tigrinya \[ትግርኛ\]; Tonga \[lea fakatonga\];
Traditional Chinese \[繁體中文\]; Tsonga \[Xitsonga\]; Tswana \[Setswana\]; Turkish
\[Türkçe\]; Tyap \[kcg\]; Uighur (Arabic) \[ug (Arab)\]; Ukrainian
\[українська\]; Urdu \[‎اردو‎\]; Uzbek (Arabic) \[‎اۉزبېک (Араб)‎\]; Uzbek
(Cyrillic) \[Ўзбек (Кирил)\]; Uzbek (Latin) \[o'zbekcha (Lotin)\]; Venda
\[Tshivenḓa\]; Vietnamese \[Tiếng Việt\]; Vunjo \[Kyivunjo\]; Walamo \[ወላይታቱ\];
Welsh \[Cymraeg\]; Wolof (Latin) \[wo (Latn)\]; Xhosa \[isiXhosa\]; Yoruba \[Èdè
Yorùbá\]; Zulu \[isiZulu\]

**Territories:** Afghanistan \[‎افغانستان‎\]; Albania \[Shqipëria\]; Algeria
\[Lezzayer, ‎الجزائر‎\]; Argentina; Armenia \[Հայաստանի Հանրապետութիւն\];
Austria \[Österreich\]; Azerbaijan \[Azərbaycan, Азәрбајҹан\]; Bahrain
\[‎البحرين‎\]; Bangladesh \[বাংলাদেশ\]; Belarus \[Беларусь\]; Belgium \[België,
Belgien, Belgique\]; Bhutan \[འབྲུག\]; Bolivia; Bosnia and Herzegovina \[Bosna i
Hercegovina, Босна и Херцеговина\]; Brazil \[Brasil\]; Brunei; Bulgaria
\[България\]; Cambodia \[កម្ពុជា\]; Cameroon \[Cameroun\]; Canada; Cape Verde
\[Kabu Verdi\]; Central African Republic \[Ködörösêse tî Bêafrîka, République
centrafricaine\]; Chile; China \[CN, རྒྱ་ནག, ꍏꇩ, 中国\]; Colombia; Congo -
Brazzaville \[Kongó-Brazzaville\]; Congo - Kinshasa \[Kongó-Kinsásá\]; Costa
Rica; Côte d’Ivoire \[CI\]; Croatia \[Hrvatska\]; Cyprus \[Κύπρος\]; Czech
Republic \[Česká republika\]; Denmark \[Danmark\]; Djibouti \[Jabuuti,
Yabuuti\]; Dominican Republic \[República Dominicana\]; Ecuador; Egypt
\[‎مصر‎\]; El Salvador; Equatorial Guinea \[Guinea Ecuatorial\]; Eritrea
\[Eretria, ኤርትራ\]; Estonia \[Eesti\]; Ethiopia \[Itiyoophiya, Itoobiya,
Itoophiyaa, Otobbia, ኢትዮጵያ\]; Faroe Islands \[Føroyar\]; Finland \[Suomi,
Suopma\]; France \[França, Frañs\]; Georgia \[საქართველო\]; Germany
\[Deutschland, Doütschland, Düütschland\]; Ghana \[Gaana, Gana, GH, Ghanadu\];
Greece \[Ελλάδα\]; Greenland \[Kalaallit Nunaat\]; Guadeloupe; Guatemala; Guinea
\[GN, Guinée\]; Guinea-Bissau \[Guiné Bissau\]; Honduras; Hong Kong SAR China
\[中国香港特别行政区, 中華人民共和國香港特別行政區\]; Hungary \[Magyarország\]; Iceland \[Ísland\];
India \[‎بھارت‎, भारत, भारतम्, ভারত, ভাৰত, ਭਾਰਤ, ભારત, ଭାରତ, இந்தியா, భారత దేశం,
ಭಾರತ, ഇന്ത്യ, རྒྱ་གར་\]; Indonesia; Iran \[IR, ‎ایران‎\]; Iraq \[‎العراق‎,
‎عێراق‎\]; Ireland \[Éire\]; Israel \[‎ישראל‎\]; Italy \[Italia, Italie\]; Japan
\[日本\]; Jordan \[‎الأردن‎\]; Kazakhstan \[Қазақстан\]; Kenya \[Emetab Kenya,
Keeniyaa, Kenia, Kiiniya\]; Kuwait \[‎الكويت‎\]; Kyrgyzstan \[Кыргызстан\]; Laos
\[ລາວ\]; Latin America and the Caribbean \[Latinoamérica y el Caribe\]; Latvia
\[Latvija\]; Lebanon \[‎لبنان‎\]; Lesotho \[LS\]; Liberia \[LR\]; Libya
\[‎ليبيا‎\]; Liechtenstein; Lithuania \[Lietuva\]; Luxembourg \[Luxemburg\];
Macau SAR China \[中国澳门特别行政区, 中華人民共和國澳門特別行政區\]; Macedonia \[Македонија\];
Madagascar \[Madagasikara\]; Malawi \[MW\]; Malaysia; Maldives \[‎ދިވެހި
ރާއްޖެ‎\]; Mali \[Maali\]; Malta; Martinique; Mauritius \[Moris\]; Mexico
\[México\]; Moldova \[Republica Moldova, Молдова\]; Monaco; Mongolia \[Монгол
улс\]; Montenegro \[Crna Gora, Црна Гора\]; Morocco \[lmɣrib, Meṛṛuk, ‎المغرب‎,
ⵍⵎⵖⵔⵉⴱ\]; Mozambique \[Moçambique\]; Myanmar \[Burma\] \[မြန်မာ\]; Namibia
\[Namibiab, Namibië\]; Nepal \[नेपाल\]; Netherlands \[Nederland\]; New Zealand
\[NZ\]; Nicaragua; Niger \[Nijar\]; Nigeria \[Najeriya, NG, Orílẹ́ède
Nàìjíríà\]; Norway \[Noreg, Norga, Norge\]; Oman \[‎عُمان‎\]; Pakistan
\[‎پاکستان‎, ‎پکستان‎\]; Panama \[Panamá\]; Paraguay; Peru \[Perú\]; Philippines
\[Pilipinas\]; Poland \[Polska\]; Portugal; Puerto Rico; Qatar \[‎قطر‎\];
Réunion; Romania \[România\]; Russia \[Россия\]; Rwanda; Saint Barthélemy
\[Saint-Barthélémy\]; Saint Martin \[Saint-Martin\]; Saudi Arabia \[‎المملكة
العربية السعودية‎\]; Senegal \[Senegaal, Sénégal, SN\]; Serbia \[Srbija,
Србија\]; Singapore \[新加坡\]; Slovakia \[Slovenská republika\]; Slovenia
\[Slovenija\]; Somalia \[Soomaaliya\]; South Africa \[iNingizimu Afrika,
Suid-Afrika, ZA\]; South Korea \[대한민국\]; Spain \[Espainia, España, Espanya\];
Sri Lanka \[இலங்கை, ශ්‍රී ලංකාව\]; Sudan \[‎السودان‎\]; Swaziland \[SZ\]; Sweden
\[Sverige\]; Switzerland \[Schweiz, Schwiiz, Suisse, Svizra, Svizzera\]; Syria
\[SY, ‎سوريا‎, ‎ܣܘܪܝܝܐ‎\]; Taiwan \[TW, 台灣\]; Tajikistan \[TJ\]; Tanzania
\[Hutanzania, Taansanía, Tadhania, Tansania\]; Thailand \[ไทย\]; Togo
\[Togodu\]; Tonga; Tunisia \[‎تونس‎\]; Turkey \[Tirkiye, Türkiye\]; Uganda
\[Yuganda\]; Ukraine \[Украина, Україна\]; United Arab Emirates \[‎الامارات
العربية المتحدة‎\]; United Kingdom \[Prydain Fawr, Rywvaneth Unys\]; United
States \[Estados Unidos, ʻAmelika Hui Pū ʻIa, ᎠᎹᏰᏟ, 𐐏𐐭𐑌𐐴𐐻𐐲𐐼 𐐝𐐻𐐩𐐻𐑅\]; Uruguay;
Uzbekistan \[Oʿzbekiston, Ўзбекистон\]; Venezuela; Vietnam \[Việt Nam\]; Yemen
\[‎اليمن‎\]; Zambia; Zimbabwe

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
