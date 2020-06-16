# Update Validity XML

1.  Run GenerateValidityXML.java
2.  This generates files in {generated}cldr/validity/. (If you have
    -DSHOW_FILES, you'll see this on the console.)
    1.  New files should not be generated. If there are any, something has gone
        wrong, so raise this as an issue on cldr-dev.
    2.  The units file is hand-curated. It is kept in sync with the units
        supported in root/en.xml. The attribute values test ensures that it is a
        superset.
3.  Diff for a sanity check with the files in /common/validity
4.  Subdivisions are special.
    1.  At the end you may see a "Codes added this release:".
    2.  Compare the country codes to those from the "deprecated" list.
    3.  If any are the same, you'll have to compare the deprecated codes to the
        new codes, to see if any deprecated code was changed into a new code.
    4.  If so, then add necessary lines in supplemental data (below <!-- end of
        data generated with GenerateSubdivisions -->) of the form:
        *   <subdivisionAlias type="<DEP-CODE>" replacement="<NEW-CODE>"
            reason="deprecated"/>
5.  Run the following (you must have all the archived versions loaded, back to
    cldr-28.0!)

    TestValidity -e9

6.  If they are ok, replace and checkin
