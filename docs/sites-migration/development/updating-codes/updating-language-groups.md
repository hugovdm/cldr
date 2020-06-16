# Updating Language Groups

1.  Go to ​<http://query.wikidata.org/>
2.  Paste in the following query.
3.  Submit ( ▶️ )
4.  Download as TSV
5.  Save as .../util/data/languages/childToParent.tsv

`SELECT DISTINCT ?child ?parent WHERE {`

` ?child p:P279/ps:P279 ?parent. #child is subclass of parent`

` {`

` ?parent wdt:P31 wd:Q25295. #parent is language family, OR`

` } UNION {`

` ?child wdt:P31 wd:Q25295. #child is language family, OR`

` } UNION {`

` ?parent wdt:P31 wd:Q34770. #parent is language, OR`

` } UNION {`

` ?child wdt:P31 wd:Q34770. #child is language`

` }`

`}`

1.  Paste in the following query.
2.  Submit ( ▶️ )
3.  Download as TSV
4.  Save as: entityToCode.tsv

`SELECT DISTINCT ?lang ?langCode WHERE {`

` {`

` ?lang wdt:P305 ?langCode. #langcode is IETF = BC47 code`

` }`

`}`

`ORDER BY ?lang`

1.  Paste in the following query.
2.  Submit ( ▶️ )
3.  Download as TSV
4.  Save as: entityToLabel.tsv

`SELECT DISTINCT ?lang ?langLabel WHERE {`

` SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }`

` {`

` ?lang wdt:P31 wd:Q25295. #lang is language family, OR`

` } UNION {`

` ?lang wdt:P31 wd:Q34770. #lang is language`

` }`

`}`

`ORDER BY ?lang`

1.  Run GenerateLanguageContainment
2.  This will create {workspace}/cldr/common/supplemental/languageGroup.xml
3.  Compare to make sure nothing is lost. If something moves or is deleted,
    consider adding override to GenerateLanguageContainment
    1.  Additions go in EXTRA_PARENT_CHILDREN
        1.  If you add something, you might have to remove it someplace else.
            You'll get a "duplicate parent" error in TestLanguageGroup
    2.  Removals go in REMOVE_PARENT_CHILDREN
        1.  "\*" for value means all.
4.  Run TestLanguageGroup
    1.  Fix problems if necessary.
5.  Run ChartLanguageGroup
    1.  Review
        {workspace}/cldr-aux/charts/<number>/supplemental/language_groups.html
6.  Check in
    1.  {workspace}/cldr/common/supplemental/languageGroup.xml
    2.  {workspace}/cldr-aux/charts/<number>/supplemental/language_groups.html

---

OLD

SELECT DISTINCT ?parent ?child ?parentLabel ?childLabel WHERE {

SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }

{

?parent wdt:P31 wd:Q25295.

?child wdt:P279 ?parent.

} UNION {

?child wdt:P31 wd:Q34770.

?child wdt:P279 ?parent.

}

}
