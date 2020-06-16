# Updating Subdivision Translations

1.  Make sure that that the subdivisions are updated first as per [Updating
    Subdivision Codes](updating-subdivision-codes.md)
2.  Go to ​<https://query.wikidata.org/>
3.  Paste in the following query.
4.  Update the language list in the query (bolded) from **(de|fr)** to the
    latest, eg as below.
5.  Submit (play button: ▶️
6.  Download as TSV
7.  Save as
    {workspace}cldr/tools/java/org/unicode/cldr/util/data/external/wikisubdivisionLanguages.tsv
8.  Run tool WikiSubdivisionLanguages
9.  Sanity check result, run tests.
    1.  **NOTES**
    2.  Should only add values, never change what is there beforehand.
    3.  Currently excludes items:
        1.  That fail exemplar check (broad test, allows any letters in script).
        2.  Many of these are reparable, but need manual work.
    4.  Currently renames items that collide *within country*.
        1.  Uses superscript 2, 3 for alternates. More than 3 alternates, it
            excludes since there is probably a more serious problem.
    5.  Needs a couple more locales: zh_Hant, de_CH, fil not working yet.
10. Check in

## Query

prefix wdt: <http://www.wikidata.org/prop/direct/> prefix wd:
<http://www.wikidata.org/entity/> SELECT ?item ?label ?code ?codeLabel WHERE {
?item wdt:P300 ?code . ?item rdfs:label ?label. BIND (lang(?label) AS
?codeLabel) FILTER regex(?codeLabel,"^**(de|fr)**$") } ORDER BY ?code ?codeLabel

## Language List

(af|am|ar|as|az|be|bg|bn|bs|ca|ceb|cs|cy|da|de|el|en|es|et|eu|fa|fi|fil|fr|ga|gl|gu|ha|he|hi|hr|hu|hy|id|ig|is|it|ja|jv|ka|kk|km|kn|ko|ky|lo|lt|lv|mk|ml|mn|mr|ms|my|nb|ne|nl|or|pa|pl|ps|pt|ro|ru|sd|si|sk|sl|so|sq|sr|sv|sw|ta|te|th|tk|tr|uk|ur|uz|vi|yo|yue|zh|zu)
