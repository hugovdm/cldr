# test-chart-links

[TOC]

You can use these to test.

***{latest} = latest release, currently 29***

***{def} = development release, current 30**β***

## Priorities

1.  **First** priority is that the link go to the right **contents**, eg
    *   <http://unicode.org/cldr/charts/latest> =>
        <http://www.unicode.org/repos/cldr-aux/charts/29/index.html>
    *   Look at the title and Version number to see that the contents are right.
2.  **Second** priority is that the link in the address bar be clean, with
    /cldr/, /latest/, or /dev/ maintained:
    *   …/cldr/… instead of …/repos/cldr-aux/…
    *   …/latest/… instead of …/24/…
    *   …/dev/… instead of …/25/…
    *   It's ok for
        *   unversioned to go to /latest/
        *   …/foo or .../foo/ to go to …/foo/index.html

## Non-Directory

/\* is not a directory (eg whenever the last entry ends with .html or .css)

***versioned charts - contents***

http://unicode.org/cldr/charts/(\[\\d.\]\*)/ =>
http://unicode.org/repos/cldr-aux/charts/$1/\*

http://unicode.org/cldr/charts/\* =>
http://unicode.org/repos/cldr-aux/charts/{latest}/\*

## Latest

<http://unicode.org/cldr/charts/latest>

<http://unicode.org/cldr/charts/latest/>

<http://unicode.org/cldr/charts/latest/index.html>

=> http://www.unicode.org/cldr/charts/{latest}/index.html

<http://unicode.org/cldr/charts/latest/transforms>

<http://unicode.org/cldr/charts/latest/transforms/>

<http://unicode.org/cldr/charts/latest/transforms/index.html>

=> http://www.unicode.org/cldr/charts/{latest}/transforms/index.html

<http://unicode.org/cldr/charts/latest/transforms/Latin-Arabic.html>

=> http://www.unicode.org/cldr/charts/{latest}/transforms/Latin-Arabic.html

## Development

<http://unicode.org/cldr/charts/dev>

<http://unicode.org/cldr/charts/dev/>

<http://unicode.org/cldr/charts/dev/index.html>

=> http://www.unicode.org/cldr/charts/{dev}/index.html

<http://unicode.org/cldr/charts/dev/transforms/index.html> (each of these)

<http://unicode.org/cldr/charts/dev/transforms/>

<http://unicode.org/cldr/charts/dev/transforms>

=> http://www.unicode.org/cldr/charts/{dev}/transforms/index.html

<http://unicode.org/cldr/charts/dev/transforms/Latin-Arabic.html>

=> http://www.unicode.org/cldr/charts/{dev}/transforms/Latin-Arabic.html

## Versioned

<http://unicode.org/cldr/charts/29>

<http://unicode.org/cldr/charts/29/>

<http://unicode.org/cldr/charts/29/index.html>

=> http://www.unicode.org/cldr/charts/{latest}/index.html

<http://unicode.org/cldr/charts/29/transforms>

<http://unicode.org/cldr/charts/29/transforms/>

<http://unicode.org/cldr/charts/29/transforms/index.html>

=> http://www.unicode.org/cldr/charts/{latest}/transforms/index.html

<http://unicode.org/cldr/charts/29/transforms/Latin-Arabic.html>

=>
<http://unicode.org/repos/cldr-aux/charts>/29/[transforms/Latin-Arabic.html](http://unicode.org/repos/cldr-aux/charts/25.1/transforms/Latin-Arabic.html)

## Unversioned = Latest

<http://www.unicode.org/cldr/charts/latest/by_type/core_data.alphabetic_information.html​>

=>
http://www.unicode.org/cldr/charts/**{latest}**/by_type/core_data.alphabetic_information.html​

<http://unicode.org/cldr/charts/keyboards/chars2keyboards.html>

=>
http://www.unicode.org/cldr/charts/**{latest}**/keyboards/chars2keyboards.html

<http://unicode.org/cldr/charts/keyboards/layouts/fr.html>

=> http://www.unicode.org/cldr/charts/**{latest}**/keyboards/layouts/fr.html

<http://unicode.org/cldr/charts/summary/de.html>

=> http://www.unicode.org/cldr/charts/**{latest}**/summary/de.html

<http://unicode.org/cldr/charts/supplemental/language_plural_rules.html>

=>
http://www.unicode.org/cldr/charts/**{latest}**/supplemental/language_plural_rules.html

<http://unicode.org/cldr/charts/transforms/Latin-Arabic.html>

=> http://www.unicode.org/cldr/charts/**{latest}**/transforms/Latin-Arabic.html

### **Main Page**

<http://unicode.org/cldr/charts> => http://cldr.unicode.org/index/charts

<http://unicode.org/cldr/charts/> => http://cldr.unicode.org/index/charts

<http://unicode.org/cldr/charts/29> => http://cldr.unicode.org/index/charts/29

<http://unicode.org/cldr/charts/29/> => http://cldr.unicode.org/index/charts/29

## Compatibility

**http://unicode.org/repos/cldr-tmp/trunk/charts/.\* =>
http://unicode.org/cldr/charts/.\***

Examples:

<http://unicode.org/repos/cldr-tmp/trunk/charts/keyboards/layouts/fr.html>

=>

<http://unicode.org/cldr/charts/keyboards/layouts/fr.html> (which then redirects
further)

## Validity

Change the version number below, then check the sampling below. Use
command-click to open a bunch of windows at once.

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/index.html
>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/by_type/index.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/transforms/index.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/transforms/Latin-Arabic.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/keyboards/chars2keyboards.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/keyboards/keyboards2chars.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/keyboards/layouts/index.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/keyboards/layouts/af.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/index.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/language_plural_rules.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/likely_subtags.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/territory_language_information.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/language_territory_information.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/languages_and_scripts.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/scripts_and_languages.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/scripts_languages_and_territories.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/day_periods.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/territory_information.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/detailed_territory_currency_information.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/territory_containment_un_m_49.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/zone_tzid.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/character_fallback_substitutions.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/supplemental/aliases.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/delta/index.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/delta/bcp47.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/delta/af.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/by_type/core_data.alphabetic_information.html>

<http://validator.w3.org/check?uri=http://www.unicode.org/repos/cldr-aux/charts/30/summary/root.html>
