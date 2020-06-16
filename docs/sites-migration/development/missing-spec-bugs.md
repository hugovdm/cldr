# Missing Spec Bugs

Here are the differences in the DTDs, checked against the spec. (Just a cursory
look at the spec, so please correct.)

There are missing sections: **please review the list, and put your name in
\[...\] by the item that you should own, then file a bug to fix it, and fix
it.**

<http://www.unicode.org/repos/cldr/trunk/docs/web/tr35.html>

**ldml**

*added:*

DONE contextTransforms

DONE metadata casingData

DONE calendar: monthPatterns cyclicNameSets

DONE otherNumberingSystems: native, traditional, finance

DONE: \[Mark\] need to fix description in bcp47 that native must be decimal.

DONE \[Mark\] collation reordering

*deprecated:*

DONE inList,

DONE inText,

DONE commonlyUsed,

DONE \[Peter\] time attribute (Some examples had time=; they were only for the
deprecated (in ldml) weekendStart and weekendEnd elements. Deleted the
examples.)

**bcp47**

*added:*

*DONE \[Yoshito\]* attributes: extension, description, and since (the latter new
on 'attribute')

**supplemental**

*added:*

*NOT-DONE \[Umesh\] gender (of personList)*

DONE territory containment - deprecated attribute

DONE plural rules can be either ordinal | cardinal

DONE mapTimezones have new attributes for version info: typeVersion otherVersion

**deprecated:**

ALL DONE (with general note)

bcp47KeywordMappings,

mapKeys,

keyMap,

mapTypes,

typeMap
