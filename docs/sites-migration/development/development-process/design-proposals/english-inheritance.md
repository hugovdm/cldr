# English Inheritance

### Summary

This proposal intends to solve some of the problems that have come up during our
review of the various regional locale variants. The goal is to create a clear
and understandable policy for the various English locales in CLDR.

### International English (en_001)

A few releases back, we created the en_001 locale in CLDR, that was intended to
remove much of the U.S. specific data that existed in the "en" locale at the
time, and serve as the inheritance point for most English locales that didn't
have a direct relationship to the U.S. This was a good starting point, but in
order to clean this up and make things more consistent worldwide, the following
changes are recommended:

*   Make en_001 be as country neutral as possible. This would mean making en_001
    have the following characteristics:

    1.  Date formats - For full, long, medium formats use European style day,
        month, year. For numeric dates, use ISO 8601 format.
    2.  Time formats - Use 12 hour clock, as this is the predominant format for
        English speaking locales ( ref :
        https://en.wikipedia.org/wiki/Date_and_time_representation_by_country)
    3.  Spelling of unit names - (metre vs. meter) - Since the BIPM spelling is
        "metre", "centimetre", etc., The "en_001" locale should prefer "metre"
        over the American spelling "meter". Thus, much of the units data that is
        currently in en_GB would move from there to en_001, and en_GB would just
        inherit it.

*   Use en_001 as the basis for translation in the CLDR Survey Tool instead of
    en.
*   Make en_CA (English - Canada) inherit from en_001 instead of en. The en_CA
    locale should be reviewed to make sure that items that previously were
    correctly inherited from "en" (such as well understood time zone
    abbreviations ) are copied into the en_CA locale.
*   Make sure that proper time formats are in place for en_XX locales, where XX
    is any country where 12 hour clock is customary according to CLDR's
    supplemental data.
*   Review the inheritance table (below), making any necessary adjustments. It
    has been suggested that en_ZA and en_ZW should inherit from en_GB instead of
    en_001.

### Reference: English locales and inheritance:

Locale Territory Name
Inherits From
en_AG Antigua & Barbuda
en_001 en_AI Anguilla en_001 en_AS American Samoa
en en_AU Australia en_GB en_BB Barbados en_001 en_BE Belgium en_GB en_BM Bermuda
en_001 en_BS Bahamas en_001 en_BW Botswana en_001 en_BZ Belize en_001 en_CA
Canada en en_CC Cocos (Keeling) Islands
en_001 en_CK Cook Islands
en_001 en_CM Cameroon en_001 en_CX Christmas Island
en_001 en_DG Diego Garcia
en_GB en_DM Dominica en_001 en_ER Eritrea en_001 en_FJ Fiji en_001 en_FK
Falkland Islands
en_GB en_FM Micronesia en_001 en_GB United Kingdom
en_001 en_GD Grenada en_001 en_GG Guernsey en_GB en_GH Ghana en_001 en_GI
Gibraltar en_GB en_GM Gambia en_001 en_GU Guam en en_GY Guyana en_001 en_HK Hong
Kong
en_GB en_IE Ireland en_GB en_IM Isle of Man
en_GB en_IN India en_GB en_IO British Indian Ocean Territory
en_GB en_JE Jersey en_GB en_JM Jamaica en_001 en_KE Kenya en_001 en_KI Kiribati
en_001 en_KN St. Kitts & Nevis
en_001 en_KY Cayman Islands
en_001 en_LC St. Lucia
en_001 en_LR Liberia en_001 en_LS Lesotho en_001 en_MG Madagascar en_001 en_MH
Marshall Islands
en en_MO Macau en_GB en_MP Northern Mariana Islands
en en_MS Montserrat en_001 en_MT Malta en_GB en_MU Mauritius en_001 en_MW Malawi
en_001 en_MY Malaysia en_001 en_NA Namibia en_001 en_NF Norfolk Island
en_001 en_NG Nigeria en_001 en_NR Nauru en_001 en_NU Niue en_001 en_NZ New
Zealand
en_GB en_PG Papua New Guinea
en_001 en_PH Philippines en_001 en_PK Pakistan en_GB en_PN Pitcairn Islands
en_001 en_PR Puerto Rico
en en_PW Palau en_001 en_RW Rwanda en_001 en_SB Solomon Islands
en_001 en_SC Seychelles en_001 en_SD Sudan en_001 en_SG Singapore en_GB en_SH
St. Helena
en_GB en_SL Sierra Leone
en_001 en_SS South Sudan
en_001 en_SX Sint Maarten
en_001 en_SZ Swaziland en_001 en_TC Turks & Caicos Islands
en_001 en_TK Tokelau en_001 en_TO Tonga en_001 en_TT Trinidad & Tobago
en_001 en_TV Tuvalu en_001 en_TZ Tanzania en_001 en_UG Uganda en_001 en_UM U.S.
Outlying Islands
en en_US United States
en en_VC St. Vincent & Grenadines
en_001 en_VG British Virgin Islands
en_GB en_VI U.S. Virgin Islands
en en_VU Vanuatu en_001 en_WS Samoa en_001 en_ZA South Africa
en_001 en_ZM Zambia en_001 en_ZW Zimbabwe en_001
