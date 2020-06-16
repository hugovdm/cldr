# Updating UN Codes

1.  UM M19
    1.  Open <https://unstats.un.org/unsd/methodology/m49/overview/#>
    2.  Hit the Copy button, to copy all the data to the clipboard
    3.  Open
        ...workspace/cldr/tools/java/org/unicode/cldr/util/data/external/UnCodes.txt
    4.  Hit paste. you should see tab-separated fields
    5.  Save
2.  EU
    1.  Go to <https://europa.eu/european-union/about-eu/countries_en>
    2.  Find the section "The XX member countries of the EU:
    3.  Copy and past into
        ...workspace/cldr/tools/java/org/unicode/cldr/util/data/external/EuCodes.txt
    4.  Compare with last revision; if there are differences, update
        containment.
3.  Run TestUnContainment
